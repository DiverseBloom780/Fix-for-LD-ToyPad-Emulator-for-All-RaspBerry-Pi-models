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

open firmware/config.txt and replace with my config.txt in releases


