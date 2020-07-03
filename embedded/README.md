# Embedded Systems

- An embedded system is a computer system that has a dedicated function within a larger mechanical or electrical system.
- Embedded systems talk with the outside world via peripherals
  - A peripheral device is ancillary device used to put information into and get information out.

#### Integrated Circuit (IC)

- A set of electronic circuits integrated into one small flat chip of semiconductor material (usually silicon).
- This results in a chip that is orders of magnitude smaller than a circuit that would have to be built by hand using separate electronic components.
- These chips are usually mass-produced, and are used in tons of electronics.
- ICs can be classified into analog, digital, and mixed signal ICs.
  - Digital integrated circuits can contain logic gates, flip-flops, multiplexors, and other circuits, and are usually produced as MCUs, DSPs, or microprocessors. They can also be classified as logic ICs, memory chips, interface ICs, power management ICs, and programmable devices.
  - Analog ICs can include sensors, power management devices, RF chips, and operational amplifiers (op-amps), which process continuous signals and perform functions such as amplification, active filtering, mixing, and demodulation.
  - Mixed-signal ICs can create functions such as analog-to-digital converters (ADC) or digital-to-analog converters (DAC), digital potentiometers, as well as clock/timing ICs.
- Application Specific Integrated Circuit (ASIC)
  - An integrated circuit customized for a particular use
  - a GPU is an ASIC.
- Application-specific standard products (ASSPs)
  - They are customized ICs which used as off-the-shelf components.
  - Their uses include USB interface chips, controller chips for a PC, and a chip for a modem.

#### Microcontroller (MCU)

- It is a single integrated circuit which contains at least one CPU (processor core), memory (RAM, flash, ROM), and programmable I/O peripherals.
- They are designed for embedded applications
- Many IoT devices use microcontrollers. Their main advantage is reducing the size and cost of a similar system using separate microprocessors/memory/input/output devices.
- There are development boards that include a microcontroller. It removes the necessity of designing a PCB for the microcontroller.
  - A programeer with a debugger is an additional hardware lays in between the development boards's MCU and the USB input port.
  - Debugger also has a smaller MCU and an have its own clock. It need the installation of a firmware. USB connector should connect to it to debug. It has a jumpper and only works when jumpper are connected.
- Types of Microcontroller
  - PIC Microcontroller - PIC Stands for Peripheral Interface Controller produced by Microchip technology
  - ARM Microcontroller - ARM stands for Advanced RISC Machine.
    - It’s the most popular Microcontrollers Programming in the digital embedded system world
  - 8051 Microcontroller - an 8bit microcontroller created by Intel in 1981.
  - AVR Microcontroller - AVR stands for Alf and Vegard's RISC Processor. It was the modified Harvard architecture machine.
  - MSP Microcontroller - MSP stands for Mixed Signal Processor. It’s the family from Texas Instruments.
- Memory architecture of microcontroller are two types, they are namely:
  - Harvard Memory Architecture Microcontroller: The point when a microcontroller unit has a dissimilar memory address space for the program and data memory, the microcontroller has Harvard memory architecture in the processor.
  - Princeton Memory Architecture Microcontroller: The point when a microcontroller has a common memory address for the program memory and data memory, the microcontroller has Princeton memory architecture in the processor.
- Classification According to Instruction Set
  - CISC: CISC is a Complex Instruction Set Computer. It allows the programmer to use one instruction in place of many simpler instructions.
  - RISC: The RISC is stands for Reduced Instruction set Computer, this type of instruction sets reduces the design of microprocessor for industry standards. It allows each instruction to operate on any register or use any addressing mode and simultaneous access of program and data.
- The memory devices are divided into two types, they are
  - Embedded memory microcontroller
  - External memory microcontroller
- Useful Documents
  - Each MCU has a dataset and a user manual
  - Each development board has a schematics, user manual and specification.
