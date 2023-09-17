## Day 1
<details>
<summary>Introduction to RISC-V</summary>

**RISC-V** (pronounced "risk-five") is an open-source instruction set architecture (ISA) that has gained significant attention and popularity in recent years. It is designed to be simple, modular, and customizable, making it suitable for a wide range of applications from embedded systems to supercomputers. In this introduction to RISC-V architecture, we'll cover its key concepts and characteristics:

**Open Source Philosophy:**
RISC-V is an open-source ISA, which means its specifications are freely available to the public. This openness encourages collaboration and innovation, allowing anyone to design, implement, and customize RISC-V processors without licensing fees.

**RISC (Reduced Instruction Set Computer):**
RISC-V follows the RISC design philosophy, which emphasizes a small and simple set of instructions. This simplicity makes it easier to design efficient and high-performance processors.

**Modular and Extensible:**
RISC-V is designed with modularity in mind. It provides a base set of instructions, known as the RV32I (for 32-bit) and RV64I (for 64-bit) instruction sets, which serve as a foundation. Beyond these base sets, custom instruction extensions can be added to meet the specific needs of different applications. This extensibility enables the architecture to be tailored for various domains, from IoT devices to data centers.

**Multiple Standard Extensions:**
RISC-V offers several standard extensions, including integer (I), multiplication and division (M), atomic (A), single-precision floating-point (F), double-precision floating-point (D), vector (V), and more. These extensions add functionality to the base architecture as needed.

**Support for Different Bit Widths:**
RISC-V supports various bit widths, such as 32, 64, and 128 bits, making it adaptable to a wide range of computing environments.

**Load-Store Architecture:**
RISC-V follows a load-store architecture, where memory operations are performed using load and store instructions. This design simplifies the instruction set and helps maintain a consistent pipeline for better performance.

**User and Privileged Modes:**
RISC-V has multiple privilege levels, including user mode, supervisor mode, and machine mode. This privilege hierarchy enables secure execution of software and is useful for implementing operating systems.

**Instruction Encoding:**
RISC-V instructions are typically encoded as fixed-length 32-bit or 64-bit words, depending on the chosen bit width. The simplicity of instruction encoding contributes to the architecture's ease of implementation.

**Wide Industry Support:**
RISC-V has gained support from a broad range of industry players, including academia, startups, and established companies. This support has led to the development of RISC-V-based hardware and software ecosystems.
**Applications:**
RISC-V is used in various applications, from low-power IoT devices and microcontrollers to high-performance servers and supercomputers. Its versatility and openness make it a compelling choice for a wide array of computing tasks.
</details>
<details>
<summary>SOC Design and OpenLANE</summary>

**Open Source Digital ASIC Design**

Components of Digital ASIC Design:

![Screenshot from 2023-09-13 00-26-13](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/ad689ae7-82b5-4a0a-abbc-ec3e9eb1309a)

EDA Tools: For digital ASIC (Application-Specific Integrated Circuit) design, various EDA (Electronic Design Automation) tools are essential to complete the design process efficiently like Qflow, OpenROAD, OpenLANE, etc.

RTL: RTL IP blocks are reusable building blocks for digital designs. They encapsulate specific functions or features and are designed to be easily integrated into larger designs, reducing the need for designing these functions from scratch.

PDK: Process Design Kit is the collection of files used to model a fabrication process for the EDA Tools used to design an IC like Google+Skywater FOSS 130nm Production PDK.

**Simplified RTL to GDS Flow**
The RTL to GDS (Register-Transfer Level to Graphic Design System) flow is a series of steps and tools used in the semiconductor industry to transform a digital circuit's high-level description (RTL) into a physical layout that can be fabricated as an integrated circuit (IC) using a specific semiconductor process. Here's an overview of the typical RTL to GDS flow:

Design Specification:
Start with a clear specification of the desired functionality and performance requirements of the digital circuit.

