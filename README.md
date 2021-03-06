# sniper7.2 with pin3.11
This repository describes how to install sniper simulator version 7.2 with pin 3.11 without errors.

# Get sniper.tgz file and untar it.
- wget http://snipersim.org/download/1e63833bb3daeb64/packages/sniper-latest.tgz
- tar -zxvf sniper-latest.tgz

# Download pin3.11 and untar it.
- wget https://software.intel.com/sites/landingpage/pintool/downloads/pin-3.11-97998-g7ecce2dac-gcc-linux.tar.gz
- tar -zxvf pin~.tar.gz

# Copy the files in pin directory to pin_kit in sniper directory.
- cd $SNIPER_ROOT
- mkdir pin_kit
- cp -r /ORIGINAL/PIN/DIRECTORY/* ./pin_kit/

# Patch sniper with 'sniper-7.2-pinversion-fix-pin3.10.patch' file (patch file can be found in this repo.)
- patch -p1 < ./sniper-7.2-pinversion-fix-pin3.10.patch

# Set SNIPER_ROOT, and PIN_ROOT in .bashrc.
- export SNIPER_ROOT='/PATH/TO/YOUR/SNIPER'
- export PIN_ROOT='/PATH/TO/YOUR/SNIPER/pin_kit'

# add *using namespace std;* in the following header files.
- sift/standalone_pin3.0/globals.h
- sift/recorder/globals.h
- frontend/pin-frontend/globals.h

- make -j
