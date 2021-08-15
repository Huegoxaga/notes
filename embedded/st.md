# STMicroelectronics

* STMicroelectronics is a French-Italian multinational electronics and semiconductor manufacturer headquartered in Geneva, Switzerland.
* It produces various MCU and related development boards.

## Products

### Microcontrollers & Microprocessors

#### STM32 32-bit Arm Cortex MCUs

* The STM32 family of 32-bit microcontrollers based on the Arm® Cortex®-M processor is designed to offer new degrees of freedom to MCU users.
  * [Click here](https://www.st.com/en/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus.html) to see of MCUs in the STM32 family.
* STM32F4x series has high performance and supports Graphical User Interface, it supports almost all peripherals
* STM32F0x series is good for beginners
* Different series uses different Arm® Cortex Core from M0 to M7

## Processor

### ARM Cortex-M

* They uses Serial Wire Debugger as the debug interface, It works with the Serial Wire Debug \(SWD\) connector.
  * It is a part of the ARM Debug Interface Specification v5.
  * SWD connector has one debug pin called SWDIO line - a bidirectional data line connected to the debug host\(ST-Link\)
    * Data like breakpoint instruction, memoery information, stop/run CPU can be sent through SWDIO.
  * SWD connector has one debug pin called SWCLK line - driven by clock from the debug host
* ARM Cortex M3/M4/M7 or higher has ITM unit.
  * The trace info comes from the Intrumentation Trace Macrocell \(ITM\) unit.
  * It has an additional Serial Wire Output \(SWO\) pin in the SWD connector for trace and the use of `printf()`
  * The SWO enables the low cost tracing technology - `SWV`\(Serial Wire Viwer\)
    * It is also connected to the debug circuitry\(ST-Link\), IDE can read message from ST-Link.
  * ITM unit uses a hardware buffer called FIFO
* For ARM Cortex M0, use openOCD based semi hosting technique to use `printf()`

### ARM7/9

* They use JTAG as the debug connector
  * It has 4 pins, while SWD connector has only 2\(exclude the SWO pin\)

## Development Boards

### Discovery Boards

* STM32 Discovery kits are a cheap and complete solution for the evaluation of the outstanding capabilities of STM32 MCUs and MPUs.
* Need an USART to USB jumpper for USB connection.
* With the integrated debugger/programmer the discovery kits are ideal for prototyping.
* It uses floating point unit.
* MCU has internal oscillator and it runs on the internal clock by default. Developer has the option to allow the MCU to run on external oscillator.
* It has an internal oscillator and an external oscillator
* It contains many onboard sensors.
* STM32F4DISCOVERY - It uses a STM32F4x microcontroller

### Nucleo Boards

* The STM32 Nucleo boards integrate an ST-Link debugger/programmer, so there is no need for a separate probe.
* It supports virtual comm port, it works directly when connect through USB.
* Nucleo has three types
  * Nucleo-32, it has 32 pins include Arduino Nano connectors
  * Nucleo-64, it has 64 pins include Arduino Uno rev3 & ST morpho connectors
  * Nucleo-144, it has 144 pins include SWDST Zio expansion connector, ARDUINO® Uno, V3ST morpho expansion connector
* STM32F446RE is the model that uses STM32F4x MCU
* The Mbed site for the nucleo boards offers great pinout diagrams

## STM32CubeIDE

* The official IDE for STM32 that supports multi-OS.
* It is Eclipse-based which has full compiling and debugging function.
* [Click here](https://www.st.com/en/development-tools/stm32cubeide.html) and select the OS for download.
  * For Linux, run the script it provides using `sudo`.
  * Drivers for the debugger will be automatically installed with IDE
  * The installation come with a GCC compiler for ARM processors
    * GCC compiler for host machine needs to be installed separately\(WinGW for Windows, GCC for Mac/Linux\(`brew install gcc`\)\)
* Floating Point Unit\(FPU\) should be disable if not in use, otherwise, there will be an warning message during compilation
  * Right click project in left navi panel and select properties, the select setting from the left, in MCU setting set Floating-point unit to None, set Floating-point ABI to software implementation.

### Project Creation

* One workspace can have many different projects
  * It is defined as a folder
  * When import other projects select copy project into workplace will copy the project files into the workplace folder
  * Use `File > Switch Workplace > Others` to switch into a new workplace
  * Use `File > New > STM32 Project` to create a MCU project
  * Use `File > New > New C/C++ Project` to create a c project for host machine
  * When create new project, a compiler toolchain should be selected, the selection is determined by the machine that will be running the project
    * Use `MacOS GCC` if the project code will be running on the MacOS host machine
    * Use `WinGW GCC` for a Windows host
    * Use `Cross GCC` host machine compiler compiles code for MCU or other machine
    * Use `MCU ARM GCC`
* The board in use need to be selected when creating new MCU project
* When peripheral configuration using `STM32CubeMX` is not needed, set `Targeted Project Type` to `None`
  * Use `Board Selector` for STM produced development boards
  * Select `MCU/MPU Selector` only when using customized boards
* A project can use either `C` or `C++` as its development language.
* `HAL` is the official library used by `STM32`
  * Same code can works on various `STM32` hardwares
  * For detail search MCU model with the keyword `HAL` and read the docs in the PDF from the search result
* `Src` folder keeps all the `.c` source file, `Inc` folder keeps all the `.h` header files.
* The infinite while loop inside `main.c` contains the actually code for running for the embedded device

### Run Code

* Right click the project name in the left navi panel and click build project to compile the code
* To rebuild the project, clean project first, the build the project again.
* For `C/C++` project, open the compiled file directly to execute
* For MCU project, right click the project select `Debug As`, select the `STM32` board to download the code onto the debugger on the board.
  * This will switch the IDE and the board into debugger perspective.
* Click the play button in the debugger mode to run the app
* Click the pause button and double click on the line number to create breakpoint, click resume so the code will stop at the breakpoint
  * double click on the line number again to remove the breakpoint
* Click step into button to run the code line by line and go into a function
* Click step return button the run a function
* Click step over to run a function without step into the function
* Click the stop button to return to the code editing perspective
* Startup file copy initialized variables from code memory to SRAM memory

### Debug

* When a debug process failed to start, go to debug perspective and right click the previous debug session click `Terminate and Remove`
* A debugger configuration is needed during the first launch.
  * enable the serial wire viwer\(SWV\) in the Debugger Tab
* To enable `printf()` with `OpenOCD`
  * Select `OpenOCD` as the debug probe in the debugger config
  * In debugger config, add `monitor arm semihosting enable` in the startup tab's `Run Commands` input box
  * Right click on project, `Properties > C/C++ Build > Settings > Tool Settings > MCU GCC Linker > Miscellaneous`, in `Other Flags` add `-specs=rdimon.specs -lc -lrdimon`
  * Right before any `printf()` add `initialise_monitor_handles();`, also add `extern void initialise_monitor_handles(void);` on top
  * Exclude `syscalls.c` from build by right click this file and select `Exclude resource from build` under the `Resourse Configuration` option
  * String should end with `\n` when using this method
* To enable `printf()` with `SWV`. Add the following code to the beginning of `syscalls.c`

  ```cpp
  /////////////////////////////////////////////////////////////////////////////////////////////////////////
  //                    Implementation of printf like feature using ARM Cortex M3/M4/ ITM functionality
  //                    This function will not work for ARM Cortex M0/M0+
  //                    If you are using Cortex M0, then you can use semihosting feature of openOCD
  /////////////////////////////////////////////////////////////////////////////////////////////////////////
  //Debug Exception and Monitor Control Register base address
  #define DEMCR                    *((volatile uint32_t*) 0xE000EDFCU )
  /* ITM register addresses */
  #define ITM_STIMULUS_PORT0       *((volatile uint32_t*) 0xE0000000 )
  #define ITM_TRACE_EN              *((volatile uint32_t*) 0xE0000E00 )
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

  * Change the content of the `_write` function to `ITM_SendChar(*ptr++);`, `_write` function is what the stanard library function `printf()` calls at a lower level
  * Use `ST-Link` as the debug probe
  * Make sure `SWV` is enabled in the debug config
  * Open `Window -> show View -> SWV -> SWV ITM Data Console`
  * Click configure trace button at the top right of the SWV ITM Data Console
  * Check port `0` of the ITM Stimulus Ports.
  * In the SWV ITM Data Console, click start trace.
  * In the main menu bar, start to debug, and start to run the code

* Enable a `USART` connection in asyn mode to get serial output from the board
  * The `IDE` will install a virtual `COMM` port. For windows machine use device manager to find it. For others, look for the `dev/tty*` device file
  * Use a serial terminal program and connect to the port with baud rate specified in the UART config code will establish the connection
  * `#include <string.h>`, and define a buffer as `uint8_t buf[12];` in user code begin 1 section in main function, and put the following code inside `while(1)` loop to test the connection

    ```c
    strcpy((char*)buf, "Test\r\n");
    HAL_UART_Transmit(&huart2, buf, strlen((char*)buf), HAL_MAX_DELAY);
    HAL_Delay(500);
    ```
* Example code for changing register settings, The offset from the base bus memory address to each peripherals is used to located the peripherals' registers.

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
  #define ADC_BASE_ADDR               0x40012000UL
  #define ADC_CR1_REG_OFFSET             0x04UL
  #define ADC_CR1_REG_ADDR              (ADC_BASE_ADDR + ADC_CR1_REG_OFFSET )
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

  * Use Window -&gt; Show View -&gt; SFRs to verify register settings.

* Debug mode uses a Memory panel to read and write bits on the RAM memory while the program is running.
* Right click project and in build setting, compiler optimization panel, change the optimization level for the project
  * `L0` will disable any optimization
  * Always use `uint8_t volatile *pReg` to acesss the register memory to avoid bug caused by unexpected optimization
* Add include path in the project compiler setting to import newly created header files in the project folder
* The memory browser window can be used to search for the data store in different memory address
  * right click inside the panel and select column, cell size and radix to change the output data format
* When connect to multiple devices specify the ST-Link S/N for each device in the debug configuration
* Use `Project Propoerties` -&gt; `C/C++ General` -&gt; `Paths and Symbols`'s `Includes` and `Source Location` tabs to specify the folder path of all the `.h` and `.c` files for build

### STM32CubeMX

* It makes hardware configuration easy with GUI interfaces
* It has been integrated with the IDE
  * Click the `.ioc` file to open this tool
* Project code will be reset and new code will be generated after clicking the save button if configuration are changed here
* Pinout Config Tab
  * In the microcontroller pinout view, select pin to assign function to it
  * There are pins that are enabled if initiating all peripherals option is selected when project starts
    * It will also setup a `UART` connection for console output
  * In the left panel, enable the connectivity that will be used by the project
    * For SPI connection, select a connection mode to enable. Select the Hardware NSS Signal and the MCU will controls the `CS` line automatically. Also change the prescaler in the parameter settings for a desired clock rate
      * Use GPIO output mode for `CS` line when controling it manually
* Clock Config Tab
  * In RCC section of the Pin configuration page, select the Crystal mode can enable the option for on-board HSE
  * Bus speed can be multiple by a factor, this is done by using prescaler.
  * Lastly, change values on the RCC register using code to finalize the changes.
    * code generator is available for these tasks, provided by STM32CubeMX
  * MCO configuration is also configured through RCC register
* Project Manager Tab
  * Allow to change the project settings
* Tools Tab
  * Current calculator
* After completing the setup, click file save to generate and update code for the changed settings
  * Code written outside code `BEGIN - END` comment blocks will be deleted during code generation

