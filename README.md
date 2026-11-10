# greenServeFE

**greenServeFE** (greenServe Fast Execution) is the VM-based execution engine for the greenServe language.

It compiles `.gsve` source into bytecode and executes that bytecode with an explicit virtual machine. The repository also provides native `.so` modules loaded at runtime.

## Quick installation

The following commands install the MacoraOne `one` CLI on Linux and then install greenServeFE.

### 1. Install MacoraOne

~~~bash
set -eu

URL="https://github.com/MacoraOne/MacoraOne/releases/download/one-v1.0.2/macoraone-linux-x86_64.zip"
TMP_DIR="$(mktemp -d)"
trap 'rm -rf "$TMP_DIR"' EXIT

curl -fL "$URL" -o "$TMP_DIR/macoraone-linux-x86_64.zip"
unzip -q "$TMP_DIR/macoraone-linux-x86_64.zip" -d "$TMP_DIR/extracted"

# Locate the executable inside the archive.
BIN="$(find "$TMP_DIR/extracted" -type f \( -name 'macoraone' -o -name 'macoraone-linux-x86_64' -o -name 'one' \) -print -quit)"

if [ -z "$BIN" ]; then
    echo "Error: could not find the MacoraOne executable in the release archive." >&2
    echo "Archive contents:" >&2
    find "$TMP_DIR/extracted" -maxdepth 3 -type f -print >&2
    exit 1
fi

chmod +x "$BIN"
sudo install -m 0755 "$BIN" /usr/local/bin/one

echo "MacoraOne installed as the 'one' command at /usr/local/bin/one"
one --help
~~~

### 2. Install greenServeFE

~~~bash
one install greenServeFE
~~~

### 3. Install native modules

Install each module separately. MacoraOne accepts one package name per install command.

~~~bash
one install server
one install construct
one install gs_math
~~~

## Published releases

Release tags and Linux x86_64 ZIP asset names below are the package inventory currently documented for this repository. Check the [GitHub Releases page](https://github.com/dominexmacedon-docs/greenServeFE-/releases) for the authoritative release status, notes, and downloadable assets.

| Package | Release tag | Linux asset |
|---|---|---|
| greenServeFE | `greenServeFE-v1.0.6` | `greenServeFE-linux-x86_64.zip` |
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

## MacoraOne package commands

Install each package with its own command; do not combine package names.

| Package | Install command |
|---|---|
| greenServeFE | `one install greenServeFE` |
| server | `one install server` |
| construct | `one install construct` |
| gsnum | `one install gsnum` |
| gs_table | `one install gs_table` |
| gs_uuid | `one install gs_uuid` |
| gs_time | `one install gs_time` |
| gs_string | `one install gs_string` |
| gs_random | `one install gs_random` |
| gs_path | `one install gs_path` |
| gs_json | `one install gs_json` |
| gs_hash | `one install gs_hash` |
| gs_env | `one install gs_env` |
| gs_base64 | `one install gs_base64` |
| gs_object | `one install gs_object` |
| gs_neural | `one install gs_neural` |
| gs_log | `one install gs_log` |
| gs_learn | `one install gs_learn` |
| gs_http | `one install gs_http` |
| gs_form | `one install gs_form` |
| gs_file | `one install gs_file` |
| gs_db | `one install gs_db` |
| gs_csv | `one install gs_csv` |
| gs_crypto | `one install gs_crypto` |
| gs_cortex | `one install gs_cortex` |
| gs_array | `one install gs_array` |
| gs-brain | `one install gs-brain` |
| gs_compute | `one install gs_compute` |
| gs_math | `one install gs_math` |
| gs_url | `one install gs_url` |
| gs_validate | `one install gs_validate` |

## Uninstall packages

Remove packages individually:

~~~bash
one uninstall server
one uninstall construct
~~~

To remove all packages managed by MacoraOne:

~~~bash
one uninstall all
~~~

## Verify and run

~~~bash
greenServeFE --version
greenServeFE test.gsve
~~~

For more information, see the [MacoraOne installation guide](https://macoraone.dominextechdocumentary.workers.dev/macoraone.html) and [MacoraOne repository](https://github.com/MacoraOne/MacoraOne).

## Language and runtime

greenServeFE is a VM-based execution engine for the greenServe language. It compiles `.gsve` source files into bytecode and executes that bytecode using its virtual machine. Native modules extend the runtime with additional functionality.

Refer to each package's release notes for module-specific changes and compatibility information.

## Related project

- [MacoraOne](https://github.com/MacoraOne/MacoraOne) — the CLI used to install, manage, and remove greenServeFE and its native modules.