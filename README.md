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

## Week-1
### Day-1
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

### Day-2

<details>
<summary> Overview of '.lib' file </summary>
Firstly lets open the sky130_fd_sc_hd__tt_025C_1v80.lib using the Vim editer.<br />
 
  ```bash
  cd ASIC/sky130RTLDesignAndSynthesisWorkshop/lib/
  gvim sky130_fd_sc_hd__tt_025C_1v80.lib
  ```
The nomenclature of the above .lib file is :
1. sky - skywater
2. 130 - 130 nanometer(nm)
3. tt - typical  library
4. 025C - Temperature
5. 1v80 - Voltage
<br />

When we look into a library 'Process Voltage Temparature' is relevant for a design to work.<br />
1. Process is important because of variations in the fabrication.
2. Voltage is important because there will be variations in circuit behaviour due to the same.
3. Semiconductors are very dependent on temperature and we would need the design to work in a wide range of        geographies having different temperatures.

We need to factor in all these conditions when designing and so our libraries will also model these specifications.<br />

Below figure shows the the library sky130_fd_sc_hd__tt_025C_1v80.lib on Vim edior:<br />

![sky_lib_file_gvim](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/fb41ff86-137e-46b5-b6f0-b9b4c8b54c5e)

The Below figure shows both the library sky130_fd_sc_hd__tt_025C_1v80.lib and the .v file sky130_fd_sc_hd.v which consists of the design of any given cell in the above-mentioned library:<br/>
![i2](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/7f61d623-da9d-4dba-be2e-c58cadc93454)


The Below side by side figure shows the details of different flavours of a 2 input and gate:<br />
Here it is seen that the area of all three are different.On Day 1 we discussed the effect of the area in efficiency and delay etc..<br />
![i1](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/3d5da99e-3fa0-48cd-b406-6729ebdd8bfe)


Below are some of the Vim commands used:<br />
```bash
:syn off "turn off highlighting
:se hls  "highlight cell
:se nu   "see line numbers
:g//     "see all the cells('highlighted ones')
:sp <directory>    "open a file with a directory along with 
:vsp     "opens the same file again side by side         

```
</details>

<details>
<summary> Hierarchical Synthesis Vs. Flat Synthesis </summary>

**Hierarchical Synthesis**

Hierarchical synthesis is the process of dividing a large number of modules into smaller, more manageable sub-modules or blocks. Before being merged into the larger system, each of these sub-modules can be synthesized or developed independently. This method enables efficient design, optimization, and verification of individual components while preserving a systematic and organized design process. The following is an example of the hierarchical synthesis of the verilog file multiple module:

```bash
module sub_module2 (input a, input b, output y);
   assign y = a | b;
endmodule

module sub_module1 (input a, input b, output y);
   assign y = a&b;
endmodule


module multiple_modules (input a, input b, input c , output y);
   wire net1;
   sub_module1 u1(.a(a),.b(b),.y(net1));  //net1 = a&b
   sub_module2 u2(.a(net1),.b(c),.y(y));  //y = net1|c ,ie y = a&b + c;
endmodule
```
<br />
In this scenario, the multiple_modules module instantiates two sub_modules, sub_module1 implementing the AND gate and sub_module2 implementing the OR gate, both of which are integrated in the multiple_modules. Synthesise the numerous modules using the commands listed below:

```bash
# Remove "#" if needed
cd /home/tyrionlanni/Desktop/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
read_verilog 
read_verilog multiple_modules.v 
synth -top multiple_modules
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show multiple_modules
write_verilog multiple_modules_hier.v
```
![multiple_module](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/5e656f72-2698-4bb9-a7bd-e17b0bb2032c)

![h_multiple_module_netlist](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/b7342bea-49f9-4f3a-87c7-ef8712c637dc)

<br />

**Flat Synthesis**
Flattening the hierarchy refers to the process of reducing a design's hierarchical structure by collapsing or merging lower-level modules or blocks into a single, cohesive representation. Flattening can be accomplished with Yosys using the flat command. Yosys' example of flattening the hierarchical structure:

