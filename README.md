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

## Installation

greenServeFE is installed and managed through the **MacoraOne `one` CLI**. This avoids maintaining a long manual download, extraction, module-copying, and environment-configuration script in this repository.

### 1. Install MacoraOne

If the `one` command is not installed, follow the [MacoraOne CLI installation guide](https://macoraone.dominextechdocumentary.workers.dev/macoraone.html) or visit the [MacoraOne repository](https://github.com/MacoraOne/MacoraOne).

### 2. Install greenServeFE

On a supported Linux x86-64 system, run:

```bash
one install greenServeFE
```

MacoraOne handles the greenServeFE package installation through its release-based installer. You do not need to manually download the engine ZIP, extract native modules, copy shared objects, or configure the module directory.

### 3. Verify the installation

```bash
greenServeFE --version
```

Use the installed engine to execute a GSVE program:

```bash
greenServeFE test.gsve
```

For MacoraOne CLI commands and updates, see the [MacoraOne project](https://github.com/MacoraOne/MacoraOne).

## Language, VM, and native modules

The language implementation, lexer, parser, bytecode compiler, virtual machine, native-module ABI, module APIs, examples, and build workflows are maintained in the [greenServeFE-build repository](https://github.com/dominexmacedon-docs/greenServeFE-build).

For the complete implementation and technical documentation, refer to that repository. This repository provides the published runtime releases and installation entry point.

## Related project

- [MacoraOne](https://github.com/MacoraOne/MacoraOne) — the CLI and unified developer-tool ecosystem used to install greenServeFE.
- [greenServeFE-build](https://github.com/dominexmacedon-docs/greenServeFE-build) — language implementation, compiler, VM, native modules, and build workflows.
