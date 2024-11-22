# TAS5822 ESP32 A2DP Example
This example is intended for the ESP32.

This is an example of a basic Bluetooth A2DP audio receiver, streaming audio to the TAS5822 I2S amplifier.

The ESP32-A2DP library (https://github.com/pschatzmann/ESP32-A2DP) is used to configure audio streaming.

## Required Hardware
* ESP32 Board (original, not ESP32-S2/S3 etc., as we need Bluetooth audio support)
* TAS5822M Breakout Board
* 12V Power Supply
* 2x 4/6/8 Ohm Speakers

## Software Setup
This folder is a PlatformIO firmware project. Open this folder using PlatformIO, and check that you can compile successfully.

Upload the compiled firmware to the ESP32 board.

## Hardware Setup
These instructions are written to suit an ESP32 DevKitC V4, with pinout as shown below. Different boards may have different pinouts that require some adjustment. Some pin mappings may be adjusted in the firmware if desired.

Reference ESP32 pinout:
![Pinout Drawing](../../Images/ESP32-DEV-KIT-DevKitC-v4-pinout-mischianti.png "ESP32 Pinout")

Reference TAS5822 pinout:
![Pinout Drawing](../../Images/TAS5822PinoutDrawing1.png "Pinout Drawing")

Connect the ESP32 and TAS5822 boards as follows:

* ESP32 5V -> TAS5822 5V
* ESP32 GND -> TAS5822 GND
* ESP32 I2C SDA (IO21) -> TAS5822 I2C_SDA
* ESP32 I2C SCL (IO22) -> TAS5822 I2C_SCL
* ESP32 I2S Word Select (IO33) -> TAS5822 I2S_WS
* ESP32 I2S Bit Clock (IO27) -> TAS5822 I2S_BCLK
* ESP32 I2S Data Out (IO32) -> TAS5822 I2S_DIN
* ESP32 (IO13) -> TAS5822 PDN

Connect the speakers to the two speaker terminals on the TAS5822 board.

Connect the TAS5822 to 12V power, either via the screw terminal or the pin header. If you are first testing the board, it is recommended to use an adjustable current-limited power supply in case of wiring mistakes. 

## Recommended Steps

Make all connections as described above.

Supply 5V power to the ESP32 board (via USB or otherwise). Check that the TAS5822 3V3 LED is lit, indicating that the 5V power from the ESP32 is received and regulated down to 3.3V as required.

Enable the 12V power supply to the TAS5822 board. Check that the TAS5822 PWR LED is lit, indicating the 12V power is being received.

Compile and upload the firmware to the ESP32 board.

Once the firmware is running, the ESP32 will present as a Bluetooth audio device. Connect to it from a suitable device (phone, laptop, etc.). Play audio and check that the speakers work as expected.