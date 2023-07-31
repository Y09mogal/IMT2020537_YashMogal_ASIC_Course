# ASIC Course Specifications
## Week-0
### Day-0 : System Installation
#### Yosys
To install Yosys, follow the below steps:
```bash
git clone https://github.com/YosysHQ/yosys.git
```
```bash
cd yosys-master 
```
```bash
sudo apt install make
```
```bash
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
```
```bash
make config-gcc
```
```bash
make
```
```bash
sudo make install
```
![yosys_installation](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/6d6ac295-19b3-4b7b-af45-4e4e6e8a90f3)


#### Iverilog
To install iVerilog :
```bash
sudo apt-get install iverilog
```
![iverilog_installation](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/bdb0271c-1280-4da5-a5da-49e631be767c)


#### gtkwave
To install gtkwave, follow these steps:
```bash
sudo apt update
```
```bash
sudo apt install gtkwave
```
![gtkwave_installation](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/1051e8dd-0bf9-4821-a511-ac1e41eaa930)
