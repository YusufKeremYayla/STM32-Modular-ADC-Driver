# STM32 Modular ADC Driver with DMA & Moving Average Filter

This project demonstrates a bare-metal embedded software implementation on STM32F4. It features a custom modular driver architecture to read analog signals via ADC using DMA, process the data with a smoothing filter, and control LEDs based on voltage thresholds.

## 🚀 Key Features (Öne Çıkan Özellikler)
* **DMA Integration:** ADC conversions are handled via Direct Memory Access (DMA) to offload the CPU.
* **Modular Driver Architecture:** The code is structured into separate layers (`adc_drive`, `io_driver`) instead of a monolithic `main.c`, following clean code principles.
* **Signal Processing:** Implements a **64-sample Moving Average Filter** to stabilize potentiometer readings and eliminate noise.
* **Linear Mapping:** Converts raw voltage data into percentage (0-100%) for precise logic control.

## 📂 Project Structure (Dosya Yapısı)
* `Core/Src/adc_drive.c`: Custom ADC driver logic (Initialization, DMA callback handling, Filtering).
* `Core/Src/io_driver.c`: GPIO control logic (LEDs, Button Debouncing).
* `Core/Src/main.c`: Application layer logic.

## 🛠 Hardware & Tools
* **Microcontroller:** STM32F4 Discovery Kit (STM32F407VG)
* **IDE:** STM32CubeIDE
* **Peripherals used:** ADC1 (DMA Mode), GPIO, SysTick
* **Components:** 10k Potentiometer, 4 LEDs (Green, Orange, Red, Blue)

## 📊 How It Works
1.  The ADC reads the potentiometer value continuously using DMA in a circular buffer.
2.  The `adc_drive` module calculates the average of 64 samples to filter out noise.
3.  The voltage is mapped to a 0-100% scale.
4.  LEDs light up based on the percentage:
    * **0-25%:** Green ON
    * **25-50%:** Green + Orange ON
    * **50-75%:** Green + Orange + Red ON
    * **75-100%:** All LEDs ON

---
*Developed by Yusuf Kerem Yayla*

