# ASIC Course Specifications
## Week-0

### Day-0 : System Installation

<details>
<summary> Yosys</summary>
<br />
    
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

</details>

<details>
<summary> Iverilog </summary>
<br />

To install iVerilog :
```bash
sudo apt-get install iverilog
```
![iverilog_installation](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/bdb0271c-1280-4da5-a5da-49e631be767c)

</details>

<details>
<summary> gtkwave </summary>
<br />
    
To install gtkwave, follow these steps:
```bash
sudo apt update
```
```bash
sudo apt install gtkwave
```
    
![gtkwave_installation](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/1051e8dd-0bf9-4821-a511-ac1e41eaa930)

</details>

### Day1
<details>
    <summary> Introduction to Simulator </summary>
A simulator is a piece of software that allows you to test the functionality of a circuit design before it is implemented in hardware. This is done by mimicking the design's behavior in software using a Hardware Description Language (HDL) such as Verilog or VHDL. The Register Transfer Level (RTL) design is the Verilog code that implements the circuit, which is the 
behavioral representation of the specification in an HDL language. To ensure that the RTL design adheres to the specifications, a testbench is built in HDL and simulated with the open-source
simulator, Icarus Verilog. The testbench generates stimulus signals that are applied to the RTL design, and the simulator verifies that the output signals are valid. Changes in the 
    input signals are monitored by the simulator. The simulator re-evaluates the RTL design and updates the output signals when an input signal changes. The simulator saves changes to the input 
    and output signals in a Value Change Dump (VCD) file. This file is used to display the design's behavior over time in the form of waveforms. To open the VCD file and examine the design, a 
    tool called GTKWave is needed, which aids in debugging the design and checking its operation in compliance with the specification.

 **The Iverilog-based simulation flow is shown below:** <br />
![iverilog_based_simulation_flow](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/2455c530-1f30-4912-9157-d5608a796d41)

**Steps to setup Labs Folder:** <br />

```bash
mkdir ASIC
cd ASIC
git clone https://github.com/kunalg123/vsdflow.git
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```


</details>