```bash
 cd /home/tyrionlanni/Desktop/ASIC/sky130RTLDesignAndSynthesisWorkshop/verilog_files
 yosys
 read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
 read_verilog 
 read_verilog multiple_modules.v 
 synth -top multiple_modules
 abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
 flatten
 show
 write_verilog multiple_modules_flat.v
```
![sky_lib_file_gvim](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/41f950d7-5db8-4e47-ab40-12509fb5b890)
![f_multiple_module](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/fea90e48-b692-47ca-a167-0da6ece47e76)
![f_netlist](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/e2807d97-dbdf-4d4b-a8b6-f32c79f910b1)


    The flatten command flattens the hierarchy and turns the design into a single module by generating AND and OR gates for the logic inferred by the submodule illustrated in the images above.
<br />
</details>

<details>
<summary> Types of Flip-Flops and various coding styles </summary>
<br />
    
**Need of using Flip-Flops**
<br />
Consider the logic diagram below, which has a gate and an or gate.
There is a propagation delay, which causes output glitches. This is a major problem because as the number of combinational circuits increases, so does the number of glitches.
![logic-d2](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/a803013c-84aa-4e97-801e-5af74fb781e3)
The blue-colored area in the figure below depicts the issue generated by the preceding logic diagram.
![glitch-d2](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/6ed6173c-a939-40f8-b90b-fddb4c3c2f85)

As previously said, more combinational circuits indicate more glitches; therefore, to minimize glitches, we must store the data, which is accomplished through the use of flops.
![dff](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/13fb471b-5991-4fbb-b676-612a307cd783)

The diagram above depicts the above-mentioned problem and solution. D-FFs produce output solely at the position of the CLK. As a result, the next combinational circuit (block) will only observe a stable input.

**Different Methods to code Flop**
<br />
Below are the three different ways in which we can code the flop.
1. Synchronous & Asynchronous reset
2. Synchronous reset
3. Asynchronous reset

<br />

![diff-FF](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/350944a0-b87d-4b0a-94e2-4f955378813a)

<br />

We will use Iverilog and GTKwave to simulate D-Flip flops with Asynchronous reset & set, Synchronous, and Synchronous & Asynchronous reset.

<br />

**Asynchronous reset:**
<br />
We'll be using a.v file called 'dff_asyncres.v' and its related testbench in this example. Run it through Verilog and then simulate it with GTKwave ash, as demonstrated below.
<br />
![Screenshot from 2023-08-15 18-34-01](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/a7c7f1bc-6bcf-432d-9a8a-13ba78dc905c)
<br />
The design's output waveform is shown below.
In this scenario, we can see that the output q follows the clk about the 550ns mark. In other words, q is synchronous with the clock.
<br />
![Screenshot from 2023-08-15 18-38-59](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/f2ef3a9c-7deb-4b31-89a8-c3107ffead51)
<br />

If we estimate this point to be between 1090ns and 1100ns. When async_reset is set to true, the output 'q' becomes low immediately. This is known as asynchronous reset. As shown in the diagram below.

<br />

![Screenshot from 2023-08-15 18-48-29](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/33994941-53a7-46aa-8862-e09ac43e5c17)

<br />

**Asynchronous set:**

We follow the same procedure here. Below are displayed the simulation output waveforms.
In the waveform below, the async_set is low between 500ns and 600ns, causing the output to seek for changes in 'd' based on the clock.
<br />

![Screenshot from 2023-08-15 19-11-24](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/d27ab948-e995-469f-b601-ed566be49fb9)

<br />

When the async_set is high in the following waveform, the output is set high and does not follow the 'd' input.
<br />
![Screenshot from 2023-08-15 19-12-12](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/bf24ee4e-9e83-44cf-a4e2-7ba329291b09)

<br />
**Synchronous reset**
The simulation stages are the same, except that we use the dff_syncres.v file and its associated test bench.
When the sync_reset is high between 500ns and 600ns, the output follows the clock, as shown in the waveform below.
As demonstrated below:
<br />
![Screenshot from 2023-08-15 19-29-57](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/9a192a73-24ad-4e05-a82b-0c0c9f51a1a5)
<br />
**Synthesis of the above three designs:**

