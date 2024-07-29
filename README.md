# BGS_4G_Telem

## Introduction
Tutorial Building BGS_4G_Telem

## 1. Install Dependencies CMake & C++ Build Environment

```Shell
sudo apt-get update
sudo apt install cmake build-essential libboost-all-dev
```
## 2. Install ZeroTier

```Shell
curl -s https://install.zerotier.com | sudo bash
sudo apt install zerotier-one
```

## 3. Build and Compile
```shell
cd
cd BGS_4G_Telem
mkdir build
cd build
cmake ..
make
```
## 4. Start ZeroTier Service
Ganti <network_id> dengan network anda sendiri ex: 56374ac9a43b489f
```shell
sudo systemctl start zerotier-one
sudo systemctl enable zerotier-one
sudo zerotier-cli join <network_id>
sudo zerotier-cli status
```
ZeroTier akan selalu otomatis berjalan setelah boot. jika mau mengganti netowrk bisa langsung ganti dengan perintah
commandd : `sudo zerotier-cli join <network_id>`

## 5. Start BGS_4G_Telem
Contoh : FCU terhubung ke /dev/ttyUSB0 dan mengirimkan data telemetri ke UDP 192.168.168.16 port 14550 
alamat IP bisa dilihat di Network ZeroTier yang digunakan 
```Shell
./BGS_4G_Telem --tty 57600 /dev/ttyUSB0 --udp_client 192.168.168.16 14550
```
### Selengkapnya Bisa dilihat Di Bawah ini
### Serial
* ***baudrate*** -> baudrate.
* ***device*** -> path of a tty device.
ex : `--tty 57600 /dev/ttyUSB0`

### UDP server
* ***port*** -> listening port.
ex : `--udp_server 14550`

### UDP client
* ***IP address*** -> target IP address.
* ***port*** -> target port.
`--udp_client 192.168.1.10 14550`

### TCP server
* ***port*** -> listening port.
ex : `--tcp_server 14550`

### TCP client
* ***IP address*** -> target IP address.
* ***port*** -> target port.
`--tcp_client 192.168.1.10 14550`

### Logger
Save received messages in .raw and .ts file (.raw contains the mavlink raw data, .ts contains timestamp for each message).
***No arguments.***
`--log`

### File
Replay content of .raw and .ts files.
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


## Thanks to 
### ZeroTier  : Online Server
### MAVkit    : Mavlink Converter
### MavLink   : Protocol Communication

