# ASIC Course Specifications
## Week-0
### Day-0 : System Installation
#### Yosys
To install Yosys, follow below steps:
1.
```bash
git clone https://github.com/YosysHQ/yosys.git
```
2.
```bash
cd yosys-master 
```
3.
```bash
sudo apt install make
```
4.
```bash
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
```
5.
```bash
make config-gcc
```
6.
```bash
make
```
7.
```bash
sudo make install
```
#### Iverilog
To insatll iVerilog :
```bash
sudo apt-get install iverilog
```
#### gtkwave
To install gtkwave, follow these steps:
1.
```bash
sudo apt update
```
2.
```bash
sudo apt install gtkwave
```
