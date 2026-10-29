# greenServeFE

**greenServeFE** (greenServe Fast Execution) is the VM-based execution engine for the greenServe language.

It compiles `.gsve` source into bytecode and executes that bytecode with an explicit virtual machine. The repository also provides native `.so` modules that are loaded by greenServeFE at runtime.

## Latest release versions

Release tags and uploaded ZIP assets were checked against the repository's published GitHub Releases on **29 October 2026**. These are the latest published, non-draft, non-prerelease versions found for each package.

| Package | Latest release | Asset |
|---|---|---|
| greenServeFE | `greenServeFE-v1.0.4` | `greenServeFE-linux-x86_64.zip` |
| server | `server-v1.0.3` | `server-linux-x86_64.zip` |
| construct | `construct-v1.0.1` | `construct-linux-x86_64.zip` |
| gsnum | `gsnum-v1.0.1` | `gsnum-linux-x86_64.zip` |
| gs_table | `gs_table-v1.0.0` | `gs_table-linux-x86_64.zip` |
| gs_uuid | `gs_uuid-v1.0.0` | `gs_uuid-linux-x86_64.zip` |
| gs_time | `gs_time-v1.0.0` | `gs_time-linux-x86_64.zip` |
| gs_string | `gs_string-v1.0.0` | `gs_string-linux-x86_64.zip` |
| gs_random | `gs_random-v1.0.0` | `gs_random-linux-x86_64.zip` |
| gs_path | `gs_path-v1.0.0` | `gs_path-linux-x86_64.zip` |
| gs_json | `gs_json-v1.0.0` | `gs_json-linux-x86_64.zip` |
| gs_hash | `gs_hash-v1.0.0` | `gs_hash-linux-x86_64.zip` |
| gs_env | `gs_env-v1.0.0` | `gs_env-linux-x86_64.zip` |
| gs_base64 | `gs_base64-v1.0.0` | `gs_base64-linux-x86_64.zip` |
| gs_object | `gsobject-v1.0.0` | `greenServeFE-gs-object-linux-x86_64.zip` |
| gs_neural | `gs_neural-v1.0.0` | `gs_neural-linux-x86_64.zip` |
| gs_log | `gs_log-v1.0.0` | `gs_log-linux-x86_64.zip` |
| gs_learn | `gs_learn-v1.0.0` | `gs_learn-linux-x86_64.zip` |
| gs_http | `gs_http-v1.0.0` | `gs_http-linux-x86_64.zip` |
| gs_form | `gs_form-v1.0.0` | `gs_form-linux-x86_64.zip` |
| gs_file | `gs_file-v1.0.0` | `gs_file-linux-x86_64.zip` |
| gs_db | `gs_db-v1.0.0` | `gs_db-linux-x86_64.zip` |
| gs_csv | `gs_csv-v1.0.0` | `gs_csv-linux-x86_64.zip` |
| gs_crypto | `gs_crypto-v1.0.0` | `gs_crypto-linux-x86_64.zip` |
| gs_cortex | `gs_cortex-v1.0.0` | `gs_cortex-linux-x86_64.zip` |
| gs_array | `gs_array-v1.0.0` | `gs_array-linux-x86_64.zip` |
| gs-brain | `gs-brain-v1.0.0` | `gs-brain-linux-x86_64.zip` |
| gs_compute | `gs_compute-v1.0.0` | `gs_compute-linux-x86_64.zip` |
| gs_math | `gs_math-v1.0.0` | `gs_math-linux-x86_64.zip` |
| gs_url | `gs_url-v1.0.0` | `gs_url-linux-x86_64.zip` |
| gs_validate | `gs_validate-v1.0.0` | `gs_validate-linux-x86_64.zip` |

