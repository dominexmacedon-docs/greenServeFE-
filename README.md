# greenServeFE

**greenServeFE** (greenServe Fast Execution) is the VM-based execution engine for the greenServe language.

It compiles `.gsve` source into bytecode and executes that bytecode with an explicit virtual machine. The repository also provides native `.so` modules that are loaded by greenServeFE at runtime.

## Release packages

The Linux x86_64 release consists of four packages:

- `greenServeFE-v1.0.0` — the greenServeFE executable
- `gs_table-v1.0.0` — the `gs_table.so` native module
- `gsnum-v1.0.0` — the `gsnum.so` native module
- `server-v1.0.0` — the `server.so` native module

## Linux installation

The following is the complete installation command for a Debian/Ubuntu Linux x86_64 system. It downloads all four release ZIP files, extracts them, installs `greenServeFE` into `/usr/local/bin`, installs the native modules into the normal system `modules` directory at `/usr/local/lib/modules`, and configures `GREENSERVE_MODULE_PATH` so the modules can be imported from any directory.

```bash
set -e

sudo apt-get update
sudo apt-get install -y curl unzip

tmp_dir="$(mktemp -d)"
trap 'rm -rf "$tmp_dir"' EXIT

cd "$tmp_dir"

curl -fL --show-error --retry 3 "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/greenServeFE-v1.0.0/greenServeFE-linux-x86_64.zip" -o greenServeFE-linux-x86_64.zip
curl -fL --show-error --retry 3 "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_table-v1.0.0/gs_table-linux-x86_64.zip" -o gs_table-linux-x86_64.zip
curl -fL --show-error --retry 3 "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gsnum-v1.0.0/gsnum-linux-x86_64.zip" -o gsnum-linux-x86_64.zip
curl -fL --show-error --retry 3 "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/server-v1.0.0/server-linux-x86_64.zip" -o server-linux-x86_64.zip

mkdir -p greenServeFE gs_table gsnum server

unzip -q -o greenServeFE-linux-x86_64.zip -d greenServeFE
unzip -q -o gs_table-linux-x86_64.zip -d gs_table
unzip -q -o gsnum-linux-x86_64.zip -d gsnum
unzip -q -o server-linux-x86_64.zip -d server

test -f greenServeFE/greenServeFE
test -f gs_table/gs_table.so
test -f gsnum/gsnum.so
test -f server/server.so

sudo install -d -m 755 /usr/local/bin
sudo install -m 755 greenServeFE/greenServeFE /usr/local/bin/greenServeFE

sudo install -d -m 755 /usr/local/lib/modules
sudo install -m 755 gs_table/gs_table.so /usr/local/lib/modules/gs_table.so
sudo install -m 755 gsnum/gsnum.so /usr/local/lib/modules/gsnum.so
sudo install -m 755 server/server.so /usr/local/lib/modules/server.so

echo 'export GREENSERVE_MODULE_PATH=/usr/local/lib/modules' | sudo tee /etc/profile.d/greenServeFE.sh >/dev/null
sudo chmod 644 /etc/profile.d/greenServeFE.sh

export GREENSERVE_MODULE_PATH=/usr/local/lib/modules

printf '\nInstallation completed.\n\n'

printf 'greenServeFE: '
/usr/local/bin/greenServeFE --version

printf '\nExecutable: %s\n' "$(command -v greenServeFE)"
printf 'Module path: %s\n' "$GREENSERVE_MODULE_PATH"

printf '\nInstalled modules:\n'
ls -lh \
    /usr/local/lib/modules/gs_table.so \
    /usr/local/lib/modules/gsnum.so \
    /usr/local/lib/modules/server.so
