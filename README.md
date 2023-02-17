# msvsd2stepadc

# Table of Contents
  * [week 0](#week-0)  
      - [Software Installation](#Software-Installation)
      - [Create inverter and perform pre-layout using xschem or ngspice](#Create-inverter-and-perform-pre-layout-using-xschem-or-ngspice)

* [week 1](#week-1)  
      - [reamaining Software Installation](#reamaining-Software-Installation)
      - [Create inverter and perform pre-layout using xschem or ngspice](#Create-inverter-and-perform-pre-layout-using-xschem-or-ngspice)

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

![2](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2001-44-05.png)

## Checking if xschem works

```
# Running or invoking the **xschem** tool
   
   arun@arun-Vostro-1550:~/Desktop/VSD_2stepadc/LAB1/xschem$xschem
```

![2](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2001-37-33.png)

## Checking if **netgen** works

```
# Running or invoking the **netgen** tool
   
   arun@arun-Vostro-1550:~/Desktop/VSD_2stepadc/LAB1/netgen$netgen
```

![1](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2001-46-05.png)

## Checking if ngspice works

```
# Running or invoking the **ngspice tool**
   
   arun@arun-Vostro-1550:~/Desktop/VSD_2stepadc/LAB1/xschem$ngspice
```

![1](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/ngspice.png)


# IV. Create inverter and perform pre-layout using xschem 
---
![1](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2002-57-22.png)

![1](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2003-35-29.png)

![1](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2003-35-45.png)

![1](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2003-56-44.png)

![1](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2003-56-36.png)

![1](https://github.com/Arunnimmala07/msvsd2stepadc/blob/main/Screenshot%20from%202023-02-14%2003-56-31.png)

# V. Create inverter and perform pre-layout using ngspice 

# week 1

# reamaining Software Installation

# Reference
- [Installing Tools](https://github.com/yathAg/Physical_Verification_SKY130A#Chapter-0---Getting-the-tools)
- [Installing ALIGN](https://github.com/sanampudig/OpenFASoC/tree/main/AUXCELL)
- [Creating Inverter](https://github.com/yathAg/Physical_Verification_SKY130A#Chapter-1---Understanding-the-design-flow)