RTL Design:
Create a Register-Transfer Level (RTL) design using a hardware description language (HDL) such as Verilog or VHDL. The RTL code describes the behavior and functionality of the digital circuit.

Simulation and Verification:
Simulate the RTL code using tools like ModelSim or VCS to verify that the design functions correctly. This involves creating testbenches and running simulations to ensure that the RTL code meets the design requirements.

Synthesis:
Use a synthesis tool (e.g., Synopsys Design Compiler, Cadence Genus) to convert the RTL code into a gate-level netlist. The synthesis process optimizes the design for area, power, and speed while targeting a specific semiconductor technology library.

Gate-Level Simulation:
Perform gate-level simulations to verify that the synthesized netlist behaves as expected and is functionally correct.

Floor Planning:
Define the physical layout of the chip, including the placement of logic blocks, standard cells, and I/O pads. This step determines the overall chip size and the placement of key components.

Place-and-Route (P&R):
Use a place-and-route tool (e.g., Cadence Innovus, Synopsys ICC) to map the gate-level netlist onto the physical chip's layout. This step involves placing the cells on the chip and routing the interconnections between them.

Clock Tree Synthesis (CTS):
Create a clock distribution network to ensure that clock signals reach all parts of the chip with minimal skew and jitter.

Power Planning:
Plan the power distribution network to ensure that all components receive the required power supply voltages and currents.

Physical Verification:
Perform physical verification checks, including Design Rule Checking (DRC), Layout vs. Schematic (LVS) checks, and Parasitic Extraction (PEX) to ensure that the layout adheres to the semiconductor process rules and matches the expected functionality.

Timing Analysis:
Perform static timing analysis (STA) to verify that the design meets its timing requirements, such as setup and hold times, clock-to-q delays, and maximum operating frequency.

Mask Generation:
Generate the mask data required for semiconductor manufacturing based on the final layout. This data includes information on the placement of transistor gates and interconnects.

Foundry Services:
Send the mask data to a semiconductor foundry for fabrication. The foundry manufactures the physical ICs using the specified semiconductor process.

Testing and Debugging:
After fabrication, the ICs undergo testing to ensure they function correctly. Any defects or issues discovered during testing may require further debugging and iteration.

Packaging and Assembly:
The fabricated ICs are packaged, which involves placing them in protective enclosures and connecting them to external pins or balls for electrical connections.

Final Testing:
Perform final testing on the packaged ICs to verify their functionality and performance.

Release and Deployment:
The final ICs are ready for deployment in various electronic devices and systems.

![Screenshot from 2023-09-13 00-15-36](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/a09241ee-1923-4a0c-86b7-a31df43b6364)

</details>

<details>
 
<summary>Installation of OpenLANE</summary>

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
```
Docker Installation:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world

sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot 


# Check for installation
sudo docker run hello-world
```
OpenLANE installation:

```bash
git clone --depth 1 https://github.com/The-OpenROAD-Project/OpenLane.git --recurse-submodules
cd OpenLane/
make
make test
cd /home/malobi/OpenLane/designs/ci
cp -r * ../
```
</details>
<details>
 
<summary>Steps for Synthesis in OpenLANE:</summary>

```bash
cd ~/OpenLane
make mount
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
run_synthesis
```


![Screenshot from 2023-09-10 23-48-30](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/3b6344f5-ab14-4a9c-8268-9c965b6e60f5)

![Screenshot from 2023-09-11 00-09-35](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/dfcc7032-5ff2-43ec-a521-ff6d90db3740)

To see the synthesis report:

![Screenshot from 2023-09-13 01-39-09](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/567dd849-0538-40b2-94a5-45520b2b7427)

