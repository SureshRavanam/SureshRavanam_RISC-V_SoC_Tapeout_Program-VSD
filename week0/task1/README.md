

# Digital VLSI SoC Design – Week 0  
**Getting Started with Digital VLSI SoC Design and Planning**

---

## Overview  
This document provides an introduction to the Digital VLSI SoC design flow, beginning from application-level modeling to board-level validation. The goal is to ensure that an application can run seamlessly on the designed chip, maintaining consistent functionality at every stage of the design process.

---

## Chip Modelling  
The primary objective is to run an application on a chip. To validate this:  

- Write the application in C and test it using the **GCC compiler** to obtain an output (O0).  
- Model the specifications in C format and run the same application to obtain another output (O1).  
- Ensure correctness by verifying **O0 = O1**.  

---

## RTL Architecture  
- Implement the hardware in **RTL (Verilog)** as a soft model.  
- Run the application on this RTL model and obtain output (O2).  
- Validate correctness by ensuring **O2 = O1**.  

---

## SoC Design Flow  
The Verilog code is divided into two categories:  

**Processor**  
- Must be conflict-free and fully synthesizable down to the gate level.  

**Peripherals / IPs**  
- **Macros (Synth RTL):** Repeated functional blocks.  
- **Analog IPs (Func RTL):** Convert analog signals to digital, need not be synthesizable.  
- **Interface IPs:** Bridge between the processor/chip and the external environment.  

---

## SoC Integration  
- Integrate the designed SoC with GPIOs and peripherals.  
- Performed by the **SoC Integration Engineer**.  
- Test the integrated SoC and measure the output (O3).  
- Verify that **O3 = O2**.  

---

## Microprocessor vs. Microcontroller  
- **Microprocessor:** General-purpose CPU requiring external memory and peripherals, typically used in PCs and servers.  
- **Microcontroller:** Integrates CPU, memory, and peripherals on a single chip, widely used in embedded applications.  

---

## RTL to GDSII Flow  
The RTL-to-GDSII flow includes:  

- **Floorplanning, Placement, CTS, and Routing** – Convert RTL into gate-level netlist (transistors and metal layers).  
- **GDSII Generation** – Create the layout database for manufacturing.  
- **DRC/LVS Checks** – Validate design rules and schematic equivalence.  
- **Tapeout** – Send GDSII to the foundry for fabrication.  
- **Tapein** – Receive packaged chips from the foundry.  

---

## Board Modelling  
- Develop the board with appropriate **firmware and software** to use the chip.  
- Run the application through peripherals and measure the output (O4).  
- Final goal: **O1 = O2 = O3 = O4**.  

Once this condition is satisfied, the chip is verified and ready for deployment.  

---
