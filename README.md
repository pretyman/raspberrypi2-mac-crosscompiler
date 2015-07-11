# RaspberryPi 2 Cross Compile for Mac OS

## Important: a case-sensitive file system is needed.

1. Create an image with the name `RaspberryPiCrossCompiler` with `Disk Utility`:
![Create Disk Image](https://raw.githubusercontent.com/wiki/pretyman/raspberrypi2-mac-crosscompiler/CreateDiskImage.png)
 1. Click on *New Image*
 2. *Save As*: `RaspberryPiCrossCompiler` 
 3. Set the following attributes, you *should* set the same name:
    * Name: `RaspberryPiCrossCompiler`
    * Size: 500MB
    * Format: Mac OS Extended (*Canse-sensitive*, Journaled)
2. Go to */Volumes/RaspberryPiCrossCompiler* and run the following magic command line:
```bash
git clone https://github.com/pretyman/raspberrypi2-mac-crosscompiler tmp 
mv tmp/.git . 
rm -rf tmp 
git reset --hard
```