```bash

61. Printing statistics.

=== picorv32 ===

   Number of wires:               9824
   Number of wire bits:          10206
   Number of public wires:        1512
   Number of public wire bits:    1894
   Number of memories:               0
   Number of memory bits:            0
   Number of processes:              0
   Number of cells:              10104
     sky130_fd_sc_hd__a2111o_2       2
     sky130_fd_sc_hd__a211o_2      101
     sky130_fd_sc_hd__a211oi_2       4
     sky130_fd_sc_hd__a21bo_2       19
     sky130_fd_sc_hd__a21boi_2       7
     sky130_fd_sc_hd__a21o_2       414
     sky130_fd_sc_hd__a21oi_2      127
     sky130_fd_sc_hd__a221o_2       65
     sky130_fd_sc_hd__a221oi_2       1
     sky130_fd_sc_hd__a22o_2       197
     sky130_fd_sc_hd__a22oi_2        2
     sky130_fd_sc_hd__a2bb2o_2      16
     sky130_fd_sc_hd__a311o_2       38
     sky130_fd_sc_hd__a31o_2        90
     sky130_fd_sc_hd__a31oi_2       10
     sky130_fd_sc_hd__a32o_2        89
     sky130_fd_sc_hd__a41o_2         2
     sky130_fd_sc_hd__and2_2       283
     sky130_fd_sc_hd__and2b_2       32
     sky130_fd_sc_hd__and3_2        77
     sky130_fd_sc_hd__and3b_2       76
     sky130_fd_sc_hd__and4_2        46
     sky130_fd_sc_hd__and4b_2        6
     sky130_fd_sc_hd__and4bb_2       3
     sky130_fd_sc_hd__buf_1       2735
     sky130_fd_sc_hd__buf_2         16
     sky130_fd_sc_hd__conb_1       106
     sky130_fd_sc_hd__dfxtp_2     1596
     sky130_fd_sc_hd__inv_2         83
     sky130_fd_sc_hd__mux2_2      1817
     sky130_fd_sc_hd__mux4_2       323
     sky130_fd_sc_hd__nand2_2      250
     sky130_fd_sc_hd__nand2b_2       2
     sky130_fd_sc_hd__nand3_2       18
     sky130_fd_sc_hd__nand3b_2       3
     sky130_fd_sc_hd__nand4_2        2
     sky130_fd_sc_hd__nor2_2       185
     sky130_fd_sc_hd__nor3_2        11
     sky130_fd_sc_hd__nor3b_2        3
     sky130_fd_sc_hd__nor4_2         4
     sky130_fd_sc_hd__nor4b_2        3
     sky130_fd_sc_hd__o2111a_2       1
     sky130_fd_sc_hd__o211a_2      224
     sky130_fd_sc_hd__o211ai_2       6
     sky130_fd_sc_hd__o21a_2       154
     sky130_fd_sc_hd__o21ai_2       94
     sky130_fd_sc_hd__o21ba_2       15
     sky130_fd_sc_hd__o21bai_2       3
     sky130_fd_sc_hd__o221a_2       19
     sky130_fd_sc_hd__o221ai_2       1
     sky130_fd_sc_hd__o22a_2        26
     sky130_fd_sc_hd__o22ai_2        1
     sky130_fd_sc_hd__o2bb2a_2       7
     sky130_fd_sc_hd__o311a_2       31
     sky130_fd_sc_hd__o311ai_2       2
     sky130_fd_sc_hd__o31a_2        21
     sky130_fd_sc_hd__o31ai_2        2
     sky130_fd_sc_hd__o32a_2        14
     sky130_fd_sc_hd__o41a_2         1
     sky130_fd_sc_hd__or2_2        337
     sky130_fd_sc_hd__or2b_2        20
     sky130_fd_sc_hd__or3_2        102
     sky130_fd_sc_hd__or3b_2        17
     sky130_fd_sc_hd__or4_2         29
     sky130_fd_sc_hd__or4b_2         6
     sky130_fd_sc_hd__xnor2_2       78
     sky130_fd_sc_hd__xor2_2        29

   Chip area for module '\picorv32': 102957.494400
```

Flop Ratio:

```bash
Flop ratio = (No.of D flipflops)/(Total no.of cells) =1596/10104 = 0.1579
```
</details>

