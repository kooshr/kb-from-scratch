# kb-from-scratch

Custom Hall Effect keyboard development, starting with a minimal Raspberry Pi Pico 2 / RP2350 firmware build.

## Milestone A: first firmware build

The initial program blinks the Pico 2's onboard LED. It does not use the Hall sensor or USB yet.

### Build on Windows PowerShell

This repository expects a local Pico SDK checkout at `pico-sdk/` and the Arm GNU bare-metal compiler on `PATH`. CMake and Ninja are stored under `.tooling/python/` for this setup.

```powershell
$env:Path = (Resolve-Path '.tooling\python\cmake\data\bin').Path + ';' + (Resolve-Path '.tooling\python\bin').Path + ';' + (Resolve-Path '.tooling\arm\bin').Path + ';' + $env:Path
$env:PICO_SDK_PATH = (Resolve-Path 'pico-sdk').Path
cmake -S . -B build -G Ninja -DPICO_BOARD=pico2 -DPICO_NO_PICOTOOL=1
cmake --build build
```

The expected firmware artifact is `build/kb_from_scratch.elf`. This first build skips Picotool because the environment cannot run Git's MSYS submodule fetch; adding Picotool will produce the flashable UF2 in the next setup step. The LED program is ready to flash after that conversion step.

The SDK and toolchain are ignored by Git so each developer can install them locally without checking megabytes of third-party files into the project. They are not yet provisioned by a reproducible setup script.
