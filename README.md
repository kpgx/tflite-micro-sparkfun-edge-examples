This repository has TfLite Micro examples specialized for the Sparkfun Edge.

The primary purpose here is to prototype how examples may be supported on a
variety of targets without needing target-specific code to be added to the
upstream Tensorflow repository.

This particular repository is **not** intended to be a supported location for
Sparkfun Edge + TFLM integration.


# Build Status

|   Build Type  |  Status  |
| -----------   |  --------- |
| Build (Linux) | [![CI](https://github.com/advaitjain/tflite-micro-sparkfun-edge-examples/actions/workflows/ci.yml/badge.svg?event=schedule)](https://github.com/advaitjain/tflite-micro-sparkfun-edge-examples/actions/workflows/ci.yml)
| Sync from tflite-micro | [![Sync from tflite-micro](https://github.com/advaitjain/tflite-micro-sparkfun-edge-examples/actions/workflows/sync.yml/badge.svg)](https://github.com/advaitjain/tflite-micro-sparkfun-edge-examples/actions/workflows/sync.yml)

`make -f Makefile TARGET=sparkfun_edge micro_speech`

`wget "https://github.com/sparkfun/AmbiqSuiteSDK/archive/master.zip"`

`cp third_party/AmbiqSuiteSDK-master/tools/apollo3_scripts/keys_info0.py third_party/AmbiqSuiteSDK-master/tools/apollo3_scripts/keys_info.py`

`python3 third_party/AmbiqSuiteSDK-master/tools/apollo3_scripts/create_cust_image_blob.py --bin gen/bin/micro_speech --load-address 0xC000 --magic-num 0xCB -o main_nonsecure_ota --version 0x0`

`python3 third_party/AmbiqSuiteSDK-master/tools/apollo3_scripts/create_cust_wireupdate_blob.py --load-address 0x20000 --bin main_nonsecure_ota.bin -i 6 -o main_nonsecure_wire --options 0x1`

`export DEVICENAME=/dev/ttyUSB0`

`export BAUD_RATE=921600`

`python3 third_party/AmbiqSuiteSDK-master/tools/apollo3_scripts/uart_wired_update.py  -b ${BAUD_RATE} ${DEVICENAME} -r 1 -f main_nonsecure_wire.bin -i 6`