- Memory Map
  - A processor in a MCU can be described by its width of the system bus.
    - 8 bits,it can provide 2^8 memory address on the system bus. from
    - 16 bits, it can provide 2^16 memory address on the system bus, from `0x0000` to `0xffff`
    - 32 bits, it can provide 2^32 memory address(4G) on the system bus, from `0x0000_0000` to `0xffff_ffff`
  - `0x` is a prefix that saying the number followed is a hexadecimal number.
  - `_` or a space is used to increase readability.
  - Different peripherals is assigned with different range of the the memory address.
  - Detailed boundaries are stated on the reference manual.
  - The relationship between the range and the assigned peripheral is called a memory map.
- Types of memory
  - ROM(Flash memory)
    - It is the program memory, stores the logic(instruction) of the program
    - stores constants data
    - stores vector tables
    - Data in the FLASH memory is accessed through the Flash controller
  - SRAM
    - It stores variables, it can also stores instructions.
    - It is the data memory
- Bus Interfaces
  - It is depicted by the MCU block diagrams.
  - Bus interfaces are the communication pathes between processors and peripherals.
  - It allows data from multiple data sources goes into the processor concurrently. The number of concurrent data trasmittion equals the number of buses.
  - There are three types of bus coming out of a processor with Advanced High-performance Bus (AHB) - Full speed, also known as HCLK speed
    - ICode Bus - Instruction Bus - get program instruction from FLASH memory
    - DCode Bus - Data Bus - get data and debug from FLASH memory
    - S-Bus - Connect to SRAM and other peripherals,
      - it can also fetch data and instruction from SRAM, it is not connected to the Flash memory.
      - its memory address boundary includes addresses for I-Bus and D-Bus.
      - All the peripherals will use S-Bus to access the processor.
      - S-Bus will be split into two AHB
        - AHB2 is used for external interfaces like USB and camera which require high I/O
        - AHB1 is used for other internal peripheral like GPIO
      - S-Bus's AHB1 will be split into two Advanced Peripheral Bus(APB) for other peripherals
        - APB1 - Half of the full speed, also known as P1CLK speed.
        - APB2 - One fourth of the full speed, also known as P2CLK speed.
        - GPIO are connected to AHB1 before the split at full speed
- Bus Matrix is where all the inter-connection happens
  - A processor is a master
  - all other peripherals it connects to are slaves.
  - Each bus interface of the master connects to certain peripherals selectively.
- Clock
  - All the peripherals are syncronized by clocks.
  - It determine the SYSCLK, SYSCLK is the main clock for the MCU
  - The clock is depicted by the clock tree in the mannul
  - The higher frenquency the clock has the higher power comsumption the board will have.
  - There are several clock resources:
    - The Cystal Oscillator (external to MCU) it is the high speed external(HSE) clock
      - Have the option to use on board external clock(Crystal mode)
      - Have the option to install own external clock or use dubeg board's clock (External mode)
    - The RC Oscillator (internal to MCU) it is the high speed internal(HSI) clock
    - Phase Locked Group (PLL) (internal to MCU) is uses HSE or HSI to boost the systen clock speed much higher.
  - All peripherals need to enable the peripheral clock before using or configuring it. It is done by changing values in the registers.
  - The register memoery location is the base address plus the offset stated in the manual

#### Microprocessor

- A microprocessor is a device that incorporates the functions of a CPU on a single IC (or a few). It is a clock-driven, register-based digital integrated circuit
- It accepts binary data as input, processes it according to an instruction set stored in its memory, and provides output.
- Different instrument sets determine the different architectures of microprocessors
  - common architectures today are generally 32-bit or 64-bit
- CPUs are almost all implemented on microprocessors, causing the two terms to be practically interchangeable.
- It is most used in personal computers or other chips used for more general purpose applications.
- Digital Signal Processor (DSP)
  - A specialized microprocessor optimized for digital signal processing.
  - optimized for continuous processing in real-time.
  - have better power efficiency and are used in mobile phones or devices with power consumption constraints.

#### System on a Chip (SoC)

- An integrated circuit with all the components of a computer, including a CPU, memory, I/O ports, and secondary storage.
- It consumes less power and take up less space than a multi-chip design, and are common in embedded systems.
- It generally refers to a single chip that does everything that used to take up multiple chips, it has at least one MCU in it.
- It is widely used in Smart phones.
- Some common ones are the Cypress Semiconductor Programmable System on a Chip (PSoC) and Altera System on a Programmable Chip (SOPC). On that topic, PSoC solely refers to the family of microcontroller-integrated SoCs produced by Cypress Semiconductor, although there are other programmable SoCs that exist.

