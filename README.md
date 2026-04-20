# Alif M55 LVGL Demo

## Description
[LVGL](https://github.com/lvgl/lvgl) example for Alif E7/E8 DevKit

This app is porting the LVGL [v9.2.2](https://github.com/lvgl/lvgl/releases/tag/v9.2.2) to Alif Cortex-M55 with D/AVE 2D GPU.
It launches the Demo Benchmark example to measure its performance on the M55 HP and HE cores using GPU acceleration and FreeRTOS.

Benchmark Summary for Alif E7 DevKit: LVGL v9.2.2, M55 HP core, D/AVE 2D, 60FPS display framerate

| Name                      | Avg. CPU | Avg. FPS | Avg. time | render time | flush time |
| ------------------------- |:--------:|:--------:|:---------:|:-----------:| ----------:|
| Empty screen              | 15%      | 61       | 9         | 2           | 7          |
| Moving wallpaper          | 22%      | 61       | 15        | 8           | 7          |
| Single rectangle          | 1%       | 61       | 6         | 0           | 6          |
| Multiple rectangles       | 13%      | 61       | 6         | 1           | 5          |
| Multiple RGB images       | 25%      | 61       | 6         | 3           | 3          |
| Multiple ARGB images      | 28%      | 61       | 7         | 4           | 3          |
| Rotated ARGB images       | 5%       | 10       | 95        | 85          | 10         |
| Multiple labels           | 49%      | 61       | 14        | 7           | 7          |
| Screen sized text         | 82%      | 30       | 31        | 27          | 4          |
| Multiple arcs             | 21%      | 61       | 9         | 2           | 7          |
| Containers                | 14%      | 61       | 2         | 2           | 0          |
| Containers with overlay   | 53%      | 60       | 15        | 10          | 5          |
| Containers with opa       | 15%      | 61       | 3         | 2           | 1          |
| Containers with opa_layer | 51%      | 53       | 16        | 10          | 6          |
| Containers with scrolling | 61%      | 61       | 14        | 10          | 4          |
| Widgets demo              | 76%      | 54       | 11        | 10          | 1          |
| All scenes avg.           | 33%      | 54       | 15        | 11          | 4          |

## Requirements
This application is built on [VSCode Getting Started Template](https://github.com/alifsemi/alif_vscode-template).
Please make sure you have setup your VSCode and other tools and environment based on this template and test it out by building and running the application.

The required software setup consists of VSCode, Git, CMake, cmsis-toolbox, Arm GNU toolchain and Alif tools.

This app also requires following CMSIS packs to be installed and added to the project:
  * `ARM::CMSIS@>=6.1.0` (https://github.com/ARM-software/CMSIS_6/releases)
  * `ARM::CMSIS-FreeRTOS@>=10.5.1` (https://github.com/ARM-software/CMSIS-FreeRTOS/releases)
  * `LVGL::lvgl@9.2.2` (https://github.com/lvgl/lvgl/tree/release/v9.2/env_support/cmsis-pack)
  * `AlifSemiconductor::Ensemble@>=2.1.0` (https://github.com/alifsemi/alif_ensemble-cmsis-dfp/releases)
  * `AlifSemiconductor::Dave2DDriver@2.0.2` (https://github.com/alifsemi/alif_dave2d-driver/releases)
  * `AlifSemiconductor::LVGL_DAVE2D@1.1.2` (https://github.com/alifsemi/alif_lvgl-dave2d/releases)

By default, these packs are installed VS Code `First time pack installation` script (see below).

The default hardware is [Alif Ensemble DevKit Gen 2](https://alifsemi.com/support/kits/ensemble-devkit-gen2/) with display.

## Get started
To build the app you need to clone this repository:
```
git clone --recursive https://github.com/alifsemi/alif_m55-lvgl
```

After setting up the environment according to the [VSCode Getting Started Template](https://github.com/alifsemi/alif_vscode-template) you can select **File->Open Folder** from VSCode and press **F1** and start choosing from the preset build tasks.

1. **F1** --> Tasks:Run Task --> First time pack installation
2. **F1** --> Tasks:Run Task --> cmsis-csolution.build:Build (Better to do this from the CMSIS Extension Build (hammer icon))
3. **F1** --> Tasks:Run Task --> Program with Security Toolkit

#### Dave2DDriver and LVGL_DAVE2D packs installation
If you need to install `AlifSemiconductor::Dave2DDriver@2.0.2` and `AlifSemiconductor::LVGL_DAVE2D@1.1.2` manually, follow next steps:
1. Download `AlifSemiconductor.Dave2DDriver.2.0.2.pack` from https://github.com/alifsemi/alif_dave2d-driver
2. Download `AlifSemiconductor.LVGL_DAVE2D.1.1.2.pack` from https://github.com/alifsemi/alif_lvgl-dave2d
3. Open VS Code Terminal: **Terminal** --> **New terminal**
4. Enter the directory where `AlifSemiconductor.Dave2DDriver.2.0.2.pack` and `AlifSemiconductor.LVGL_DAVE2D.1.1.2.pack` are located
5. Execute commands `cpackget add AlifSemiconductor.Dave2DDriver.2.0.2.pack; cpackget add AlifSemiconductor.LVGL_DAVE2D.1.1.2.pack`
