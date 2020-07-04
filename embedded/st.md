# STMicroelectronics

- STMicroelectronics is a French-Italian multinational electronics and semiconductor manufacturer headquartered in Geneva, Switzerland.
- It produces various MCU and related development boards.

## MCUs

- The STM32 family of 32-bit microcontrollers based on the Arm® Cortex®-M processor is designed to offer new degrees of freedom to MCU users.
  - [Click here](https://www.st.com/en/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus.html) to see of MCUs in the STM32 family.
  - STM32F4x series has high performance and supports Graphical User Interface, it supports almost all peripherals.

## Processor

### ARM Cortex-M

- They uses Serial Wire Debugger as the debug interface, It works with the Serial Wire Debug (SWD) connector.
  - It is a part of the ARM Debug Interface Specification v5.
  - SWD connector has one debug pin called SWDIO line - a bidirectional data line connected to the debug host(ST-Link)
    - Data like breakpoint instruction, memoery information, stop/run CPU can be sent through SWDIO.
  - SWD connector has one debug pin called SWCLK line - driven by clock from the debug host
- ARM Cortex M3/M4/M7 or higher has ITM unit.
  - The trace info comes from the Intrumentation Trace Macrocell (ITM) unit.
  - It has an additional Serial Wire Output (SWO) pin in the SWD connector for trace and the use of `printf()`
  - The SWO enables the low cost tracing technology - `SWV`(Serial Wire Viwer)
    - It is also connected to the debug circuitry(ST-Link), IDE can read message from ST-Link.
  - ITM unit uses a hardware buffer called FIFO
- For ARM Cortex M0, use openOCD based semi hosting technique to use `printf()`

### ARM7/9

- They use JTAG as the debug connector
  - It has 4 pins, while SWD connector has only 2(exclude the SWO pin)

## Boards

### Discovery Boards

- STM32 Discovery kits are a cheap and complete solution for the evaluation of the outstanding capabilities of STM32 MCUs and MPUs.
- Need an USART to USB jumpper for USB connection.
- With the integrated debugger/programmer the discovery kits are ideal for prototyping.
- It uses floating point unit.
- MCU has internal oscillator and it runs on the internal clock by default. Developer has the option to allow the MCU to run on external oscillator.
- It has an internal oscillator and an external oscillator
- It contains many onboard sensors.
- STM32F4DISCOVERY - It uses a STM32F4x microcontroller

### Nucleo Boards

- The STM32 Nucleo boards integrate an ST-Link debugger/programmer, so there is no need for a separate probe.
- It supports virtual comm port, it works directly when connect through USB.
- Nucleo has three types
  - Nucleo-32 include Arduino Nano connectors
  - Nucleo-64 include Arduino Uno rev3 & ST morpho connectors
  - Nucleo-144 include SWDST Zio expansion connector, ARDUINO® Uno, V3ST morpho expansion connector
- STM32F446RE is the model that uses STM32F4x MCU

## IDE

### STM32CubeIDE

- The official IDE for STM32 that supports multi-OS.
- It is Eclipse-based which has full compiling and debugging function.
- [Click here](https://www.st.com/en/development-tools/stm32cubeide.html) and select the OS for download.
  - For Linux, run the script it provides using `sudo`.
  - Drivers for the debugger will be automatically installed with IDE
- Floating Point Unit(FPU) should be disable if not in use.
  - Right click project in left navi panel and select properties, the select setting from the left, in MCU setting set Floating-point unit to None, set Floating-point ABI to software implementation.
- One workspace can have many different projects.
- The board in use need to be selected when creating new project.
  - Select MCU only when using customized board.
- A project can use either `C` or `C++` as its development language.
- When peripheral configuration using STM32CubeMX is not needed, set targeted project type to None.
- `Src` folder keeps all the `.c` source file, `Inc` folder keeps all the `.h` header files.
- Right click the project name in the left navi panel and click build project to compile the code
- To rebuild the project, clean project first, the build the project again.
- Right click the project select `Debug As`, select the `STM32` board to download the code onto the debugger on the board.
  - This will switch the IDE and the board into debugger mode.
- A debugger configuration is needed during the first launch.
  - enable the serial wire viwer(SWV) in the Debugger Tab
- To enaable `printf()`. Add the following code to the beginning of `syscalls.c`
  ```cpp
  /////////////////////////////////////////////////////////////////////////////////////////////////////////
  //					Implementation of printf like feature using ARM Cortex M3/M4/ ITM functionality
  //					This function will not work for ARM Cortex M0/M0+
  //					If you are using Cortex M0, then you can use semihosting feature of openOCD
  /////////////////////////////////////////////////////////////////////////////////////////////////////////
  //Debug Exception and Monitor Control Register base address
  #define DEMCR        			*((volatile uint32_t*) 0xE000EDFCU )
  /* ITM register addresses */
  #define ITM_STIMULUS_PORT0   	*((volatile uint32_t*) 0xE0000000 )
  #define ITM_TRACE_EN          	*((volatile uint32_t*) 0xE0000E00 )
  void ITM_SendChar(uint8_t ch)
  {
    //Enable TRCENA
    DEMCR |= ( 1 << 24);
    //enable stimulus port 0
    ITM_TRACE_EN |= ( 1 << 0);
    // read FIFO status in bit [0]:
    while(!(ITM_STIMULUS_PORT0 & 1));
    //Write to ITM stimulus port0
    ITM_STIMULUS_PORT0 = ch;
  }
  ```
  - Change the content of the `_write` function to `ITM_SendChar(*ptr++);`, `_write` function is what the stanard library function `printf()` calls at a lower level.
  - Make sure `SWV` is enabled in the debug config.
  - Open Window -> show View -> SWV -> SWV ITM Data Console.
  - Click configure trace button at the top right of the SWV ITM Data Console
  - Check port 0 of the ITM Stimulus Ports.
  - In the SWV ITM Data Console, click start trace.
  - In the main menu bar, start to debug, and start to run the code.
- Example code for changing register settings, The offset from the base bus memory address to each peripherals is used to located the peripherals' registers.
  ```cpp
  /**
  ******************************************************************************
  * @file    main.c
  * @author  Auto-generated by STM32CubeIDE
  * @version V1.0
  * @brief   Default main function.
  ******************************************************************************
  */
  #include<stdint.h>
  #define ADC_BASE_ADDR   			0x40012000UL
  #define ADC_CR1_REG_OFFSET 			0x04UL
  #define ADC_CR1_REG_ADDR  			(ADC_BASE_ADDR + ADC_CR1_REG_OFFSET )
  #define RCC_BASE_ADDR              0x40023800UL
  #define RCC_APB2_ENR_OFFSET        0x44UL
  #define RCC_APB2_ENR_ADDR          (RCC_BASE_ADDR + RCC_APB2_ENR_OFFSET )
  int main(void)
  {
    uint32_t *pAdcCr1Reg = (uint32_t*) ADC_CR1_REG_ADDR;
    uint32_t *pRccApb2Enr = (uint32_t*) RCC_APB2_ENR_ADDR;
    //1.Enable the peripheral clock for ADC1
    *pRccApb2Enr |= ( 1 << 8);
    //2. modify the ADC cr1 register
    *pAdcCr1Reg |= ( 1 << 8);
    for(;;);
  }
  ```
  - Use Window -> Show View -> SFRs to verify register settings.
- Debug mode uses a Memory panel to read and write bits on the RAM memory while the program is running.
- The compiler can set a optimization level that uses different strategy to convert C/C++ code into disassembly code for the MCU. Level 0 does not provide much optimization
  - Use the volatile keyword to ask the compile to access the memory frenquently in case the value of the memory will be changed when running in high optimization mode.

### STM32CubeMX

- It makes hardware configuration easy with GUI interfaces
- Clock Config
  - In RCC section of the Pin configuration page, select the Crystal mode can enable the option for on-board HSE
  - Bus speed can be multiple by a factor, this is done by using prescaler.
  - Lastly, change values on the RCC register using code to finalize the changes.
    - code generator is available for these tasks, provided by STM32CubeMX
  - MCO configuration is also configured through RCC register.
