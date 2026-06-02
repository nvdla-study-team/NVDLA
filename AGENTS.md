# IC Project Agent Guide

本文件适用于 `/home/yian/prj/NVDLA`。该目录是 IC workspace 中的一个独立 Git 工程。

## Scope

- 修改前必须在本工程根目录查看 `README*`、构建入口、文件列表和 `git status --short`。
- 默认只改本工程内部文件，不跨工程隐式修改。
- `/home/yian/prj` 是多个 IC 工程并列放置的工作区，不是单一仓库。

## EDA Tool Paths

当前环境中可直接使用的 EDA 路径如下：

| Tool | Command | Path |
| --- | --- | --- |
| VCS | `vcs` | `/home/yian/Synopsys/vcs/V-2023.12-SP2/bin/vcs` |
| DVE | `dve` | `/home/yian/Synopsys/vcs/V-2023.12-SP2/bin/dve` |
| Verdi | `verdi` | `/home/yian/Synopsys/verdi/V-2023.12-SP2/bin/verdi` |
| Design Compiler | `dc_shell` | `/home/yian/Synopsys/syn/V-2023.12-SP3/bin/dc_shell` |
| Design Vision | `design_vision` | `/home/yian/Synopsys/syn/V-2023.12-SP3/bin/design_vision` |
| DC NXT | `dcnxt_shell` | `/home/yian/Synopsys/syn/V-2023.12-SP3/bin/dcnxt_shell` |
| RTL Architect | `rtl_shell` | `/home/yian/Synopsys/rtla/V-2023.12/bin/rtl_shell` |
| RTL Architect LM | `lm_shell` | `/home/yian/Synopsys/rtla/V-2023.12/bin/lm_shell` |
| SpyGlass | `spyglass` | `/home/yian/Synopsys/spyglass/V-2023.12-SP1/SPYGLASS_HOME/bin/spyglass` |
| SpyGlass Shell | `sg_shell` | `/home/yian/Synopsys/spyglass/V-2023.12-SP1/SPYGLASS_HOME/bin/sg_shell` |
| PrimeTime | `pt_shell` | `/home/yian/Synopsys/prime/V-2023.12/bin/pt_shell` |
| PrimeTime GUI | `primetime` | `/home/yian/Synopsys/prime/V-2023.12/bin/primetime` |
| PrimePower | `primepower` | `/home/yian/Synopsys/prime/V-2023.12/bin/primepower` |
| Power Shell | `pwr_shell` | `/home/yian/Synopsys/prime/V-2023.12/bin/pwr_shell` |
| StarRC wrapper | `starrc_wrapper` | `/home/yian/Synopsys/prime/V-2023.12/bin/starrc_wrapper` |
| IC Compiler II | `icc2_shell` | `/home/yian/Synopsys/icc2/V-2023.12/bin/icc2_shell` |
| IC Compiler II LM | full path recommended | `/home/yian/Synopsys/icc2/V-2023.12/bin/lm_shell` |
| DSO.ai | `dso_shell` | `/home/yian/Synopsys/dsoai/V-2023.12/dsoai/V-2023.12/bin/dso_shell` |
| DSO.ai Shell | `ai_shell` | `/home/yian/Synopsys/dsoai/V-2023.12/dsoai/V-2023.12/bin/ai_shell` |
| SCL lmgrd | `lmgrd` | `/home/yian/Synopsys/scl/2024.06/linux64/bin/lmgrd` |
| SCL lmutil | `lmutil` | `/home/yian/Synopsys/scl/2024.06/linux64/bin/lmutil` |
| RISC-V GCC | `riscv64-unknown-elf-gcc` | `/home/yian/prj/tools/riscv64-unknown-elf-wrapper/bin/riscv64-unknown-elf-gcc` |
| RISC-V objcopy | `riscv64-unknown-elf-objcopy` | `/home/yian/prj/tools/riscv64-unknown-elf-wrapper/bin/riscv64-unknown-elf-objcopy` |
| RISC-V readelf | `riscv64-unknown-elf-readelf` | `/home/yian/prj/tools/riscv64-unknown-elf-wrapper/bin/riscv64-unknown-elf-readelf` |

环境变量：

- `LM_LICENSE_FILE=27000@localhost.localdomain`
- `DC_HOME=/home/yian/Synopsys/syn/V-2023.12-SP3`
- `VCS_HOME=/home/yian/Synopsys/vcs/V-2023.12-SP2`
- `VERDI_HOME=/home/yian/Synopsys/verdi/V-2023.12-SP2`
- `SCL_HOME=/home/yian/Synopsys/scl/2024.06`
- `PRIME_HOME=/home/yian/Synopsys/prime/V-2023.12`
- `ICC2_HOME=/home/yian/Synopsys/icc2/V-2023.12`
- `DSOAI_HOME=/home/yian/Synopsys/dsoai/V-2023.12/dsoai/V-2023.12`
- `RISCV_GNU_TOOLCHAIN=/home/yian/prj/tools/xpack-riscv-none-elf-gcc-15.2.0-1`
- Synopsys bin directories are configured in `/home/yian/.bashrc`.
- RISC-V toolchain bin and wrapper bin directories are added in `/home/yian/.bashrc`.
- Before running the first EDA command in a task, start an interactive shell and execute `lmg` manually once to initialize license access; only begin invoking EDA tools after `lmg` has completed successfully. `lmg` may be defined by interactive shell startup files, so do not assume it is available from a non-interactive `bash -c` command.

Not found in this workspace scan: Cadence, Mentor/Siemens Questa, Xilinx/Vivado, Synopsys Formality, and Fusion Compiler standalone installs.

If a tool command is missing, first check whether the current shell inherited `PATH`; do not hard-code a different personal path into project files.

Environment changes require user approval first. This includes edits to `/home/yian/.bashrc`, `PATH`, license variables, tool aliases, shell startup files, and project-wide environment setup scripts. Before changing them, explain the intended change and wait for confirmation.
