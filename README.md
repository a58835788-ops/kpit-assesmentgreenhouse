# Low-Power Temperature Sampling with LM35 Wake-Up

Repository for project assessment of Honors course for **KPIT Apex Lab** under **Honors EP&ACN** (AISSMS IOIT).

## Overview
- **Student:** Aaron Mobby
- **PRN:** 24310001
- - **Target Board:** STM32 Nucleo-F446RE (`STM32F446RE`)
- **Sensor:** LM35 Analog Temperature Sensor (`10 mV/°C`, connected to `PA1 / ADC1_IN1`)
- **Communication:** `USART2` (`PA2` TX / `PA3` RX) at `115200` baud via ST-LINK VCP
- **Low-Power Strategy:** `STOP` mode (`PWR_LOWPOWERREGULATOR_ON`, `PWR_STOPENTRY_WFI`) with periodic `RTC` wake-up timer (`~30 s` interval using `LSI`, `AsynchPrediv = 127`, `SynchPrediv = 255`, `WUTR = 29`)

## Repository Structure
- `Core/Inc/` — STM32CubeIDE header files (`main.h`, `stm32f4xx_it.h`, `stm32f4xx_hal_conf.h`)
- `Core/Src/` — C source files (`main.c`, `stm32f4xx_it.c`, `stm32f4xx_hal_msp.c`, `system_stm32f4xx.c`)
- `Test_Cases_Photos/` — Hardware setup photos, PuTTY/Tera Term UART logs, and power/timing measurements
- `greenhouse.ioc` — STM32CubeMX hardware & clock configuration (`84 MHz` SYSCLK via HSI+PLL, `ADC1_IN1`, `USART2`, `LSI`)
- `Project_report.pdf` / `Low_Power_Temperature_Sampling_Report.docx` — Final KPIT Apex Lab Agile project report
- `General_Instructions.pdf` — KPIT Apex Lab project guidelines
