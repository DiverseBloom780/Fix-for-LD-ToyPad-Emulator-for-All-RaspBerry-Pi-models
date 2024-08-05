if your are getting this when trying to run the index node.js

pi@raspberrypi:~/LD-ToyPad-Emulator $ node index.js
fs.js:119
throw err;
^

Error: ENOENT: no such file or directory, open '/dev/hidg0'
at Object.openSync (fs.js:448:3)
at new RawTransport (/home/pi/LD-ToyPad-Emulator/node_modules/node-ld/dist/transports/raw.js:11:27)
at new ToyPadEmu (/home/pi/LD-ToyPad-Emulator/node_modules/node-ld/dist/lib/ToyPadEmu.js:65:69)
at Object. (/home/pi/LD-ToyPad-Emulator/index.js:24:10)
at Module._compile (internal/modules/cjs/loader.js:816:30)
at Object.Module._extensions..js (internal/modules/cjs/loader.js:827:10)
at Module.load (internal/modules/cjs/loader.js:685:32)
at Function.Module._load (internal/modules/cjs/loader.js:620:12)
at Function.Module.runMain (internal/modules/cjs/loader.js:877:12)
at internal/main/run_main_module.js:21:11

open firmware/config.text and replace with this

# For more options and information see
# http://rptl.io/configtxt
# Some settings may impact device functionality. See link above for details

# Uncomment some or all of these to enable the optional hardware interfaces
#dtparam=i2c_arm=on
#dtparam=i2s=on
#dtparam=spi=on

# Enable audio (loads snd_bcm2835)
dtparam=audio=on

# Additional overlays and parameters are documented
# /boot/firmware/overlays/README

# Automatically load overlays for detected cameras
camera_auto_detect=1

# Automatically load overlays for detected DSI displays
display_auto_detect=1

# Automatically load initramfs files, if found
auto_initramfs=1

# Enable DRM VC4 V3D driver
dtoverlay=vc4-kms-v3d
max_framebuffers=2

# Don't have the firmware create an initial video= setting in cmdline.txt.
# Use the kernel's default instead.
disable_fw_kms_setup=1

# Disable compensation for displays with overscan
disable_overscan=1

# Run as fast as firmware / board allows
arm_boost=1

[cm4]
# Enable host mode on the 2711 built-in XHCI USB controller.
# This line should be removed if the legacy DWC2 controller is required
# (e.g. for USB device mode) or if USB support is not required.
# Remove the following line to use DWC2 in device mode:
# otg_mode=1

[cm5]
# Set DWC2 in peripheral mode if used as a device:
dtoverlay=dwc2,dr_mode=peripheral

[all]
# Enable USB OTG for all Raspberry Pi models
dtoverlay=dwc2