#### Programmable Logic Device (PLD)

- a more generic terms that refers to an electronic component used to build reconfigurable digital circuits
- they differ from logic gates, which have a fixed function, as PLDs don’t have functions after being manufactured.
- Programmable logic array (PLA)
- Programmable array logic (PAL)
  - PAL was owned by Monolithic Memories, Inc. (MMI) and currently held by Lattice Semiconductor.
- Generic array logic (GAL)
- Field-programmable gate array (FPGA)
  - An FPGA is an integrated circuit that can be configured by a consumer after manufacture (“field-programmable”).
  - Its configuration is specified using a hardware description language (HDL).
  - They contain programmable logic blocks (like AND and XOR) and a hierarchy of reconfigurable interconnects that “wire together” the blocks.
  - These blocks can also contain memory elements (flip-flops, etc.)
  - Common FPGAs are the Xilinx Spartan and Virtex Series and the Altera Stratix and Cyclone Series.
- Complex Programmable Logic Device (CPLD)
  - A programmable logic device which is primarily consisted of a macrocell with logic expressions and operations.
  - It doesn’t require an external configuration ROM (needed by FPGAs) and has less internal state storage and layered logic than FPGAs. CPLDs have thousands to tens of thousands of logic gates, while FPGAs can have up to several millions.
  - They are primarily manufactured by Altera, Atmel, Cypress Semiconductor, Lattice Semiconductor, or Xilinx, and are programmed in VHDL, Verilog HDL, or Standard Test and Programming Language (JAM/STAPL).

#### Electronic design automation (EDA)

- A category of software tools for designing electronic systems for integrated circuits (ICs) or printed circuit boards (PCBs).
- Major companies producing EDAs are Altium (Altium Designer), Cadence Design Systems (Verilog, OrCAD), Autodesk (EAGLE), National Instruments (Multisim), and WestDev (Pulsonix). There is also KiCAD, an open-source EDA software, as well as many web-based EDA tools, some of which are web-based versions of the aforementioned EDAs.

#### ODROID

- A series of single-board computers capable of running Android and Linux distributions (the name comes from “open” + “Android”).
- The hardware features a SoC with a ARM CPU and an on-chip GPU. SD cards are used to store the operating system.
- The outputs include USB 2.0, USB 3.0, HDMI, and a 3.5 mm jack. There are also lower-level output pins with general-purpose input/output (GPIO) pins supporting common protocols such as I2C. There are also some models with an 8P8C Ethernet port and an eMMC port.
- Common models are the ODROID-C1, ODROID-C2, and the ODROID-XU4.

#### Raspberry Pi

- A series of single-board computers developed for teaching and protityping purposes.
- The models all featured a Broadcom SoC, with an ARM CPU and an on-chip GPU. SD cards are used to store the operating system, and the outputs include USB ports, HDMI ports, a 3.4 mm jack for audio, and lower-level GPIO pins supporting I2C and other protocols. There are also some models with an 8P8C Ethernet port and an eMMC port.
- Common models are the Model A, Model B, and Zero.

#### Arduino

- An open-source hardware and software company and user community that produces single-board microcontrollers and microcontroller kits.
- Their hardware contains an Atmel 8-bit AVR microcontroller with flash memor and a single or double row of pins that can connect to add-on modules (“shields”) and can be addressable via a I2C serial bus.
- Most models are pre-programmed with a boot loader for uploading programs to the on-chip flash memory. Some of the I/O pins can produce pulse-width modulated signals and receive analog inputs.
- Common boards are the Arduino Pro, Arduino Mega, and Arduino Yun.

#### Printed Circuit Board (PCB)

- It mechanically supports and electrically connects electrical or electronic components using conductive tracks, pads and other features etched from one or more sheet layers of copper laminated onto and/or between sheet layers of a non-conductive substrate.
- Components are generally soldered onto the PCB to both electrically connect and mechanically fasten them to it.