## Day 2
<details>
 <summary>Good and Bad Floorplanning, Placement and Library cells</summary>

## Floorplan using OpenLANE
 
 To run the picorv32a floorplan in openLANE:
 ```bash
run_floorplan
```
To view the floorplan, Magic is invoked after moving to the results/floorplan directory:

```bash
magic /home/malobi/.volare/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.min.lef def read picorv32.def
```


![Screenshot from 2023-09-17 11-29-09](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/e61bf309-0e26-4732-901e-e12c94e00ed1)

![Screenshot from 2023-09-17 11-30-57](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/2fc24f2e-754c-4c3b-9cf5-ea570f9d450f)

## Run Placement in OpenLANE

Below is the command to run placement in openlane:

```bash
run_placement
```
![Screenshot from 2023-09-17 11-33-16](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/500bb8dc-2737-469c-ba9e-7472cddc8772)

![Screenshot from 2023-09-17 11-33-54](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/69ff38e6-5276-4199-b5bd-282d4041c226)

![Screenshot from 2023-09-17 11-35-27](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/4ef0f731-e30d-4afe-8adf-01f431854734)

</details>

## Day 3
<details>
 <summary>Design Library Cell using magic and ngspice</summary>

 cmos.cir file:
 
 ```bash
*** MODEL Descriptions ***

*** NETLIST Description ***

M1 out in vdd vdd pmos W=0.37u L=0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u

cload out 0 10f

vdd vdd 0 2.5

Vin in 0 2.5

*** SIMULATION Commands ***

.op

.dc Vin 0 2.5 0.05

***.include tsmc_025um_model.mod ***
.LIB "tsmc_025um_model.mod" cmos_models
.end
```

Model file:

