# STM32 I2C Scanner using UART Debugging (STM32F401CCU6)

This project scans all possible I2C addresses using STM32F401CCU6 and logs the detected addresses over UART (USART2). It toggles the onboard LED (PC13) to indicate activity.

## 🛠 Board and Peripherals

- **MCU**: STM32F401CCU6 (Blackpill)
- **I2C**: `hi2c1` (default I2C interface)
- **UART**: `huart2` (used for debugging/logging)
- **LED**: `GPIOC, PIN13` (onboard LED)

## 🔍 Features

- Scans for all active I2C slave devices (0x03 to 0x77).
- Logs found I2C addresses to UART terminal (PuTTY).
- LED blinks for each scan attempt.

## 📦 Requirements

- STM32CubeIDE (for building/flashing/debugging)
- ST-LINK Programmer **or**
- STM32CubeProgrammer (for command-line or GUI flashing)
- USB to TTL module (to view UART logs in PuTTY)

## 🧪 How to Use

### 🔧 1. Flash the Program

You can use any of the following methods:

#### ✅ Option 1: Using STM32CubeIDE
- Open the project in STM32CubeIDE.
- Connect ST-LINK.
- Build and flash directly using the IDE.

#### ✅ Option 2: Using STM32CubeProgrammer CLI

Example command:
```bash
"C:\Program Files\STMicroelectronics\STM32Cube\STM32CubeProgrammer\bin\STM32_Programmer_CLI.exe" -c port=USB1 -w "C:\STM32CubeIDE\workspace_1.17.0\I2C_SCAN\I2CSCAN\Debug\I2CSCAN.bin" 0x08000000 -v -rst
Replace the .bin file path with your actual binary location.

💻 2. View UART Output
Connect a USB-to-TTL module to USART2 pins:

TX (STM32) -> RX (USB-TTL)

RX (STM32) -> TX (USB-TTL)

Open PuTTY (or any serial terminal):

Baud Rate: 115200

Data Bits: 8

Parity: None

Stop Bits: 1

💡 LED Behavior
PC13 LED blinks on each I2C scan iteration.

📝 Output Example
mathematica
Copy
Edit
Scanning I2C addresses...
Device found at 0x3C
Device found at 0x48
Scan complete.
