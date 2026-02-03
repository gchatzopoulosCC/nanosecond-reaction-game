# Nanosecond Reaction Game

A Nanosecond Reaction Game built on an STM32F401RE using an LED and a Push Button (DFR0029). It utilises the NVIC, DWT, and ITM registers of the Internal Private Peripheral Bus (PPB) to detect triggers (push button), count clock cycles (timer), and report the result via the Serial Wire Output (SWO), respectively.

## CubeMX Configuration

It is assumed that the Push Button and the LED are connected to the PA_0 and PA_1 pins, respectively. The following outlines the CubeMX steps for configuring the project.

### Pinout & Configuration

1.  Pinout
    - PA_0:
       * -> **GPIO_EXTI0**
    - PA_1:
       * -> **GPIO_Output**
2. System Core -> **SYS**
    - Debug -> **Trace Asynchronous Sw**
3. System Core -> GPIO
   - PA_1:
      * -> GPIO Mode: **External Interrupt Mode with Falling edge trigger detection**
      * -> Pull-up/Pull-down: **Pull-up**
4. System Core -> NVIC
   - EXTI line0 interrupts

### Clock Configuration

1. HLCK -> 84 MHz

## Display

To observe the project's functionality, several steps are required. The project is only visible in _DEBUG_ mode, and the Debugger's Core Clock **MUST** be the same as your HCLK (84 MHz). Furthermore, the ITM reports to the **SMV ITM Data Console** that you have to _manually_ open from the Window tab. It is important to note that the SMV ITM Data Console _must_ be configured to run on a Port (Configure Trace -> Port 0) and start recording (the red button next to Configure Trace).

## User Code

The user code will be found in the _Src/main.c_ between all the appropriate comment blocks.
