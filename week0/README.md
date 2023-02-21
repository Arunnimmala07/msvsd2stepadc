# msvsd2stepadc

# Table of Contents
  * [week 0](#week-0)  
      - [Software Installation](#Software-Installation)
      - [Create inverter and perform pre-layout using xschem or ngspice](#Create-inverter-and-perform-pre-layout-using-xschem-or-ngspice)

* [week 1](#week-1)  
      - [reamaining Software Installation](#reamaining-Software-Installation)
      

# week 0
---
# I: Operating system installion  

In the week 0: we have to install linux Operting System: I installed: Ubuntu 20.04. 

Then, We need to install following softwares or tools.

|	S .No.|Software|	Description|
| --- | --- | ---|
|1	|magic|	Layout Editor|
|2	|ngspice	|SPICE Simulation|
|4	|xschem	|Schematic Editor|
|3	|netgen	|Netlist comparator or LVS|
|5	|Open PDK (Sky130)	|Sky130 library|
|6	|ALIGN	|Automating Analog Layout|

![1](https://user-images.githubusercontent.com/123537301/218300844-1c144e4d-f49e-4d2c-ac44-2a1cc8a889a4.jpg)

       A). MAGIC, B). NETGEN, C). XSCHEM, D). NGSPICE, E). OPEN_PDKs (SKY130) and F). ALIGN

# II: Software Installation
---

- First update ubuntu with command 

```verilog
 $sudo apt-get update
 $sudo apt-get upgrade
```

- Then install the following required pakages.

```
 # install git tool
   $sudo apt install -y git
    
# Install build-essential tools
    $sudo apt install -y build-essential
    
# Install csh
    $sudo apt install -y csh
    
# Install x11
    $sudo apt install -y x11-apps
    
# Install X11
    $sudo apt install -y x11-xserver-utils
    
# Install OpenGL
    $sudo apt install -y libglu1-mesa-dev freeglut3-dev mesa-common-dev
    
# Cnstall Tcl/Tk
    $sudo apt install -y tcl-dev tk-dev
    
# Install libjpeg-dev 
    $sudo apt-get -y install libjpeg-dev
    
# Install xcb
    $sudo apt-get -y install xcb
    
 # Install Xaw library
    $sudo apt-get -y install libxaw7-dev
    
# Install xterm
    $sudo apt-get -y install xterm
    
# Install bison
    $sudo apt-get -y install bison
    
# Install flex
    $sudo apt-get -y install flex
    
# Install readlines library
    $sudo apt-get -y install libreadline6-dev

# Install setup-tools
    $sudo apt-get -y install python3-setuptools
    
# Install GNU m4
    $sudo apt-get install -y m4
    
```

## A). MAGIC

Magic is an open-source VLSI layout tool.

|Tool Name| Purpose|Inputs|ouptputs|
|---------|--------|--------|-------|
|MAGIC|Layout|netlist and PDKs|GDSII|

Install steps:

```
# Change to the work directory
    $cd ~/VSD_2stepadc
    
# Clone the git repo
    $git clone https://github.com/RTimothyEdwards/magic
    
# Change into the magic directory
    $cd magic
    
# Configure magic
    $./configure
    
# Build magic
    $make
    
# Install magic
    $sudo make install
```

## B). NETGEN

Netgen is a tool for comparing netlists, a process known as LVS, which stands for "Layout vs. Schematic"

|Tool Name| Purpose|Inputs|ouptputs|
|---------|--------|--------|-------|
|NETGEN|LVS|netlist (pre-layout or from schematic) <br> and <br> netlist (post layout or from layout\)|comp.out|

Install steps:

```
# Home directory
   $cd ~/VSD_2stepadc

# Clone the repository
   $git clone https://github.com/RTimothyEdwards/netgen
   $cd netgen

# Configure the package
   $./configure

# Compile the package
   $make

# Install the package
   $sudo make install

```

