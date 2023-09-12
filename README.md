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
## Steps for Synthesis in OpenLANE:

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

 
</details>