```bash
* SPICE 3f5 Level 8, Star-HSPICE Level 49, UTMOST Level 8

.lib cmos_models 
* DATE: Feb 23/01
* LOT: T0BM                  WAF: 07
* Temperature_parameters=Default
.MODEL nmos  NMOS (                                LEVEL   = 49
+VERSION = 3.1            TNOM    = 27             TOX     = 5.8E-9
+XJ      = 1E-7           NCH     = 2.3549E17      VTH0    = 0.3907535
+K1      = 0.4376003      K2      = 8.265151E-3    K3      = 4.214601E-3
+K3B     = -3.7220937     W0      = 2.517345E-6    NLX     = 2.310668E-7
+DVT0W   = 0              DVT1W   = 0              DVT2W   = 0
+DVT0    = 0.2411602      DVT1    = 0.3707226      DVT2    = -0.5
+U0      = 316.5922683    UA      = -9.89493E-10   UB      = 2.154013E-18
+UC      = 2.474632E-11   VSAT    = 1.254499E5     A0      = 1.2735648
+AGS     = 0.2428704      B0      = 2.579719E-8    B1      = -1E-7
+KETA    = 4.87168E-4     A1      = 0              A2      = 0.5196633
+RDSW    = 120            PRWG    = 0.5            PRWB    = -0.2
+WR      = 1              WINT    = 2.357855E-8    LINT    = 1.210018E-9
+DWG     = 2.292632E-9
+DWB     = -9.94921E-10   VOFF    = -0.1039771     NFACTOR = 1.3905578
+CIT     = 0              CDSC    = 2.4E-4         CDSCD   = 0
+CDSCB   = 0              ETA0    = 3.894977E-3    ETAB    = 7.800632E-4
+DSUB    = 0.0307944      PCLM    = 1.7312397      PDIBLC1 = 0.999135
+PDIBLC2 = 4.850036E-3    PDIBLCB = -0.0866866     DROUT   = 0.8612131
+PSCBE1  = 7.995844E10    PSCBE2  = 1.457011E-8    PVAG    = 0.0099984
+DELTA   = 0.01           RSH     = 5              MOBMOD  = 1
+PRT     = 0              UTE     = -1.5           KT1     = -0.11
+KT1L    = 0              KT2     = 0.022          UA1     = 4.31E-9
+UB1     = -7.61E-18      UC1     = -5.6E-11       AT      = 3.3E4
+WL      = 0              WLN     = 1              WW      = -1.22182E-16
+WWN     = 1.2127         WWL     = 0              LL      = 0
+LLN     = 1              LW      = 0              LWN     = 1
+LWL     = 0              CAPMOD  = 2              XPART   = 0.4
+CGDO    = 3.11E-10       CGSO    = 3.11E-10       CGBO    = 1E-12
+CJ      = 1.741905E-3    PB      = 0.9876681      MJ      = 0.4679558
+CJSW    = 3.653429E-10   PBSW    = 0.99           MJSW    = 0.2943558
+CF      = 0              PVTH0   = -0.01          PRDSW   = 0
+PK2     = 2.589681E-3    WKETA   = -1.866069E-3   LKETA   = -0.0166961      )
*
.MODEL pmos  PMOS (                                LEVEL   = 49
+VERSION = 3.1            TNOM    = 27             TOX     = 5.8E-9
+XJ      = 1E-7           NCH     = 4.1589E17      VTH0    = -0.583228
+K1      = 0.5999865      K2      = 6.150203E-3    K3      = 0
+K3B     = 3.6314079      W0      = 1E-6           NLX     = 1E-9
+DVT0W   = 0              DVT1W   = 0              DVT2W   = 0
+DVT0    = 2.8749516      DVT1    = 0.7488605      DVT2    = -0.0917408
+U0      = 136.076212     UA      = 2.023988E-9    UB      = 1E-21
+UC      = -9.26638E-11   VSAT    = 2E5            A0      = 0.951197
+AGS     = 0.20963        B0      = 1.345599E-6    B1      = 5E-6
+KETA    = 0.0114727      A1      = 3.851541E-4    A2      = 0.614676
+RDSW    = 1.496983E3     PRWG    = -0.0440632     PRWB    = -0.2945454
+WR      = 1              WINT    = 7.879211E-9    LINT    = 2.894523E-8
+DWG     = -1.112097E-8
+DWB     = 9.815716E-9    VOFF    = -0.1204623     NFACTOR = 1.2259401
+CIT     = 0              CDSC    = 2.4E-4         CDSCD   = 0
+CDSCB   = 0              ETA0    = 0.3325261      ETAB    = -0.0623452
+DSUB    = 0.9206875      PCLM    = 0.833903       PDIBLC1 = 9.948506E-4
+PDIBLC2 = 0.0191187      PDIBLCB = -1E-3          DROUT   = 0.9938581
+PSCBE1  = 2.887413E10    PSCBE2  = 8.325891E-9    PVAG    = 0.8478443
+DELTA   = 0.01           RSH     = 3.6            MOBMOD  = 1
+PRT     = 0              UTE     = -1.5           KT1     = -0.11
+KT1L    = 0              KT2     = 0.022          UA1     = 4.31E-9
+UB1     = -7.61E-18      UC1     = -5.6E-11       AT      = 3.3E4
+WL      = 0              WLN     = 1              WW      = 0
+WWN     = 1              WWL     = 0              LL      = 0
+LLN     = 1              LW      = 0              LWN     = 1
+LWL     = 0              CAPMOD  = 2              XPART   = 0.4
+CGDO    = 2.68E-10       CGSO    = 2.68E-10       CGBO    = 1E-12
+CJ      = 1.864957E-3    PB      = 0.976468       MJ      = 0.4614408
+CJSW    = 3.118281E-10   PBSW    = 0.6870843      MJSW    = 0.3021929
+CF      = 0              PVTH0   = 6.397941E-3    PRDSW   = 30.410214
+PK2     = 2.100359E-3    WKETA   = 5.428923E-3    LKETA   = -0.0111599      )
*
.endl
```
Commands to open ngspice and run the simulation:

```bash
ngspice
source Cmos.cir
```
To execute:

