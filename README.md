# Pre-Built toolchain for RISCV
Up-to-date prebuilt RISC-V GNU toolchains for painless setup. No more building from source every time. The purpose of this effort is to save time and computer resources for users and a contribution to eco-friendly computing practices.

This repository uses GitHub Actions to build [riscv-gnu-toolchain](https://github.com/riscv-collab/riscv-gnu-toolchain) from source and publishes the results as [GitHub Releases](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases). Just download a prebuilt toolchain, add it to your `PATH` and use it.

### Supported Environment
Prebuilt binaries are for x86_64 Linux hosts. Every configuration is built on two
operating systems; pick the one that matches your host's glibc:

| Build OS | Asset suffix | Container image | glibc | Runs on |
| :--- | :--- | :--- | :--- | :--- |
| Rocky Linux 9.9 | `-rocky9` | `rockylinux/rockylinux:9.9` | 2.34 | glibc 2.34 or newer: Rocky/RHEL/AlmaLinux 9+, Ubuntu 22.04+, Debian 12+ |
| Ubuntu 24.04 LTS | `-ubuntu24` | `ubuntu:24.04` | 2.39 | glibc 2.39 or newer: Ubuntu 24.04+, Debian 13+ |

If unsure, use the `rocky9` build: it runs on the widest range of distributions.
Check your host's glibc with `ldd --version`.

### Downloads

Builds are published as [GitHub Releases](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases): no sign-in required, no expiry.

| Release page | What it contains | Updated |
| :--- | :--- | :--- |
| [**Latest stable**](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest) | Latest upstream riscv-gnu-toolchain release. One release per upstream version, tagged with it (e.g. `2026.10.29`); older versions stay on the [releases page](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases) | Monthly; rebuilt in place when there is no new upstream release |
| [**Rolling**](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/tag/rolling) (prerelease) | Tip of upstream `master` | Every ~10 days; assets replaced in place |
| [**CVA6**](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/tag/cva6-81245a4-gcc-13.1.0) | GCC 13.1.0 with `-mtune=cva6`, from pinned sources | Monthly, same sources |

Direct downloads (always the newest build of each):

| Configuration | Tools | Rocky 9 · stable | Ubuntu 24.04 · stable | Rocky 9 · rolling | Ubuntu 24.04 · rolling |
| :--- | :--- | :---: | :---: | :---: | :---: |
| [RV64 Newlib](https://github.com/riscv-collab/riscv-gnu-toolchain) | `riscv64-unknown-elf-*` | [`rv64-newlib-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv64-newlib-rocky9.tar.gz) | [`rv64-newlib-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv64-newlib-ubuntu24.tar.gz) | [`rv64-newlib-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/rolling/rv64-newlib-rocky9.tar.gz) | [`rv64-newlib-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/rolling/rv64-newlib-ubuntu24.tar.gz) |
| [RV64 Multilib · bare-metal](https://github.com/riscv-collab/riscv-gnu-toolchain) | `riscv64-unknown-elf-*` | [`rv64-multilib-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv64-multilib-rocky9.tar.gz) | [`rv64-multilib-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv64-multilib-ubuntu24.tar.gz) | [`rv64-multilib-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/rolling/rv64-multilib-rocky9.tar.gz) | [`rv64-multilib-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/rolling/rv64-multilib-ubuntu24.tar.gz) |
| [SCR1 Newlib](https://github.com/syntacore/scr1) | `riscv32-unknown-elf-*` | [`rv32-scr1-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv32-scr1-rocky9.tar.gz) | [`rv32-scr1-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv32-scr1-ubuntu24.tar.gz) | [`rv32-scr1-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/rolling/rv32-scr1-rocky9.tar.gz) | [`rv32-scr1-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/rolling/rv32-scr1-ubuntu24.tar.gz) |
| [Ibex Newlib](https://github.com/lowRISC/ibex) | `riscv32-unknown-elf-*`, plus `riscv64-unknown-elf-*` aliases | [`rv32-ibex-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv32-ibex-rocky9.tar.gz) | [`rv32-ibex-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv32-ibex-ubuntu24.tar.gz) | [`rv32-ibex-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/rolling/rv32-ibex-rocky9.tar.gz) | [`rv32-ibex-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/rolling/rv32-ibex-ubuntu24.tar.gz) |
| [CVA6 · tuned](https://github.com/openhwfoundation/cva6) | `riscv-none-elf-*` | [`rv64-cva6-rocky9.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/cva6-81245a4-gcc-13.1.0/rv64-cva6-rocky9.tar.gz) | [`rv64-cva6-ubuntu24.tar.gz`](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/download/cva6-81245a4-gcc-13.1.0/rv64-cva6-ubuntu24.tar.gz) | — | — |

Each `.tar.gz` comes with two companion assets, named after it:

| Asset | Contents |
| :--- | :--- |
| `<config>-<os>.tar.gz` | The toolchain; unpacks to `bin/`, `lib/`, `libexec/`, … |
| `<config>-<os>.tar.gz.sha256` | SHA-256 checksum, for `sha256sum -c` |
| `<config>-<os>-build-info.txt` | Build OS and glibc, upstream commits, configure flags, compiler version |

If you require a custom configuration, consider building it yourself (see [Need Something Else?](#need-something-else)) or open an Issue with the `Enhancement` label.

### Installation
1- Download a toolchain and its checksum from [Releases](https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases), and verify it. For example, the RV64 Newlib toolchain built on Rocky 9:
```
$ curl -LO https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv64-newlib-rocky9.tar.gz
$ curl -LO https://github.com/aamir-sultan/riscv-gnu-prebuilt/releases/latest/download/rv64-newlib-rocky9.tar.gz.sha256
$ sha256sum -c rv64-newlib-rocky9.tar.gz.sha256
```
2- Create an installation directory. Preferred `/home/usr/riscv`, to avoid the possibility of the toolchain affecting any of the system files.
```
$ sudo mkdir -p /home/usr/riscv
```
3- Extract the archive into the new directory. Permissions and symlinks are preserved, so no `chmod` is needed.
```
$ sudo tar -xzf rv64-newlib-rocky9.tar.gz -C /home/usr/riscv/
```
4- Add the toolchain to your `PATH` and apply the change
```
$ echo 'export PATH=/home/usr/riscv/bin:$PATH' >> ~/.bashrc
$ source ~/.bashrc
```

### Verify installation
Run the compiler for your configuration (`riscv64-unknown-elf-gcc` for `rv64-*`,
`riscv32-unknown-elf-gcc` for `rv32-*`, `riscv-none-elf-gcc` for CVA6):
```
$ riscv64-unknown-elf-gcc -v
```
- You should get output starting with
```
Using built-in specs.
COLLECT_GCC=riscv64-unknown-elf-gcc
COLLECT_LTO_WRAPPER=/home/usr/riscv/bin/../libexec/gcc/riscv64-unknown-elf/<gcc-version>/lto-wrapper
Target: riscv64-unknown-elf
```
`build-info.txt` in the installation directory records exactly what was built.

If a tool reports a missing shared library, install the runtime libraries:
- Rocky/RHEL/AlmaLinux: `sudo dnf install -y libmpc mpfr gmp expat ncurses-libs zlib`
- Ubuntu/Debian: `sudo apt-get install -y libmpc3 libmpfr6 libgmp10 libexpat1 libncursesw6 zlib1g`

It is highly recommended to install the dependencies mentioned in the `riscv-gnu-toolchain` README. It will help avoid getting stuck at several stages if you move forward to building sibling tools.

Rocky/RHEL/AlmaLinux 9:
```
$ sudo dnf install -y dnf-plugins-core epel-release
$ sudo dnf config-manager --set-enabled crb
$ sudo dnf install -y autoconf automake curl python3 python3-pip libmpc-devel mpfr-devel gmp-devel gawk gcc gcc-c++ make bison flex texinfo gperf libtool patchutils bc zlib-devel expat-devel ninja-build git cmake glib2-devel
```
Ubuntu/Debian:
```
$ sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat1-dev ninja-build git cmake libglib2.0-dev
```

Congratulations! You have successfully installed the riscv-gnu-toolchain without wasting your system resources.

## CI/CD

### Workflows

Every workflow is named `<config>-<os>-<channel>.yaml`. Badges show the latest run
on `main`; click one to open that workflow's runs.

| Configuration | Rocky 9 · stable | Rocky 9 · rolling | Ubuntu 24.04 · stable | Ubuntu 24.04 · rolling |
| :--- | :---: | :---: | :---: | :---: |
| [RV64 Newlib](https://github.com/riscv-collab/riscv-gnu-toolchain)<br><sub>`rv64gc_zicsr_zifencei` / `lp64d`</sub> | [![rv64-newlib-rocky9-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-newlib-rocky9-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-newlib-rocky9-stable.yaml) | [![rv64-newlib-rocky9-rolling](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-newlib-rocky9-rolling.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-newlib-rocky9-rolling.yaml) | [![rv64-newlib-ubuntu24-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-newlib-ubuntu24-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-newlib-ubuntu24-stable.yaml) | [![rv64-newlib-ubuntu24-rolling](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-newlib-ubuntu24-rolling.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-newlib-ubuntu24-rolling.yaml) |
| [RV64 Multilib · bare-metal](https://github.com/riscv-collab/riscv-gnu-toolchain)<br><sub>RV32 + RV64, multiple ABIs</sub> | [![rv64-multilib-rocky9-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-multilib-rocky9-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-multilib-rocky9-stable.yaml) | [![rv64-multilib-rocky9-rolling](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-multilib-rocky9-rolling.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-multilib-rocky9-rolling.yaml) | [![rv64-multilib-ubuntu24-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-multilib-ubuntu24-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-multilib-ubuntu24-stable.yaml) | [![rv64-multilib-ubuntu24-rolling](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-multilib-ubuntu24-rolling.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-multilib-ubuntu24-rolling.yaml) |
| [SCR1 Newlib](https://github.com/syntacore/scr1)<br><sub>`rv32imc_zicsr_zifencei` / `ilp32`</sub> | [![rv32-scr1-rocky9-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv32-scr1-rocky9-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv32-scr1-rocky9-stable.yaml) | [![rv32-scr1-rocky9-rolling](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv32-scr1-rocky9-rolling.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv32-scr1-rocky9-rolling.yaml) | [![rv32-scr1-ubuntu24-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv32-scr1-ubuntu24-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv32-scr1-ubuntu24-stable.yaml) | [![rv32-scr1-ubuntu24-rolling](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv32-scr1-ubuntu24-rolling.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv32-scr1-ubuntu24-rolling.yaml) |
| [Ibex Newlib](https://github.com/lowRISC/ibex)<br><sub>`rv32imc_zicsr_zifencei` / `ilp32`</sub> | [![rv32-ibex-rocky9-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv32-ibex-rocky9-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv32-ibex-rocky9-stable.yaml) | [![rv32-ibex-rocky9-rolling](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv32-ibex-rocky9-rolling.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv32-ibex-rocky9-rolling.yaml) | [![rv32-ibex-ubuntu24-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv32-ibex-ubuntu24-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv32-ibex-ubuntu24-stable.yaml) | [![rv32-ibex-ubuntu24-rolling](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv32-ibex-ubuntu24-rolling.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv32-ibex-ubuntu24-rolling.yaml) |
| [CVA6 · tuned](https://github.com/openhwfoundation/cva6)<br><sub>GCC 13.1.0, `-mtune=cva6`</sub> | [![rv64-cva6-rocky9-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-cva6-rocky9-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-cva6-rocky9-stable.yaml) | — | [![rv64-cva6-ubuntu24-stable](https://img.shields.io/github/actions/workflow/status/aamir-sultan/riscv-gnu-prebuilt/rv64-cva6-ubuntu24-stable.yaml?branch=main&style=for-the-badge&label=build)](https://github.com/aamir-sultan/riscv-gnu-prebuilt/actions/workflows/rv64-cva6-ubuntu24-stable.yaml) | — |

A passing badge means the last build succeeded; the archive is on the matching
release page.

### Channels

| Channel | Builds | Schedule | Release | Artifact retention |
| :--- | :--- | :--- | :--- | :--- |
| **stable** | The riscv-gnu-toolchain release recorded by the submodule | Monthly, started by [bump-riscv-gnu-toolchain.yaml](.github/workflows/bump-riscv-gnu-toolchain.yaml) (03:00 UTC on the 1st) | `<version>`, e.g. `2026.10.29` (marked latest) | 40 days |
| **rolling** | Tip of upstream `master` | 06:00 UTC on the 5th, 15th and 25th | `rolling` (prerelease) | 20 days |
| **CVA6** | Pinned CVA6 builder, GCC 13.1.0 + `-mtune=cva6` | 03:00 UTC on the 1st | `cva6-81245a4-gcc-13.1.0` | 40 days |

**How stable updates work.** The `riscv-gnu-toolchain` submodule records the release
the stable channel builds. Every month `bump-riscv-gnu-toolchain.yaml` looks up the
latest upstream release. If it is newer than the submodule, it commits
`Bump riscv-gnu-toolchain to <tag>` on `main`. Either way, it then starts all eight
`*-stable.yaml` workflows, which build the submodule's commit. A stable workflow
started by hand rebuilds the release the submodule currently records. The rolling
channel never changes the submodule. Use stable builds unless you need unreleased
upstream fixes.

**Releases** are only published from runs on `main`. Each build uploads its own
`<config>-<os>` assets, so builds publish to a shared release independently. Every
run also keeps its archive as a workflow artifact named
`<config>-<os>-<channel>-<version>-<run>`; open the run and look under **Artifacts**
(GitHub sign-in required).

**CVA6** pins live in [_build-cva6-rocky9.yaml](.github/workflows/_build-cva6-rocky9.yaml)
and [_build-cva6-ubuntu24.yaml](.github/workflows/_build-cva6-ubuntu24.yaml). To upgrade,
update `CVA6_REF`, `TOOLCHAIN_CONFIG`, `GCC_VERSION`, and the three component commit
IDs together, in both files; the release tag changes with `CVA6_REF` and `GCC_VERSION`, so update the
CVA6 links in this README too. The fetch step checks that the upstream release tags
resolve to those component commits before applying the patch. The CVA6 archive also
records the tuning patch checksum.

### Shared workflows

Each OS has its own build file, so a Rocky or Ubuntu change touches only that OS.

| File | Purpose |
| :--- | :--- |
| [_build-riscv-gnu-rocky9.yaml](.github/workflows/_build-riscv-gnu-rocky9.yaml) | Builds one riscv-gnu-toolchain configuration in the Rocky Linux 9.9 container, then publishes it |
| [_build-riscv-gnu-ubuntu24.yaml](.github/workflows/_build-riscv-gnu-ubuntu24.yaml) | Same, in the Ubuntu 24.04 container |
| [_build-cva6-rocky9.yaml](.github/workflows/_build-cva6-rocky9.yaml) | Builds the CVA6 toolchain in the Rocky Linux 9.9 container, then publishes it |
| [_build-cva6-ubuntu24.yaml](.github/workflows/_build-cva6-ubuntu24.yaml) | Same, in the Ubuntu 24.04 container |
| [_release.yaml](.github/workflows/_release.yaml) | Creates the release if needed and uploads the `.tar.gz`, `.sha256` and build-info assets |
| [bump-riscv-gnu-toolchain.yaml](.github/workflows/bump-riscv-gnu-toolchain.yaml) | Monthly submodule bump; starts the stable builds |

### Build conventions

| Property | Value |
| :--- | :--- |
| Runner | `ubuntu-24.04` (GitHub-hosted) |
| Build environment | `rockylinux/rockylinux:9.9` or `ubuntu:24.04` container, running as root |
| Disk cleanup | Host `/usr` and `/opt` mounted at `/host/usr` and `/host/opt`; unused preinstalled SDKs are removed before the build |
| Dependencies | Rocky: `dnf` with `crb` and `epel-release` enabled. Ubuntu: `apt-get --no-install-recommends` |
| Sources | Exact upstream commit, shallow clone. Only the `binutils`, `gcc`, `gdb` and `newlib` submodules are fetched, from GitHub mirrors with retries, avoiding rate limits (HTTP 429) and timeouts from `gcc.gnu.org`, `sourceware.org` and `savannah.gnu.org` |
| Build | `make -j"$(nproc)"`, installed under `$HOME/riscv` |
| Timeout | 350 minutes per build |
| Checks | Smoke test compiles and links a test program; multilib checks cover both RV32 and RV64 |
| Output | `.tar.gz` with `build-info.txt`, published to a release and kept as a workflow artifact |

Smoke tests cross-link executables without running them on the x86_64 host.

To start a build manually, open **Actions**, select the workflow, click
**Run workflow**, choose the branch and confirm. With the GitHub CLI:
```
$ gh workflow run rv64-multilib-rocky9-stable.yaml --ref main
$ gh workflow run rv64-multilib-ubuntu24-rolling.yaml --ref main
$ gh workflow run bump-riscv-gnu-toolchain.yaml --ref main   # bump + all eight stable builds
```

## Need Something Else?
If you are looking for a customized flavour of riscv-toolchain and want to use this framework, follow the instructions below:

1- Fork this repository and clone it on your local machine, or edit on GitHub.com
```
git clone https://github.com/aamir-sultan/riscv-gnu-prebuilt.git
cd riscv-gnu-prebuilt/.github/workflows
```
2- Copy an existing workflow, e.g. `rv64-newlib-rocky9-stable.yaml`, to `rv32-mycore-rocky9-stable.yaml` (and the other OS/channel combinations you want), then change its inputs. The build steps live in `_build-riscv-gnu-rocky9.yaml` (or `_build-riscv-gnu-ubuntu24.yaml` for the `-ubuntu24` copy); you do not need to copy them. To have the monthly bump start your stable workflows, add them to `STABLE_WORKFLOWS` in `bump-riscv-gnu-toolchain.yaml`.
```
    with:
      name: rv32-mycore
      channel: stable           # or rolling
      configure_flags: --with-arch=rv32gc --with-abi=ilp32d
      triple: riscv32-unknown-elf
      smoke_march: rv32gc_zicsr_zifencei
      smoke_mabi: ilp32d
```
3- Commit (and push, if working locally)

4- Go to GitHub.com/your_forked_repo > Actions > select your workflow > `Run workflow`

It will take a while. If all goes well, the archive appears on the run's **Artifacts** and on the matching release; otherwise, find the errors in the build logs. Releases need **Settings > Actions > General > Workflow permissions** set to **Read and write**.

## Contributions
Contributions from developers like you make open source a vibrant and innovative space. To contribute to `riscv-gnu-prebuilt`, please follow the guidelines outlined in the [CONTRIBUTING.md](CONTRIBUTING.md) file. Your efforts are highly valued, and together, we can continue to enhance and improve the project for the entire community.