Every release link follows this format: `https://github.com/dominexmacedon-docs/greenServeFE-/releases/tag/TAG_NAME`. See the [complete releases page](https://github.com/dominexmacedon-docs/greenServeFE-/releases) for release notes and assets.

The installation script below installs the core engine and the original base-module set. Additional modules in the table can be downloaded from their individual release pages.

## Linux installation

The following is the complete installation command for a Debian/Ubuntu Linux x86_64 system.

It downloads the greenServeFE executable and all native module release ZIP files, extracts them, installs `greenServeFE` into `/usr/local/bin`, installs every native module into `/usr/local/lib/modules`, and configures `GREENSERVE_MODULE_PATH` so the modules can be loaded from any directory.

```bash
set -e

sudo apt-get update
sudo apt-get install -y curl unzip

printf '\nRemoving existing greenServeFE installation...\n'

sudo rm -f /usr/local/bin/greenServeFE

sudo rm -f /usr/local/lib/modules/gs_table.so
sudo rm -f /usr/local/lib/modules/gsnum.so
sudo rm -f /usr/local/lib/modules/server.so
sudo rm -f /usr/local/lib/modules/gs_uuid.so
sudo rm -f /usr/local/lib/modules/gs_time.so
sudo rm -f /usr/local/lib/modules/gs_string.so
sudo rm -f /usr/local/lib/modules/gs_random.so
sudo rm -f /usr/local/lib/modules/gs_path.so
sudo rm -f /usr/local/lib/modules/gs_json.so
sudo rm -f /usr/local/lib/modules/gs_hash.so
sudo rm -f /usr/local/lib/modules/gs_env.so
sudo rm -f /usr/local/lib/modules/gs_base64.so
sudo rm -f /usr/local/lib/modules/gs_object.so

sudo rm -f /etc/profile.d/greenServeFE.sh

unset GREENSERVE_MODULE_PATH

printf 'Existing installation removed.\n'

tmp_dir="$(mktemp -d)"
trap 'rm -rf "$tmp_dir"' EXIT

cd "$tmp_dir"

printf '\nDownloading greenServeFE...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/greenServeFE-v1.0.4/greenServeFE-linux-x86_64.zip" \
  -o greenServeFE-linux-x86_64.zip

printf 'Downloading gs_table...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_table-v1.0.0/gs_table-linux-x86_64.zip" \
  -o gs_table-linux-x86_64.zip

printf 'Downloading gsnum...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gsnum-v1.0.1/gsnum-linux-x86_64.zip" \
  -o gsnum-linux-x86_64.zip

printf 'Downloading server...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/server-v1.0.3/server-linux-x86_64.zip" \
  -o server-linux-x86_64.zip

printf 'Downloading gs_uuid...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_uuid-v1.0.0/gs_uuid-linux-x86_64.zip" \
  -o gs_uuid-linux-x86_64.zip

printf 'Downloading gs_time...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_time-v1.0.0/gs_time-linux-x86_64.zip" \
  -o gs_time-linux-x86_64.zip

printf 'Downloading gs_string...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_string-v1.0.0/gs_string-linux-x86_64.zip" \
  -o gs_string-linux-x86_64.zip

printf 'Downloading gs_random...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_random-v1.0.0/gs_random-linux-x86_64.zip" \
  -o gs_random-linux-x86_64.zip

printf 'Downloading gs_path...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_path-v1.0.0/gs_path-linux-x86_64.zip" \
  -o gs_path-linux-x86_64.zip

printf 'Downloading gs_json...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_json-v1.0.0/gs_json-linux-x86_64.zip" \
  -o gs_json-linux-x86_64.zip

printf 'Downloading gs_hash...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_hash-v1.0.0/gs_hash-linux-x86_64.zip" \
  -o gs_hash-linux-x86_64.zip

printf 'Downloading gs_env...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_env-v1.0.0/gs_env-linux-x86_64.zip" \
  -o gs_env-linux-x86_64.zip

printf 'Downloading gs_base64...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gs_base64-v1.0.0/gs_base64-linux-x86_64.zip" \
  -o gs_base64-linux-x86_64.zip

printf 'Downloading gs_object...\n'

curl -fL --show-error --retry 3 \
  "https://github.com/dominexmacedon-docs/greenServeFE-/releases/download/gsobject-v1.0.0/greenServeFE-gs-object-linux-x86_64.zip" \
  -o greenServeFE-gs-object-linux-x86_64.zip

printf '\nCreating extraction directories...\n'

mkdir -p \
  greenServeFE \
  gs_table \
  gsnum \
  server \
  gs_uuid \
  gs_time \
  gs_string \
  gs_random \
  gs_path \
  gs_json \
  gs_hash \
  gs_env \
  gs_base64 \
  gs_object

printf '\nExtracting packages...\n'

unzip -q -o greenServeFE-linux-x86_64.zip -d greenServeFE
unzip -q -o gs_table-linux-x86_64.zip -d gs_table
unzip -q -o gsnum-linux-x86_64.zip -d gsnum
unzip -q -o server-linux-x86_64.zip -d server
unzip -q -o gs_uuid-linux-x86_64.zip -d gs_uuid
unzip -q -o gs_time-linux-x86_64.zip -d gs_time
unzip -q -o gs_string-linux-x86_64.zip -d gs_string
unzip -q -o gs_random-linux-x86_64.zip -d gs_random
unzip -q -o gs_path-linux-x86_64.zip -d gs_path
unzip -q -o gs_json-linux-x86_64.zip -d gs_json
unzip -q -o gs_hash-linux-x86_64.zip -d gs_hash
unzip -q -o gs_env-linux-x86_64.zip -d gs_env
unzip -q -o gs_base64-linux-x86_64.zip -d gs_base64
unzip -q -o greenServeFE-gs-object-linux-x86_64.zip -d gs_object

printf '\nVerifying downloaded packages...\n'

test -f greenServeFE/greenServeFE

test -f gs_table/gs_table.so
test -f gsnum/gsnum.so
test -f server/server.so
test -f gs_uuid/gs_uuid.so
test -f gs_time/gs_time.so
test -f gs_string/gs_string.so
test -f gs_random/gs_random.so
test -f gs_path/gs_path.so
test -f gs_json/gs_json.so
test -f gs_hash/gs_hash.so
test -f gs_env/gs_env.so
test -f gs_base64/gs_base64.so
test -f gs_object/gs_object.so

printf 'All release packages verified.\n'

printf '\nInstalling greenServeFE...\n'

sudo install -d -m 755 /usr/local/bin

sudo install -m 755 \
  greenServeFE/greenServeFE \
  /usr/local/bin/greenServeFE

printf 'Installing native modules...\n'

sudo install -d -m 755 /usr/local/lib/modules

sudo install -m 755 \
  gs_table/gs_table.so \
  /usr/local/lib/modules/gs_table.so

sudo install -m 755 \
  gsnum/gsnum.so \
  /usr/local/lib/modules/gsnum.so

sudo install -m 755 \
  server/server.so \
  /usr/local/lib/modules/server.so

sudo install -m 755 \
  gs_uuid/gs_uuid.so \
  /usr/local/lib/modules/gs_uuid.so

sudo install -m 755 \
  gs_time/gs_time.so \
  /usr/local/lib/modules/gs_time.so

sudo install -m 755 \
  gs_string/gs_string.so \
  /usr/local/lib/modules/gs_string.so

sudo install -m 755 \
  gs_random/gs_random.so \
  /usr/local/lib/modules/gs_random.so

sudo install -m 755 \
  gs_path/gs_path.so \
  /usr/local/lib/modules/gs_path.so

sudo install -m 755 \
  gs_json/gs_json.so \
  /usr/local/lib/modules/gs_json.so

sudo install -m 755 \
  gs_hash/gs_hash.so \
  /usr/local/lib/modules/gs_hash.so

sudo install -m 755 \
  gs_env/gs_env.so \
  /usr/local/lib/modules/gs_env.so

sudo install -m 755 \
  gs_base64/gs_base64.so \
  /usr/local/lib/modules/gs_base64.so

sudo install -m 755 \
  gs_object/gs_object.so \
  /usr/local/lib/modules/gs_object.so

printf '\nConfiguring module path...\n'

echo 'export GREENSERVE_MODULE_PATH=/usr/local/lib/modules' |
  sudo tee /etc/profile.d/greenServeFE.sh >/dev/null

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
  /usr/local/lib/modules/server.so \
  /usr/local/lib/modules/gs_uuid.so \
  /usr/local/lib/modules/gs_time.so \
  /usr/local/lib/modules/gs_string.so \
  /usr/local/lib/modules/gs_random.so \
  /usr/local/lib/modules/gs_path.so \
  /usr/local/lib/modules/gs_json.so \
  /usr/local/lib/modules/gs_hash.so \
  /usr/local/lib/modules/gs_env.so \
  /usr/local/lib/modules/gs_base64.so \
  /usr/local/lib/modules/gs_object.so

printf '\nInstallation verification:\n'

test -x /usr/local/bin/greenServeFE

test -f /usr/local/lib/modules/gs_table.so
test -f /usr/local/lib/modules/gsnum.so
test -f /usr/local/lib/modules/server.so
test -f /usr/local/lib/modules/gs_uuid.so
test -f /usr/local/lib/modules/gs_time.so
test -f /usr/local/lib/modules/gs_string.so
test -f /usr/local/lib/modules/gs_random.so
test -f /usr/local/lib/modules/gs_path.so
test -f /usr/local/lib/modules/gs_json.so
test -f /usr/local/lib/modules/gs_hash.so
test -f /usr/local/lib/modules/gs_env.so
test -f /usr/local/lib/modules/gs_base64.so
test -f /usr/local/lib/modules/gs_object.so

test -f /etc/profile.d/greenServeFE.sh

printf 'greenServeFE executable: OK\n'
printf 'gs_table module: OK\n'
printf 'gsnum module: OK\n'
printf 'server module: OK\n'
printf 'gs_uuid module: OK\n'
printf 'gs_time module: OK\n'
printf 'gs_string module: OK\n'
printf 'gs_random module: OK\n'
printf 'gs_path module: OK\n'
printf 'gs_json module: OK\n'
printf 'gs_hash module: OK\n'
printf 'gs_env module: OK\n'
printf 'gs_base64 module: OK\n'
printf 'gs_object module: OK\n'
printf 'Module configuration: OK\n'

printf '\nAll greenServeFE packages installed successfully.\n'
