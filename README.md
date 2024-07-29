# BGS_4G_Telem

## Introduction
Tutorial Building BGS_4G_Telem

## 1. Install Dependencies CMake & C++ Build Environment
```Shell
tes
tes
tes
tes
```

### 3. Build and Complie
***Dependencies*** : Boost + MAVLink usual dependencies

```shell
cd
cd BGS_4G_Telem
mkdir build
cd build
cmake ..
make
```

The first messenger will take on the role of master.

### Serial
***Arguments :***
* ***baudrate*** -> baudrate.
* ***device*** -> path of a tty device.

ex : `--tty 57600 /dev/ttyUSB0`

### UDP server
***Arguments :***
* ***port*** -> listening port.

ex : `--udp_server 14550`

### UDP client
***Arguments :***
* ***IP address*** -> target IP address.
* ***port*** -> target port.

`--udp_client 192.168.1.10 14550`

### TCP server
***Arguments :***
* ***port*** -> listening port.

ex : `--tcp_server 14550`

### TCP client
***Arguments :***
* ***IP address*** -> target IP address.
* ***port*** -> target port.

`--tcp_client 192.168.1.10 14550`

### Logger
Save received messages in .raw and .ts file (.raw contains the mavlink raw data, .ts contains timestamp for each message).

***No arguments.***

`--log`

### File
Replay content of .raw and .ts files.

***Arguments :***
* ***file prefix*** -> logs are made of two files (.raw and .ts), both should be located on the same place for mavkit to find them. Example : dir/log will look for dir/log.raw and dir/log.ts files.
* ***speed multiplier*** -> floating point multiplier for the reading speed.
* ***starting time*** -> time to start in the file in seconds.

ex : `--file ../myLog 2.0 50`

### display
Output messages to stdout.

***No arguments.***

`--display`

---
You can combine almost as many messengers as you want in command line.

Example :

```Shell
./mavkit --tty 57600 /dev/ttyACM0 --udp_server 14550 --display --log --tcp_client 127.0.0.1 14551
```