Synthesis output for Asynchronous reset:
![asynchronous_reset](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/bae288ea-ff21-490c-a074-acdaed7d31d8)
<br />

Synthesis output for Asynchronous set:
![asynchronous_set](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/df241aac-0d45-4313-9a8c-a2a139191492)
<br />

Synthesis output for Synchronous reset:
![synchronous_reset](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/67bfc45d-86b4-4b6a-a87d-63c9ee4beeb7)
<br />

</details>    

<details>
<summary> Optimizations </summary>
This section addresses several unique situations. Specifically, two unusual.v files.
Let's use the following Shell command to open them in the Vim editor:

```bash
gvim mult_*.v -o
```
Here we are opening two files mult_2.v and mult_8.v.
Let us consider the first one 'mult_2.v' :
The below figure shows the mult_2.v file.
<br />
![opti-1](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/396e7304-6746-4c46-ace9-4c7b30ec316a)
<br />
The block diagram below explains the basic functionality of the design:
<br />
![mux-lab2-opti](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/ad856aaf-0349-492b-8036-2185a11bfab1)
<br />
But, as a specific case, there must be a twist.
There appears to be no need for any additional hardware components. The input 'a' and output 'y' are shown in the diagram below.
(The output y is just a zero appended to 'a' a,1'b0. It is depicted below.)
<br />
![260248865-d32db5ed-227b-47ef-a8b6-1e38c4ede5bd](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/d417d5ac-bcda-4003-b806-f7ad8595381c)
<br />
In the below screenshot, we can see there are no hardware components required.
![mul2](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/7f1ea224-c327-4ea6-bd45-f5013aa1bc9e)
<br />
The schematic diagram for the same is shown below.
![mul2-schematic](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/49adb2f2-c2d6-474d-a248-22aca61a7791)
<br />

**mult_8.v**
<br />
Following the similar exercise as done above for mult_8.v RTL design
The figure below shows the mult_8.v file:
<br />
![mult_8](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/9aa8ceaf-a2aa-4229-99d4-a776b50b3026)

<br />
Here we are doing ax9=y, which can be rewritten as {ax(8+1)=y}
ax9 = {a,0,0,0} + a ----> {a,a}
<br />


![mult8](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/8680cfc0-77a5-49b3-9c76-4bdaabc64b2b)

<br />
The figure below shows that there are no hardware components required:
<br />


![mult8-show-yosys](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/a8187814-ed4c-4d0a-9172-33c28886643b)

<br />
Schematic Diagram for the same:
<br />

![schematic-mult8](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/f6454d06-c115-4324-8746-ef516a2213ae)

<br />


</details>

## Week-3
### Day-3 
<details>
<summary> Intro to Optimizations </summary>
The principles of optimization serve as the foundation for obtaining improved performance, efficiency, and functionality in the vast world of ASIC design. We can ensure that the combinational logic in your ASIC design is fine-tuned for optimal performance and efficiency by using techniques such as Boolean logic optimization, logic synthesis, and technology mapping.

</details>


<details>
<summary> Combination logic optimizations </summary>
    
Combinational optimization is a key component in the ASIC design process, focused on logic circuits that generate output entirely dependent on their current input values. At this stage, optimization aims to refine the logic gates and their interconnections in order to achieve minimal propagation delays, low power consumption, and compact layouts. The commands for the same are listed below:

<br />

```bash
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog opt_check.v
yosys> synth -top opt_check
yosys> opt_clean -purge
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```

<br />

A schematic of the optimized design is shown below:

<br />

![Screenshot from 2023-08-15 21-43-03](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/02822a32-b282-4764-9079-168690e39a64)

<br />

A schematic of the optimized design of optcheck_2.v (y=a?1:b) is shown below:

<br />

![Screenshot from 2023-08-15 21-45-45](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/494f2d1a-337d-4cd3-a4a6-816032fd9aa5)

<br />

A schematic of the optimized design of optcheck_3.v (y=a?(c?b:0):0) is shown below:

<br />

![Screenshot from 2023-08-15 21-47-58](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/3d8824b9-3ef5-42fd-a850-bfd0f0078ace)

<br />

A schematic of the optimized design of optcheck_4.v (y = a?(b?(a & c ):c):(!c)) is shown below:

<br />

![Screenshot from 2023-08-15 21-49-30](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/663dea1c-a1aa-44ea-97f1-73fec0752e59)

<br />

A schematic of the optimized design of multiple_module_opt.v is shown below:

<br />

![Screenshot from 2023-08-15 21-53-15](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/d03bfe2a-7900-48a2-afa9-ed95556fb270)


</details>


<details>
<summary> Sequential logic optimizations </summary>

<br />

On the other hand, sequential optimization explores the complexity brought on by memory components and feedback loops within a circuit. Sequential logic is created by these elements, in which the result is dependent not only on the inputs being used at the time but also on earlier states. A comprehensive strategy is required to achieve optimal performance in sequential logic, which includes elements such as clock frequency, setup and hold periods, and routing congestion.
Commands for simulation of the design 'dff_const1.v' is shown below:

<br />

```bash
iverilog dff_const1.v tb_dff_const1.v
./a.out
gtkwave tb_dff_const1.vcd
```
<br />

**dff_const1**

The waveform representation obtained after the simulation of dff_const1 is shown below:

<br />

![Screenshot from 2023-08-15 22-14-23](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/e3f4a05e-3d22-4fd7-a71b-8cba45b30c27)


<br />

The schematic obtained after the synthesis of dff_const1 is shown below:

<br />

![Screenshot from 2023-08-15 22-29-56](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/a2734827-52c2-4f15-adde-9fbd82b27730)


<br />

**dff_const2**

The waveform representation obtained after the simulation of dff_const2 is shown below:

<br />

![Screenshot from 2023-08-15 22-16-19](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/1ff256fd-590c-4b02-b9c5-fea770b20f9c)


<br />

The schematic obtained after the synthesis of dff_const2 is shown below:

<br />

![Screenshot from 2023-08-15 22-32-25](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/e814ee9d-6e52-4022-88f6-93d8c678f3b5)


<br />

**dff_const3**

The waveform representation obtained after the simulation of dff_const3 is shown below:

<br />

![Screenshot from 2023-08-15 22-17-21](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/96b1f128-21b4-461d-b2d9-fe4a2cce4797)


<br />

The schematic obtained after the synthesis of dff_const3 is shown below:

<br />

![Screenshot from 2023-08-15 22-33-31](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/b838b5c4-09e6-44ef-9a2b-cbfebf4bfd2a)


<br />

**dff_const4**

The waveform representation obtained after the simulation of dff_const4 is shown below:

<br />

![Screenshot from 2023-08-15 22-18-19](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/82c9fbed-e47b-42c9-97ce-569ea7cedd5d)


<br />

The schematic obtained after the synthesis of dff_const4 is shown below:

<br />

![Screenshot from 2023-08-15 22-34-43](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/bd47808e-f4a8-4463-a823-0ccab994afca)


<br />

**dff_const5**

The waveform representation obtained after the simulation of dff_const5 is shown below:

<br />

![Screenshot from 2023-08-15 22-19-18](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/f111989b-d695-4951-bcf2-1d4be1d33520)


<br />

The schematic obtained after the synthesis of dff_const5 is shown below:

<br />

![Screenshot from 2023-08-15 22-36-11](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/1e565fbd-aee5-4d42-b568-73552022676d)


<br />

**counter_opt**

<br />

The schematic obtained after the synthesis of counter_opt is shown below:

<br />

![Screenshot from 2023-08-15 22-42-07](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/ccd01f82-dfdf-4150-99e9-84fc85b91dc5)


<br />


**counter_opt2**

<br />

The schematic obtained after the synthesis of counter_opt2 is shown below:

<br />

![Screenshot from 2023-08-15 22-45-19](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/76452a4d-5fc1-493b-b967-45b9c1021236)


<br />



</details>

### Day-4 
<details>
<summary> Overview of Gate Level Simulations and Synthesis level mismatch </summary>

Gate-level simulation is critical in digital hardware design and verification, particularly in VLSI, FPGA, and ASIC design. It includes simulating a digital circuit's behavior at the gate level, which is the lowest level of abstraction in the design hierarchy. Before fabrication or hardware implementation, gate-level simulation can help evaluate the validity of a circuit's logic and functionality. 
Yosys generates verilog code to map gate-level netlists to conventional cell libraries later. This code is functionally comparable to the RTL design code that we wrote. The netlist is simulated to check that functionality is retained after synthesis. The netlist is constructed using gate models that are either timing or functionally aware, or both. Timing awareness relates to knowledge of gate delays.
Ideally, we expect gate-level netlists to perform similarly to RTL designs. However, it may fail to perform as planned due to a variety of factors such as missing signals in the sensitivity list, incorrect usage of blocking and non-blocking statements, and poor RTL design.

</details>


<details>
<summary> Overview of Blocking and Non-blockin</summary>

Blocking assignments are executed in the order that they appear in the code. When a blocking assignment occurs, the expression on the right-hand side (RHS) is immediately evaluated, and the signal on the left-hand side (LHS) is updated with the new value. Non-blocking assignments, on the other hand, are not immediately executed. Instead, at the end of a procedural block's execution, all non-blocking assignments are assessed concurrently.

</details>

<details> 
<summary> Simulation and synthesis: ternary_operator_mux </summary>

<br />
**Simulation:**

Follow the below command to simulate the ternary_operator_mux:

<br />

```bash
iverilog <name verilog: ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```

<br />

The resultant waveform after the simulation of ternary_operator_mux is shown below:

<br />

![Screenshot from 2023-08-15 23-21-21](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/ab1c465a-e4bb-410e-8163-9d4453369ba2)


<br />

**Synthesis & Netlist**

<br />

Follow the below-given commands to synthesize the ternary_operator_mux:

<br />

```bash
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog ternary_operator_mux.v
yosys> synth -top ternary_operator_mux
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> write_verilog -noattr ternary_operator_mux_net.v
yosys> show
```

<br />

The resultant waveform after the simulation of ternary_operator_mux is shown below:

<br />
![Screenshot from 2023-08-15 23-22-05](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/7ff970db-0b60-416d-9d31-e7f425b4e6e2)

<br />

![Screenshot from 2023-08-15 23-22-18](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/fa1f70dd-64d0-40ac-b3fa-92e174a8c9df)


<br />

**GLS**

<br />

Follow the below-given commands for GLS of the ternary_operator_mux:

<br />

```bash
iverilog <path to verilog model: ../mylib/verilog_model/primitives.v> <path to sky130_fd_sc_hd__tt_025C_1v80.lib: ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib> <name netlist: ternary_operator_mux_net.v> <name testbench: tb_ternary_operator_mux.v>
./a.out
gtkwave tb_ternary_operator_mux.vcd
```

<br />

Below is the simulation which matches with pre-synthesis simulation:

<br />

![Screenshot from 2023-08-15 23-22-51](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/8b303f91-f5c5-419a-b02b-87bab1e96b83)


<br />


</details>

<details> 
<summary> Simulation and synthesis: bad_mux </summary>

<br />
**Simulation:**

Follow the below command to simulate the bad_mux:

<br />

```bash
iverilog <name verilog: bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```

<br />

The resultant waveform after the simulation of ternary_operator_mux is shown below:

<br />



<br />

**Synthesis & Netlist**

<br />

Follow the below-given commands to synthesize the ternary_operator_mux:

<br />

```bash
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog ternary_operator_mux.v
yosys> synth -top ternary_operator_mux
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> write_verilog -noattr ternary_operator_mux_net.v
yosys> show
```

<br />

The resultant waveform after the simulation of ternary_operator_mux is shown below:

<br />



<br />

**GLS**

<br />

Follow the below-given commands for GLS of the ternary_operator_mux:

<br />

```bash
iverilog <path to verilog model: ../mylib/verilog_model/primitives.v> <path to sky130_fd_sc_hd__tt_025C_1v80.lib: ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib> <name netlist: ternary_operator_mux_net.v> <name testbench: tb_ternary_operator_mux.v>
./a.out
gtkwave tb_ternary_operator_mux.vcd
```

<br />

Below is the simulation which matches with pre-synthesis simulation:

<br />



<br />


</details>


### Day-5 
<details>
<summary> Overview </summary>

To achieve optimal performance and functionality in the field of ASIC VLSI system design, effective decision-making and control flow techniques are critical. This is where conditional structures like "if" and "case" statements come into play. These statements are extremely useful for controlling the behaviour of digital circuits, allowing designers to build dynamic reactions based on specified conditions or input values. The complicated interplay between these conditional statements and the underlying hardware architecture is the foundation for creating sophisticated and responsive ASIC designs in this setting. 

</details>

<details>
<summary> Incomplete If case labs </summary>

<br />

<details>
<summary> Simulation and synthesis of incomp_if </summary>

<br />

A simulation and synthesis depiction is shown below, along with the results of the simulation process. Analysis reveals that an inferred latch has materialised inside the design. This conclusion is based on the observation that the output constantly maintains a constant value when the "select" signal fails to acquire a high state.

<br />

![Screenshot from 2023-08-15 23-46-03](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/631f25b1-0299-4217-98b9-6642b2df426f)


<br />

![Screenshot from 2023-08-15 23-46-22](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/66c96343-47ce-43b5-856f-6e61db6c76e0)


<br />

</details>


<br />

<details>
<summary> Simulation and synthesis of incomp_if2 </summary>

<br />

The simulation and synthesised representation of incomp_if2 are presented here.

<br />

![Screenshot from 2023-08-15 23-48-02](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/35c07f96-2718-4b0f-9854-43000987610e)


<br />

![Screenshot from 2023-08-15 23-48-16](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/5fe1b869-6a6c-46c3-b059-eb8642cdb4be)


<br />

</details>

<br />

</details>


<details>
<summary> Simulation and synthesis of incomp_case and comp_case </summary>

In essence, a "case" statement involves evaluating a given expression against a set of predefined conditions, known as case values. Once a match is found between the expression and a case value, the associated block of logic is executed. This allows for the implementation of various pathways based on different input scenarios.

<br />

```bash

```

<br />

The representation of simulation and synthesis is illustrated below. This behaviour is most noticeable when the "select" signal is assigned a value of 2 or 3, with special focus on the condition where the second bit of the "select" signal, indicated as sel[1,] asserts a logic level of 1.

<br />

![Screenshot from 2023-08-15 23-49-59](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/854ede61-f9b2-443b-8e05-e076b975055c)


<br />

<br />

![Screenshot from 2023-08-15 23-50-13](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/e48b8c22-1232-46d5-90ce-271eb9eea441)


<br />

Below is the representation of incomp_case

<br />

![Screenshot from 2023-08-15 23-50-26](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/f1044be2-695a-47b3-b1a1-534c057fe275)


<br />

![Screenshot from 2023-08-15 23-50-43](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/ab494141-86fd-4cce-bd90-e2114fa38566)


<br />

</details>

<details>
<summary> Synthesis of partial_case_assign </summary>

A representation of the design achieved is shown here, and within it, a clear consequence corresponds with our objectives. As expected, a single latch appears, controlling the behaviour of the x output. Furthermore, the design itself deduces the boolean expressions we predicted for x and y. This means that the design accurately recognises and implements the logic we intended for x and y, the way they should work based on specified conditions.

<br />

![Screenshot from 2023-08-15 23-53-19](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/4b6bfa4b-8a7d-495e-87a8-c925b62399c7)


<br />

</details>


<details>
<summary> Simulation, synthesis, and GLS of bad_case </summary>

The representation of bad_case is shown below. When the "select" input is set to the binary value "11," the simulation encounters a perplexing predicament. In this case, the simulator appears to struggle with choosing the best course of action, resulting in the y output assuming a constant value of "1."

<br />

![Screenshot from 2023-08-15 23-54-29](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/fc548e5a-4436-43d2-8025-0ba9b92609b7)


<br />

<br />

![Screenshot from 2023-08-15 23-54-43](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/2c9f3173-f2ea-4ebb-b947-afc2bc70caef)

<br />

Below are the commands for GLS:

<br />

```bash
iverilog  ../mylib/verilog_model/primitives.v ../mylib/verilog_model/sky130_fd_sc_hd.v bad_case_net.v tb_bad_case.v
./a.out
gtkwave tb_bad_case.vcd
```

<br />

The simulation that follows shows the mismatch.

<br />

![Screenshot from 2023-08-15 23-56-49](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/d8306a49-d429-41d8-89be-2b37380a4e8d)

<br />

</details>

<details>
<summary> Simulation, synthesis, and GLS of mux_generate </summary>

Below is the representation simulation of mux_generate which is 4*1 mux

<br />

![Screenshot from 2023-08-15 23-59-29](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/f8d9fa58-1d79-4207-b995-14d5fef2c492)

<br />

<br />

![Screenshot from 2023-08-15 23-59-42](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/8d3bd420-8984-4078-8703-9e6159a980c2)

<br />

To obtain GLS below are the commands:

<br />

```bash
iverilog  ../mylib/verilog_model/primitives.v ../mylib/verilog_model/sky130_fd_sc_hd.v mux_generate_net.v tb_mux_generate.v
./a.out
gtkwave tb_mux_generate.vcd
```

<br />

Below is the resulted simulation which completely matches with previous one:


<br />

![Screenshot from 2023-08-15 23-59-29](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/93c959b2-4e3f-4bec-bb3b-ab6210eb32b0)

<br />

</details>


<details>
<summary> demux_case </summary>

Below is the representation of demux_case, and by observing it, it is 1*8 demux:

<br />

![Screenshot from 2023-08-16 00-01-16](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/0c76ca27-e20b-4d59-be5f-f1ea657ce170)

<br />

</details>


<details>
<summary> demux_generate </summary>

Below is the representation of demux_generate and by observing it is 1*8 demux

<br />

![Screenshot from 2023-08-16 00-04-05](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/3c108e46-7f6e-4e40-960f-af98c5a42b96)


<br />

Below is the synthesized design representation

<br />

![Screenshot from 2023-08-16 00-04-15](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/d833b3c2-8647-4dbd-a4e8-d480cd69215e)


<br />

To obtain GLS below are the commands:

<br />

```bash
iverilog  ../mylib/verilog_model/primitives.v ../mylib/verilog_model/sky130_fd_sc_hd.v mux_generate_net.v tb_mux_generate.v
./a.out
gtkwave tb_mux_generate.vcd
```

<br />

Below is shown the simulation which perfectly matches the previous one


<br />

![Screenshot from 2023-08-16 00-04-33](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/9b119830-c6aa-46ef-b7c8-83855a503b66)

<br />

</details>

<details>
<summary> RCA </summary>

Below is the representation of rca and by observing it is 8bit rca

<br />

![Screenshot from 2023-08-16 00-07-25](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/d3921a77-abb3-47b5-81b0-3b078f81ac70)


<br />

Below is the synthesized version of 8bit rca



<br />

![Screenshot from 2023-08-16 00-07-36](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/59d64c51-eaf8-411e-be52-372a5cb01b5e)



<br />

To obtain GLS below are the commands:

<br />

```bash
iverilog  ../mylib/verilog_model/primitives.v ../mylib/verilog_model/sky130_fd_sc_hd.v mux_generate_net.v tb_mux_generate.v
./a.out
gtkwave tb_mux_generate.vcd
```

<br />

Below is shown the simulation which perfectly matches the previous one


<br />

![Screenshot from 2023-08-16 00-07-46](https://github.com/Y09mogal/IMT2020537_YashMogal_ASIC_Course/assets/79003694/582bd689-b7e4-426d-b309-18155f391e23)


<br />

</details>




### Acknowledgments
* Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.

### Contact Information
* Yash Dharemsh Mogal, IMtech 2020, International Institute of Information Technology, Bangalore Yash.Mogal@iiitb.ac.in
* Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. kunalghosh@gmail.com

## References
* https://en.wikipedia.org/wiki/Logic_synthesis
* https://en.wikipedia.org/wiki/Icarus_Verilog
* https://yosyshq.net/yosys/
* https://iverilog.fandom.com/wiki/GTKWave
* https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop

