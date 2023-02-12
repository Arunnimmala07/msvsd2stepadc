# msvsd2stepadc

# Table of Contents
  * [week 0](#week-0)  
      - [Software Installation](#Software-Installation)
      - [Create inverter and perform pre-layout using xschem or ngspice](#Create-inverter-and-perform-pre-layout-using-xschem-or-ngspice)




# week 0
---
In the week 0: we have to install linux Operting System: I installed: Ubuntu 20.04. 

OS installation

Then, We need to install following softwares or tools.

|	S .No.|Software|	Description|
| --- | --- | ---|
|1	|magic|	Layout Editor|
|2	|ngspice	|SPICE Simulation|
|4	|xschem	|Schematic Editor|
|3	|netgen	|Netlist Generator|
|5	|Open PDK (Sky130)	|Sky130 library|
|6	|ALIGN	|Analog Netlist to GDS|

# Software Installation
---


- First update ubuntu with command 
```verilog
$ sudo apt-get update
$ sudo apt-get upgrade
```
- Then install the following required pakages.

```verilog
$ sudo apt-get install m4
$ sudo apt-get install tcsh
$ sudo apt-get install csh
$ sudo apt-get install libx11-dev
$ sudo apt-get install tcl-dev tk-dev
$ sudo apt-get install libcairo2-dev
$ sudo apt-get install mesa-common-dev libglu1-mesa-dev
$ sudo apt-get install libncurses-dev
$ sudo apt-get install flex
$ sudo apt-get install bison
$ sudo apt-get install libxpm-dev
$ sudo apt-get install libxaw7-dev
$ sudo apt-get install lib32readline8 lib32readline-dev
$ sudo apt-get install libreadline-dev 
```
### Magic
Magic is an open-source VLSI layout tool.

Install steps:
```verilog
$  git clone https://github.com/RTimothyEdwards/magic
$  cd magic
$	 ./configure
$  make
$  sudo make install
```
- [More Info](http://opencircuitdesign.com/magic/index.html)

### Netgen
Netgen is a tool for comparing netlists, a process known as LVS, which stands for "Layout vs. Schematic"

Install steps:
```verilog
$  git clone https://github.com/RTimothyEdwards/netgen
$  cd netgen
$	./configure
$  make
$  sudo make install
```
- [More Info](http://opencircuitdesign.com/netgen/index.html)

### Xschem
In the present electronic system the circuit diagram has to be drawn using an interactive computer program called *schematic editor* , this is usually a very first step in the design cycle of the product. Once the schematic has been drawn on the computer, the circuit connectivity and device list **(netlist)** can be generated and sent to a **circuit simulator** (spice, hspice, eldo etc..) for performing circuit simulation.

XSCHEM is a schematic capture program that allows to interactively enter an electronic circuit using a graphical and easy to use interface. When the schematic has been created a circuit netlist can be generated for simulation. 

|Tool Name |Purpose|Outputs|
|Xschem| Schematic Editor| Netlist|

Install steps:
```verilog
$  git clone https://github.com/StefanSchippers/xschem.git xschem_git
$  cd xschem_git
$	./configure
$  make
$  sudo make install
```
- [More Info](http://repo.hu/projects/xschem/index.html)



### open_pdk
Open_PDKs is distributed with files that support the Google/SkyWater sky130 open process description https://github.com/google/skywater-pdk. Open_PDKs will set up an environment for using the SkyWater sky130 process with open-source EDA tools and tool flows such as magic, qflow, openlane, netgen, klayout, etc.

Install steps:
```verilog
$  git clone https://github.com/RTimothyEdwards/open_pdks
$  cd open_pdks
$	./configure --enable-sky130-pdk
$  make
$  sudo make install
```


### ALIGN

- Installing ALIGN
```verilog
# Clone the ALIGN source
git clone https://github.com/ALIGN-analoglayout/ALIGN-public

cd ALIGN-public

# Install virtual environment for python
sudo apt -y install python3.8-venv

# Install the latest pip
sudo apt-get -y install python3-pip

# Create python virtual envronment
python3 -m venv general

source general/bin/activate

python3 -m pip install pip --upgrade

pip install pandas
pip install scipy
pip install nltk
pip install gensim

pip install setuptools wheel pybind11 scikit-build cmake ninja

# Install Boost using
sudo apt-get install libboost-all-dev
# Installing lp_slove
sudo apt-get update
sudo apt-get install lp-solve

# Install ALIGN as a user
pip install -v .

# Install ALIGN  as a developer
pip install -e .

pip install -v -e .[test] --no-build-isolation
pip install -v --no-build-isolation -e . --no-deps --install-option='-DBUILD_TESTING=ON'

```

- Clone the Sky130 PDK
```verilog
cd ~/software/ALIGN-public

git clone https://github.com/ALIGN-analoglayout/ALIGN-pdk-sky130
```
- If faced this error 

- Solution
```
# First update setuptools
pip install -U setuptools
# Then use the correct package for dotenv, which is python-dotenv.
pip install python-dotenv
```

# Create inverter and perform pre-layout using xschem or ngspice
---
### Verifiying the open_pdk installation
An initial working directory can be made by copying the required files as follows:
```verilog
$ mkdir week0
$ cd week0
$ mkdir inverter
$ cd inverter
$ mkdir mag
$ mkdir netgen
$ mkdir xschem
$ cd xschem
$ cp /usr/local/share/pdk/sky130A/libs.tech/xschem/xschemrc .
$ cp /usr/local/share/pdk/sky130A/libs.tech/ngspice/spinit .spiceinit
$ cd ../mag
$ cp /usr/local/share/pdk/sky130A/libs.tech/magic/sky130A.magicrc .magicrc
$ cd ../netgen
$ cp /usr/local/share/pdk/sky130A/libs.tech/netgen//sky130A_setup.tcl .
```

#### Checking if magic works


#### Checking if xschem works


#### Checking if netgen works


#### Checking if ngspice works


### Creating inverter schematic using xschem

# Reference
- [Installing Tools](https://github.com/yathAg/Physical_Verification_SKY130A#Chapter-0---Getting-the-tools)
- [Installing ALIGN](https://github.com/sanampudig/OpenFASoC/tree/main/AUXCELL)
- [Creating Inverter](https://github.com/yathAg/Physical_Verification_SKY130A#Chapter-1---Understanding-the-design-flow)