- [More Info](http://opencircuitdesign.com/netgen/index.html)

## C). XSCHEM

In the present electronic system the circuit diagram has to be drawn using an interactive computer program called **SCHEMATIC EDITOR** , this is usually a very first step in the design cycle of the product. Once the schematic has been drawn on the computer, the circuit connectivity and device list **(NETLIST)** can be generated and sent to a **CIRCUIT SIMUALTOR** (spice, hspice, eldo etc..) for performing circuit simulation.

[**XSCHEM**](https://xschem.sourceforge.io/stefan/xschem_man/what_is_xschem.html) is a schematic capture program that allows to interactively enter an electronic circuit using a graphical and easy to use interface. When the schematic has been created a circuit netlist can be generated for simulation. 

|Tool Name |Purpose|Inputs|Outputs|
|----------|-------|-------|------|
|Xschem| Schematic Editor|Schematic|Netlist|

Install steps:

```
# Home directory
    $cd ~/VSD_2stepadc
    
# Clone the repository
    $git clone https://github.com/StefanSchippers/xschem.git xschem_git
        $cd xschem_git
        
# Configure the installation
    $./configure
    
# Compile the source
    $make
    
# Install the software
    $sudo make install
    
```

- [More Info](http://repo.hu/projects/xschem/index.html)

## D). NGSPICE

[NGSPICE](https://ngspice.sourceforge.io/) ngspice is the open source spice simulator for electric and electronic circuits and it is a SPICE compatible.
Download the [ngspice-39.tar.gz](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/39/ngspice-39.tar.gz/download) and extract the file by using the commands as below.

Note: ngspice does not provide schematic entry. Its input is command line or file based

```
# Home directory
    $cd ~/VSD_2stepadc
    $tar -xzvf ngspice-39.tar.gz
    $cd ngspice-39
    $mkdir release
    $cd release 
    
# Run configuration
    $../configure  --with-x --with-readline=yes --disable-debug
    
# Build
    $make 
    
# Install 
    $sudo make install
```

## E). OPEN_PDKs

Open_PDKs is distributed with files that support the Google/SkyWater sky130 open process description https://github.com/google/skywater-pdk. Open_PDKs will set up an environment for using the SkyWater sky130 process with open-source EDA tools and tool flows such as magic, qflow, openlane, netgen, klayout, etc.

Install steps:

```
# Home directory
    $cd ~/VSD_2stepadc
    
# Clone the Open PDK repository
    $git clone https://github.com/RTimothyEdwards/open_pdks
    $cd open_pdks
    
# Configure Open PDK to use Sky130 libraries
    $./configure --enable-sky130-pdk
    
# Compile the PDK
    $make 
    
# Install the PDK
    $sudo make install
```

## F). ALIGN

ALIGN (**_Analog Layout, Intelligently Generated from Netlists_**) is tool used for the analog layout automation or simple, ALIGN: A System for Automating Analog Layout. [example](https://arxiv.org/pdf/2008.10682.pdf)

|Tool Name| Purpose|Inputs|ouptputs|
|---------|--------|--------|-------|
|ALIGN|Automating Analog Layout|netlist and PDKs|GDSII|

- Installing ALIGN

```
# Home directory
    $cd ~/VSD_2stepadc

# Clone the ALIGN source
    $git clone https://github.com/ALIGN-analoglayout/ALIGN-public
    $cd ALIGN-public

# Install virtual environment for python
    $sudo apt -y install python3.8-venv

# Install the latest pip
    $sudo apt-get -y install python3-pip

# Create python virtual envronment
    $python3 -m venv general
    $source general/bin/activate
    $python3 -m pip install pip --upgrade
    $pip install align
    $pip install pandas
    $pip install scipy
    $pip install nltk
    $pip install gensim
    $pip install setuptools wheel pybind11 scikit-build cmake ninja

# Install ALIGN as a user
    $pip install -v .

# Install ALIGN  as a developer
    $pip install -e .
    $pip install -v -e .[test] --no-build-isolation
    $pip install wheel setuptools pip --upgrade
    $pip3 install wheel setuptools pip --upgrade
    $pip install -v --no-build-isolation -e . --no-deps --install-option='-DBUILD_TESTING=ON'
```

#### Making ALIGN Portable to Sky130 tehnology

Clone the following Repository inside ALIGN-public directory

```
    $git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130
```

Move SKY130_PDK folder to ~/VSD_2stepadc/ALIGN-public/pdks.
Everytime we start the tool in new terminal, run the following commands.

```
# Running ALIGN TOOL
    $python -m venv general
    $source general/bin/activate
```

Commands to run ALIGN (goto ALIGN-public directory)

```
    $mkdir work
    $cd work
```

General syntax to give inputs

```
schematic2layout.py <NETLIST_DIR> -p <PDK_DIR> -c

EXAMPLE 1:
schematic2layout.py ../examples/telescopic_ota -p ../pdks/FinFET14nm_Mock_PDK/

EXAMPLE 2:
schematic2layout.py ../ALIGN-pdk-sky130/examples/five_transistor_ota -p ../pdks/SKY130_PDK/

```

# III. Verifiying the open_pdk and Open source tools installation

An initial working directory can be made by copying the required files as follows:

```
$ mkdir LAB1
$ cd LAB1

$ mkdir xschem
$ cd xschem
$ cp /usr/local/share/pdk/sky130A/libs.tech/xschem/xschemrc .

$ cp /usr/local/share/pdk/sky130A/libs.tech/ngspice/spinit .spiceinit

$ mkdir mag
$ cd ../mag
$ cp /usr/local/share/pdk/sky130A/libs.tech/magic/sky130A.magicrc .magicrc

$ mkdir netgen
$ cd ../netgen
$ cp /usr/local/share/pdk/sky130A/libs.tech/netgen/sky130A_setup.tcl .

```

## Verifiying the open source tools and open_pdk installation



## Checking if magic works

```
# Running or invoking the **magic** tool
   
   arun@arun-Vostro-1550:~/Desktop/VSD_2stepadc/LAB1/magic$magic
   
   ```

![Screenshot from 2023-02-14 01-44-05](https://user-images.githubusercontent.com/123537301/219945118-651da5c5-981e-4fab-9d23-2fd37cdcc466.png)

```
# Running or invoking the **xschem** tool
   
   arun@arun-Vostro-1550:~/Desktop/VSD_2stepadc/LAB1/xschem$xschem
```

![Screenshot from 2023-02-14 01-37-33](https://user-images.githubusercontent.com/123537301/219944990-ae1767c8-4e22-4912-ba2c-79c3b4d41480.png)

## Checking if **netgen** works

```
# Running or invoking the **netgen** tool
   
   arun@arun-Vostro-1550:~/Desktop/VSD_2stepadc/LAB1/netgen$netgen
```

![Screenshot from 2023-02-14 01-46-05](https://user-images.githubusercontent.com/123537301/219945256-1a2ecb3f-d316-40db-bfc1-e90eb8096512.png)

## Checking if ngspice works

```
# Running or invoking the **ngspice tool**
   
   arun@arun-Vostro-1550:~/Desktop/VSD_2stepadc/LAB1/xschem$ngspice
   
```

![ngspice](https://user-images.githubusercontent.com/123537301/219946106-8bf16051-8072-4a81-a456-545f2f8c61fb.png)


# IV. Create inverter and perform pre-layout using xschem 
---

![Screenshot from 2023-02-14 02-57-22](https://user-images.githubusercontent.com/123537301/219945278-c089f8b5-21a7-4c60-926a-fe0a896f79f9.png)


![Screenshot from 2023-02-14 03-35-29](https://user-images.githubusercontent.com/123537301/219945287-419783d8-53a6-4ed0-a965-68b0ddd8ca33.png)


![Screenshot from 2023-02-14 03-35-45](https://user-images.githubusercontent.com/123537301/219945299-4f79fd2a-8ce9-4ce3-bf0e-16ab2464616c.png)

![Screenshot from 2023-02-14 03-56-44](https://user-images.githubusercontent.com/123537301/219945325-4ccdff22-7aec-4dcb-bf65-625a04c6d9b6.png)

![Screenshot from 2023-02-14 03-56-36](https://user-images.githubusercontent.com/123537301/219945319-61453f91-174f-45c1-9cd8-38afdf3d07ec.png)

![Screenshot from 2023-02-14 03-56-31](https://user-images.githubusercontent.com/123537301/219945311-d00e83a3-dc0a-4529-9f19-aae6622e8f0c.png)


# V. Create inverter and perform pre-layout using ngspice 

````
*SPICE3 file created for inverter pre-layout simulation

.option scale=0.09u

.include 130nm_bulk.txt

M1 out in gnd gnd nmos w=10 l=2
+ ad=50 pd=30 as=50 ps=30
M2 out in vdd vdd pmos w=10 l=2
+ ad=50 pd=30 as=50 ps=30

Vdd vdd 0 1.8V
Gnd gnd 0 0V
Vin in gnd pulse(0 1.8V 0 0.1ns 0.1ns 2ns 4ns)
 
*.tran 1n 20n
.dc Vin 0 1.8 0.01
.control
set color0=white
set color1=black
set color2=red
set color3=blue
set xbrushwidth=3
plot in out
run
.endc
.end

````

![Screenshot from 2023-02-19 15-50-33](https://user-images.githubusercontent.com/123537301/219944782-96d02855-7ee3-46c5-a3ee-58206f4f914a.png)


# VI. Simulation of Inverter using Ngspice

The tech file ['min2.tech']() and model file used [130nm BSIM4 model card for bulk CMOS](http://ptm.asu.edu/modelcard/2006/130nm_bulk.pm) has been for simulation of inverter and boolean function in the next section.

## VI.a. Pre-layout Simulation of Inverter using Ngspice
The figure shown the pre-layout netlist of the inverter

![image](https://user-images.githubusercontent.com/104830557/218102867-11f3b0fd-0f88-41c6-8e6e-430f0f9a5224.png)


![image](https://user-images.githubusercontent.com/104830557/218084345-fe34ce3e-eea0-4c61-a677-79e4abebec33.png)

## VI.b. Post-layout Simulation of Inverter using Ngspice
The layout  'inv.mag' was drawn in Magic as shown.
![image](https://user-images.githubusercontent.com/104830557/218103878-9ff2a9bf-27ee-4a01-b286-c82596e604c9.png)

Extract the netlist from the layout using
```
extract all
ext2spice rthesh 0 cthresh 0
ext2spice
```
Simulate the spice file extracted from magic after modifications. 

![image](https://user-images.githubusercontent.com/104830557/218105205-85ed2b21-1df1-4640-b39d-b40c4257add0.png)

Use `ngspice inv.spice`and `plot out vs time in` to get the following plot.

![image](https://user-images.githubusercontent.com/104830557/218082285-c7cc110d-a2ef-4f98-93bc-f9784ff3692e.png)

## VI.c. Comparison of Pre-layout and Post-layout timing parameters for inverter.

| Parameter    | Value from Pre-layout Simulation| Value from Post-layout Simulation|
|----------|-----|-----|
|Rise Time|40.8 ps|54.679 ps|
|Fall Time|25.01 ps|26.97 ps|
|Cell Rise Delay|32.79 ps|41.29 ps|
|Cell Fall Delay|4.3 ps|4.4 ps|
## VI.d LVS Report
The layout vs schematic compares the pre-layout netlist with the netlist extracted from the layout. The mismatch is due to the extra parasitic capacitances in the post-layout netlist. The report `comp.out` is obtained using Netgen by typing the following command.
```
~/VSD_2stepadc/LAB1/netgen$ netgen -batch lvs INV_pre.spice INV_post.spice
```
The content of the report is as shown.

Subcircuit summary:
Circuit 1: INV_pre.spice                   |Circuit 2: INV_post.spice
-------------------------------------------|-------------------------------------------
nmos (1)                                   |nmos (1)
pmos (1)                                   |pmos (1)
vsrc (2)                                   |vsrc (2)
(no matching element)                      |c (5)
Number of devices: 4 **Mismatch**          |Number of devices: 9 **Mismatch**
Number of nets: 5                          |Number of nets: 5

Netlists do not match.
Cells have no pins;  pin matching not needed.
Device classes INV_pre.spice and INV_post.spice are equivalent.
Final result: Netlists do not match.

# VII. Simulation of a function using Magic and Ngspice
Euler path and stick diagrams are helpful for getting better layouts for circuits with many MOSFETs. One such funtion is implemented here using CMOS.
Fn = Fn= [(B+D).(A+C)+E.F]'
![image](https://user-images.githubusercontent.com/104830557/218004046-205b15ce-bafd-4023-b527-9591cad9ea42.png)

## VII.a Pre-layout Simulation of function Fn using Ngspice

The netlist `fn_prelayout.spice` for the function **Fn** given can be written as 
```
***Netlist description for prelayout simulation***
M1 3 a vdd vdd pmos W=2.125u L=0.25u
M2 2 b vdd vdd pmos W=2.125u L=0.25u
M3 4 d 2 2 pmos W=2.125u L=0.25u
M4 4 c 3 3 pmos W=2.125u L=0.25u
M5 out e 4 4 pmos W=2.125u L=0.25u
M6 out f 4 4 pmos W=2.125u L=0.25u

M7 out a 6 6 nmos W=2.125u L=0.25u
M8 out c 6 6 nmos W=2.125u L=0.25u
M9 out e 7 7 nmos W=2.125u L=0.25u
M10 6 b 0 0 nmos W=2.125u L=0.25u
M11 6 d 0 0 nmos W=2.125u L=0.25u
M12 7 f 0 0 nmos W=2.125u L=0.25u

cload out 0 10f

Vdd vdd 0 2.5
V1 a 0 0 pulse 0 2.5 0.1n 10p 10p 1n 2n
V2 b 0 0 pulse 0 2.5 0.2n 10p 10p 1n 2n
V3 c 0 0 pulse 0 2.5 0.3n 10p 10p 1n 2n
V4 d 0 0 pulse 0 2.5 0.4n 10p 10p 1n 2n
V5 e 0 0 pulse 0 2.5 0.5n 10p 10p 1n 2n
V6 f 0 0 pulse 0 2.5 0.6n 10p 10p 1n 2n

***Simulation commands***
.op
.tran 10p 4n

*** .include model file ***
.include my_model_file.mod
.end
```
Run the ngspice simulation using the following commands.
```
    $ngspice fn_prelayout.spice
```
```
    ngspice 2 -> run
    ngspice 3 -> plot out
```
![image](https://user-images.githubusercontent.com/104830557/218006311-1a970c75-bc35-4d2d-9d40-a701253359c6.png)

## VII.b Post-layout Simulation of function Fn using Magic and Ngspice
![image](https://user-images.githubusercontent.com/104830557/218008163-b35a4fea-e8f9-4428-a76f-b2da4c400984.png)

Extract the netlist from the from the magic layout by typing these commands in tkcon 2.3 Main console.

![image](https://user-images.githubusercontent.com/104830557/218009160-0503c4c0-659b-4349-92e5-3644f0f54bc8.png)
The netlist `fn_postlayout.spice` generated is as shown. The netlist shows the parasitic capacitances also. Model file is same as the one used for pre-layout simulation. 

```
***Netlist description for post-layout simulation***
* SPICE3 file created from fn_postlayout.ext - technology: min2
.option scale=0.09u
M1000 a_46_38# d a_22_38# vdd pmos w=17 l=2
+  ad=102 pd=46 as=204 ps=92
M1001 out c a_14_9# gnd nmos w=17 l=2
+  ad=204 pd=92 as=204 ps=92
M1002 vdd b a_46_38# vdd pmos w=17 l=2
+  ad=204 pd=92 as=0 ps=0
M1003 gnd f a_30_9# gnd nmos w=17 l=2
+  ad=204 pd=92 as=102 ps=46
M1004 gnd b a_14_9# gnd nmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1005 out e a_22_38# vdd pmos w=17 l=2
+  ad=102 pd=46 as=0 ps=0
M1006 a_14_38# a vdd vdd pmos w=17 l=2
+  ad=102 pd=46 as=0 ps=0
M1007 a_14_9# a out gnd nmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1008 a_30_9# e out gnd nmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1009 a_22_38# f out vdd pmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1010 a_22_38# c a_14_38# vdd pmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
M1011 a_14_9# d gnd gnd nmos w=17 l=2
+  ad=0 pd=0 as=0 ps=0
C0 a_30_9# gnd 3.37fF
C1 a_14_9# gnd 6.82fF
C2 out gnd 8.40fF
C3 a_22_38# gnd 3.02fF
C4 vdd gnd 9.58fF

Vdd vdd 0 2.5
V1 a 0 0 pulse 0 2.5 0.1n 10p 10p 1n 2n
V2 b 0 0 pulse 0 2.5 0.2n 10p 10p 1n 2n
V3 c 0 0 pulse 0 2.5 0.3n 10p 10p 1n 2n
V4 d 0 0 pulse 0 2.5 0.4n 10p 10p 1n 2n
V5 e 0 0 pulse 0 2.5 0.5n 10p 10p 1n 2n
V6 f 0 0 pulse 0 2.5 0.6n 10p 10p 1n 2n
***Simulation commands***
.op
.tran 10p 4n
*** .include model file ***
.include  my_model_file.mod
.end
```
Run the ngspice simulation using the following commands.
```
    $ngspice fn_postlayout.spice
```
```
    ngspice 2 -> run
    ngspice 3 -> plot out
```
![image](https://user-images.githubusercontent.com/104830557/218010876-af06f84e-8d51-47b2-8ded-4adda43f5560.png)

## VI.c. Comparison of results
We can note that the graph of out vs time for both pre-layout simulation and post layout simulation are similar. Pre-layout simulation considers zero net delays and parasitic capacitances, hence the timing values are more optimistic. Post- layout simulation includes parasitic capacitance and non-zero netdelays, hence the timing values are more accurate.
## VI.d LVS Report

The layout vs schematic compares the pre-layout netlist with the netlist extracted from the layout. The mismatch is due to the extra parasitic capacitances in the post-layout netlist. The report `comp.out` is obtained using Netgen by typing the following command.
```
~/VSD_2stepadc/LAB1/netgen$ netgen -batch lvs INV_pre.spice INV_post.spice
```
The content of the report is as shown.
![image](https://user-images.githubusercontent.com/104830557/218120933-50b65183-17cf-464f-9a6e-413828482d80.png)

It can be seen that except for 4 extra devices(Capacitances) and corresponding nets, the pre-layout netlist and the post-layout extracted netlist are same.
