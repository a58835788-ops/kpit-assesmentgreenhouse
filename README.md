# Low-Power Temperature Sampling with LM35 Wake-Up

Repository for the **KPIT Apex Lab** project assessment under **Honors EP&ACN**.

## Student & Course Details

| Field | Details |
| :--- | :--- |
| **Student** | Aaron Mobby |
| **PRN** | 24310001 |
| **College** | AISSMS IOIT |
| **Program** | Honors EP&ACN — KPIT Apex Lab Assessment |

## System Overview

- **Target Board:** STM32 Nucleo-F446RE (`STM32F446RE`)
- **Sensor:** LM35 Analog Temperature Sensor (`10 mV/°C`)
- **Communication:** `USART2` at `115200` baud via ST-LINK VCP
- **Low-Power Strategy:** `STOP` mode (`PWR_LOWPOWERREGULATOR_ON`, `PWR_STOPENTRY_WFI`) with periodic `RTC` wake-up timer (`~30 s` interval using `LSI`, `AsynchPrediv = 127`, `SynchPrediv = 255`, `WUTR = 29`)

## Hardware Pinout

| STM32F446RE Pin | Peripheral / Function | Connected Component / Interface | Notes |
| :--- | :--- | :--- | :--- |
| `PA1` | `ADC1_IN1` | LM35 (`Vout`) | Analog temperature input (`10 mV/°C`) |
| `PA2` | `USART2_TX` | ST-LINK VCP | Serial TX at `115200` baud |
| `PA3` | `USART2_RX` | ST-LINK VCP | Serial RX at `115200` baud |

## Repository Structure

```text
kpit-assesmentgreenhouse/
├── Test_Cases_Photos/
│   ├── Hardware_Setup.jpg                      # Hardware setup photo
│   └── UART_Serial_Log.png                     # UART serial log output
├── General_Instructions.pdf                    # KPIT Apex Lab project guidelines
├── Low_Power_Temperature_Sampling_Report.docx  # Final project report (DOCX)
├── Project_report.pdf                          # Final project report (PDF)
└── README.md                                   # Project documentation
```

## Overview
- **Student:** Aaron Mobby
- **PRN:** 24310001
- **Target Board:** STM32 Nucleo-F446RE (`STM32F446RE`)
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
