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
In order to view the folder structure of the lab and the contents of the directory, follow below commands:

```bash
cd ASIC/sky130RTLDesignAndSynthesisWorkshop/
ls -R
```
![Screenshot from 2023-08-15 10-36-24](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/ab5a9c9d-75b4-429c-b4d8-375bf88979fa)

![Screenshot from 2023-08-15 10-36-45](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/a7bfb69c-44ef-4909-b3ca-0b33bd1a2a21)

![Screenshot from 2023-08-15 10-36-52](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/3301a05b-a515-49ca-ac39-61cd6c81f9bc)

All of the library files required for the lab, including the sky130 standard cell library, are located in the lib subdirectory. The Verilog models of the standard cells in the.lib file can be found in the verilog_model folder in /home/tyrionlanni/Desktop/ASIC/VLSI/sky130RTLDesignAndSynthesisWorkshop/my_lib. All of the lab experiment Verilog source files and testbench files required to simulate the designs are located in the verilog_files folder.


</details>

<details>
    <summary> Standard cell library </summary>
A standard cell library is a set of logic gates that are properly specified and appropriately characterized and can be utilized to construct a digital design. The Liberty format contains timing data for standard cells. The lib directory contains the library file sky130_fd_sc_hd__tt_025C_1v80.lib. Libraries in the SKY130 PDK are named using the following scheme:
<br />
    <Process_name><Library_Source_Abbreviation><Library_type_abbreviation>[_<Library_name>]
<br />
Where,
- sky130 - Process Technology of the PDK sky130
- fd - SkyWater Foundry
- sc - Digital standard cells
- hd - High density
- tt - Typical Timing
- 025C - 25 degree celsius Temperature
- 1v80 - 1.8V Supply Voltage


</details>

<details>
    <summary> Demonstration of iVerilog and GTKWave </summary>
    Follow the below command to change to directory that contains all the verilog files required for the lab exercise:

    ```bash
    cd /home/tyrionlanni/Desktop/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
    ```
In lab-1, we were asked to simulate the RTL design of a good_mux and its testbench using the following command:

```bash
iverilog good_mux.v tb_good_mux.v 
```
The above command will build and compile both the design and testbench and upon successful compilation an executable file 'a.out' will be generated.
Next, a '.vcd' file will be dumped upon executing 'a.out' file which captures the changes in the output of the design in correspondence with the changing input. Further, the dumped 'tb_good_mux.vcd' is provided to GTKWave as input to observe the performance of the RTL design of 'good_mux_v' against its testbench in the form of the waveform.
Commands to execute to view the waveform :
```bash
./a.out
gtkwave tb_good_mux.vcd
```
![Screenshot from 2023-08-15 13-51-28](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/d34519f4-bc55-4708-b853-53c6caeb4261)
    
</details>

<details>
<summary> Introduction of Synthesis </summary>
Following Simulation, Synthesis is required. We're doing this via a tool called Yosys, which will generate a netlist, which is a representation of the design in standard cells. For the synthesis process, commands such as read_verilog, read_liberty, and write_verilog are utilized. Following Synthesis, the netlist is also verified.
    
**Basic Synthesis flow:**
![systhesis_flow](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/891acc4e-f60f-46c0-968f-fca1add2c164)

**Liberty(.lib):**
The .lib file functions as a repository of standard cells, which are fundamental building blocks for implementing various logic functions. These cells come in different versions, such as low-speed and high-speed variants. The existence of these various gate versions raises the question of why they are necessary.

The upper limit of a digital circuit's speed is determined by the combined delay along its logical path. To attain high circuit speed, especially for operations involving high-frequency clocks, minimizing the combinational delay (Tcomb) is essential. Operating at higher frequencies inherently results in superior performance. However, if only maximum performance is sought, faster cells might seem sufficient, prompting the query of why medium and slower cell alternatives are essential.

The inclusion of slower cells addresses hold-time concerns. In digital logic circuits, the load is typically in the form of capacitance. Swift charging and discharging of this capacitance result in minimal delays. Propagation delay, a central concept, denotes the time required for an alteration in a digital logic gate or circuit's input to bring about a corresponding change in its output. It spans from the start of the input transition to the completion of the output transition.

Larger capacitance values lead to slower driving, while smaller capacitance values enable quicker driving. Achieving rapid charging and discharging of capacitance necessitates a higher current sourcing capacity. However, this requirement leads to broader transistors, which in turn consume more area and power. On the contrary, narrower transistors occupy less space and consume lower power.

The speed of cells introduces a trade-off between rapid operation, area usage, and power consumption. Providing information to the synthesis tool regarding the selection of cells is vital. Excessive use of faster cells amplifies area and power demands, potentially resulting in hold time violations. Conversely, an overabundance of slower cells compromises performance. Optimal cell selection for the synthesizer is guided by constraints that dictate the appropriate set of cells to be used.

</details>

<details>
<summary> Demonstration of Synthesis using Yosys </summary>
In this lab exercise, we are supposed to synthesize a basic 2x1 mux which was simulated in iVerilog and GTKWave as done above.
First of all, change the current working directory to the directory containing the Verilog files using the following command :

```bash
cd /home/tyrionlanni/Desktop/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
```

Next, launch the yosys by using the following code :

```bash
yosys
```

Then, read the liberty file by using the following command:

```bash
read_liberty -lib /home/tyrionlanni/Desktop/ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
```
    
Next, read the verilog design file using the following command:

```bash
read_verilog good_mux.v 
```


![Screenshot from 2023-08-15 15-21-10](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/236ddfd4-9e44-4e33-becc-58bdcfa50301)
        
Then, using the following command synthesize the verilog file:    
 
```bash
synth -top good_mux
```

 ![Screenshot from 2023-08-15 15-22-54](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/298ac461-ee07-45f4-a5ab-be8dcb7bde7f)

The synthesis output shows the number of wires used, the number of standard cells used, and the name of the standard cell.    

Next, a netlist needs to be generated using the following command:
```bash
abc -liberty /home/tyrionlanni/Desktop/ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
![Screenshot from 2023-08-15 15-27-07](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/94b7baa0-a033-476c-810c-0ee4c3d6d58c)

![Screenshot from 2023-08-15 15-27-34](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/63829715-0841-4c2f-bfa9-d5fa16a403c4)


To view the netlist, use the following command:
```bash 
show
```

![Screenshot from 2023-08-15 15-36-36](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/678c20eb-7134-4912-8e68-1d66ef466677)


The schematic above is a sky130 based 2:1 multiplexer standard cell with three inputs and one output.

The netlist and the write_verilog command is shown below:
```bash
write_verilog -noattr good_mux_netlist.v
```

![Screenshot from 2023-08-15 15-38-14](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/0cd3558c-0629-42e8-b7c5-8480efcf00fc)

![Screenshot from 2023-08-15 15-39-55](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/f0cdf9d3-068a-40f7-8800-9896a1ec33c0)


</details>

### Day2