```bash
run
setplot
display
```

Spice Simulation:
 ![Screenshot from 2023-09-17 11-41-42](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/b5d0f0ee-dcbb-4a31-a1e3-95da04a51128)

 ![Screenshot from 2023-09-17 11-41-58](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/92939ad9-1a04-4489-b48b-95e2e26df5fa)

 To execute:

```bash
run
setplot
display
```

![Screenshot from 2023-09-17 11-50-10](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/a91dc875-38fd-482a-8688-4944d2a7ef25)

## Switching Threshold

Modified Cmos file:
```bash
*** MODEL Descriptions ***

*** NETLIST Description ***

M1 out in vdd vdd pmos W=0.375u L=0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u

cload out 0 10f

vdd vdd 0 2.5

Vin in 0 0 pulse 0 2.5 0 10p 10p 1n 2n

*** SIMULATION Commands ***


.tran 10p 4n


***.include tsmc_025um_model.mod ***
.LIB "tsmc_025um_model.mod" cmos_models
.end
```
## CMOS Fabrication

## Inverter Standard Cell Layout & Spice Extraction

To see the magic layout of the CMOS inverter we'll get the magic file from vsdstdcelldesign by cloning it within Openlane directory:

```bash
git clone https://github.com/nickson-jose/vsdstdcelldesign
```
It will create a folder named vsdstdcelldesign in Openlane directory. now we will view the sky130_inv.mag file using following command. Before that we have to make sure sky130A.tech file is also in the same directory.

```bash
magic -T sky130A.tech sky130_inv.mag &
```
![Screenshot from 2023-09-17 11-53-46](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/c0cf63a3-0509-4071-a6a3-c181fb591309)

## Identification of NMOS and PMOS

![Screenshot from 2023-09-17 11-57-00](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/40bf50a3-b686-40d8-9d00-7974b4a1e3a7)

## Steps to Create Standard Cell and Extract Spice Netlist

Command:

```bash
extract all
ext2spice cthresh 0 rthresh 0
ext2spice
```
![Screenshot from 2023-09-17 12-07-57](https://github.com/malobimukherjee/Advanced_Physical_Design_using_OpenLANE/assets/141206513/4c789ca9-e9f5-44f7-b40a-7db0099f2991)

Following Spice file is created:

```bash
* SPICE3 file created from sky130_inv.ext - technology: sky130A

.option scale=10000u

.subckt sky130_inv A Y VPWR VGND
M1000 Y A VPWR VPWR pshort w=37 l=23
+  ad=1443 pd=152 as=1517 ps=156
M1001 Y A VGND VGND nshort w=35 l=23
+  ad=1435 pd=152 as=1365 ps=148
C0 A Y 0.05fF
C1 VPWR Y 0.11fF
C2 A VPWR 0.07fF
C3 Y 0 0.24fF
C4 VPWR 0 0.59fF
.ends
```

Modified the same spice file after extracting:

```bash
* SPICE3 file created from sky130_inv.ext - technology: sky130A

.option scale=0.01u
.include ./libs/pshort.lib
.include ./libs/nshort.lib
//.subckt sky130_inv A Y VPWR VGND
M1000 Y A VPWR VPWR pshort_model.0 w=37 l=23 
+  ad=1.44n pd=0 as=1.51n ps=0.156m
M1001 Y A VGND VGND nshort_model.0 w=35 l=23 
+  ad=1.44n pd=0.152m as=1.37n ps=0.148m

VDD VPWR 0 3.3V
VSS VGND 0 0V
Va A VGND PULSE(0V 3.3V 0 0.1ns 0.1ns  2ns 4ns)

C0 A Y 0.05fF
C1 VPWR Y 0.11fF
C2 A VPWR 0.07fF
C3 Y 0 0.24fF
C4 VPWR 0 0.59fF
C5 VPWR VGND 0.781f
//.ends
.tran 1n 20n
.control
run 
.endc
.end
```



</details>
