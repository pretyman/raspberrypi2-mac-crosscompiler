# RaspberryPi 2 Cross Compile for Mac OS

## Important: a case-sensitive file system is needed.

1. This toolchain requires GLIBCXX_3.4.20 which is only available in the jessie distribution. You can upgrade from wheezy to jessie following the instructions in this URL: http://raspberrypi.stackexchange.com/questions/27858/upgrade-to-raspbian-jessie
2. Create an image with the name `RaspberryPiCrossCompiler` with `Disk Utility`:
![Create Disk Image](https://raw.githubusercontent.com/wiki/pretyman/raspberrypi2-mac-crosscompiler/CreateDiskImage.png)
 1. Click on *New Image*
 2. *Save As*: `RaspberryPiCrossCompiler` 
 3. Set the following attributes, you *should* set the same name:
    * Name: `RaspberryPiCrossCompiler`
    * Size: 500MB
    * Format: Mac OS Extended (*Canse-sensitive*, Journaled)
3. Go to */Volumes/RaspberryPiCrossCompiler* and run the following magic command line:
```bash
git clone https://github.com/pretyman/raspberrypi2-mac-crosscompiler tmp 
mv tmp/.git . 
rm -rf tmp 
git reset --hard
```
## Using the cross compiler
This cross compiler is supported by the [polly](https://github.com/ruslo/polly) toolchain collection and [hunter](https://github.com/ruslo/hunter) package manager. To use it, the following environment variables must be setup:
```
export RASPBERRYPI_CROSS_COMPILE_TOOLCHAIN_PATH=/Volumes/RaspberryPiCrossCompiler/x-tools/arm-unknown-linux-gnueabihf/bin/
export RASPBERRYPI_CROSS_COMPILE_TOOLCHAIN_PREFIX=arm-unknown-linux-gnueabihf
export RASPBERRYPI_CROSS_COMPILE_SYSROOT=/Volumes/RaspberryPiCrossCompiler/x-tools/arm-unknown-linux-gnueabihf/arm-unknown-linux-gnueabihf/sysroot
```

Then `build.py --toolchain raspberrypi2-cxx11` of [polly](https://github.com/ruslo/polly) can be used to build your CMake based project.
