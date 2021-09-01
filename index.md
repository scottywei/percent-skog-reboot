# <center><font size="32">Skog Reboot PCB Guide</font> <br> <font size="5">Percent Studio x Basic I/O Instruments</font></center>

## Introduction
Welcome to the Skog Reboot, this is an 87% customize keyboard designed by Percent Studio and powered by Basic I/O Instruments. This document is for the prototype version of the board and will be changed and updated along with the development progress.

## Features
 - USB and BLE(Bluetooth Low Energy, version 4.2) duo-mode.
 - QMK firmware, enabled with VIA.
 - Per-key RGB backlight.
 - RGB strip light and RGB logo light.
 - VIA Programmable Encoder.
 - Use BL-5C/BL-5J battery, Hundreds hours of battery life.
 - Separated BLE module daughterboard, improved signal reception.

## Hardware
A Complete Skog Reboot PCB set contains 1 Mainboard, 1 Encoder daughterboard, 1 BLE module daughterboard, and 1 Battery Module board. the BLE module and the Battery module duaghterboards are optional, in case you're not going to use the BLE feature of this board.

### Mainboard
- **Power Switch** is the main switch which controls the power from the battery, this switch is located beside the <kbd>SPACE</kbd> key switch and indicated with labeled with "ON" and "OFF". 
>**NOTICE:** The battery still can be charged even if the power switch is OFF.

- **Reset Button**, indicated with "RESET", press to bring the board into DFU mode.

- **Battery Connector**, This is a 2 pin JST SH connector, connected to the battery module with a 2 pin cable. This board has battery connection safety, if your battery connection is in the wrong polarity, it will prevent burning up the components on the board. But we still highly recommend that you should carefully connect your battery, Might the polarity!

- **Encoder Connector**, This is a 5 pin JST SH connector beside the Battery Connector, you will connect the Encoder daughterboard with a 5pin cable here.

- **BLE Module Connector**, This is a 10 pin Board-to-Board connector, indicated with a rounded-corner rectangular. When you connect the BLE Module Daughterboard here, please align the edge of the daughterboard to the rectangular mark.

- **RGB Backlights**, There are 92 RGB backlights in total on the board, each key switch has its own RGB backlight, these RGB lights are controlled by 2 IS31FL3737 controllers. You can control the RGB lights by QMK RGB keycodes.
- **RGB Strip and LOGO lights**, These are 10 WS2812 RGB lights, 5 to the Strip light above the arrow keys, and another 5 are under the LOGO on the bottom. the RGB strip and LOGO lights can be controlled in the "LIGHTING" panel in the VIA.

Additionally, there are some basic control keys for RGB backlights and the RGB strip:

|         | Toggle | Mode+ | Mode- | Hue |
  | ------: | :-------: | :-------: | :-------: | :------: |
  | RGB Backlights |    <kbd>F13</kbd>    |    <kbd>F14</kbd>    |    <kbd>F15</kbd>    |   <kbd>F16</kbd>    |
  | RGB Strip |    <kbd>F17</kbd>    |    <kbd>F18</kbd>    |    <kbd>F19</kbd>    |   <kbd>F20</kbd>    |

### BLE Module Daugtherboard
Optional module to enable BLE feature for this board, connect to the mainboard via the BLE Module Connector.

### Encoder Daughterboard
Loaded with an EC11 rotary encoder, connect to the mainboard via a 5 pin SH cable. The function of the rotary encoder can be programmed in the VIA.

### Battery Module Daughterboard
There 2 types of battery modules specifically designed for BL-5C or BL-5J 3.7v Li-ion battery, these batteries were designed for Nokia phones and still easy to get nowadays. The BL-5C and BL-5J is different in dimension and capacity. For a BL-5C, the typical capacity is 1150maAh, which means approximately 500 hours of standby battery life(All RGB lights OFF), and for a BL-5J the capacity is larger to 1320mAh. This module is connect to the mainboard via a 2 pin SH cable.

## Firmware
To be done.

## Usage
### USB Mode
The board will preferentially run in USB mode when it is connected to a USB host device via USB cable. 

### Bluetooth Mode
Once the board is powered, either by USB or battery, it will start broadcasting a device named "SKOG REBOOT BLE". To pair the board to your device, you just need to search for "SKOG REBOOT BLE" then pair it in the Bluetooth settings of your device. To unpair the board, just remove it from the paired devices(New unpair method is under development).

### Mode Switching
You can toggle the keyboard bwteen USB mode and Bluetooth mode by using command key: <kbd>LShift</kbd>+<kbd>RShift</kbd>+<kbd>B</kbd> 

### Bootloader(DFU) Mode
Once you want to upgrade the firmware or reset the EEPROM of the board, you will need to bring the board into bootloader or DFU mode first, and you will do it like this:

- Method 1:  
Simpliy Press the "RESET" button on the mainboard.

- Method 2:
1. Turn "OFF" the power switch;
2. Pull out the USB cable (if it is attached);
3. Keep pressing the <kbd>ESC</kbd> and plug the USB cable back in agian, hold the <kbd>ESC</kbd> pressed for at least 2 seconds.

When the board is in DFU mode, you can see the yellow text "Device Connected" on the QMK Toolbox Console. 

Since this is a duo-mode board, the board might keep powered by the battery even the USB cable is pulled out. This will cause the board stay in DFU mode and it's unable to use as a keyboard until you exit. If you want to exit the DFU mode, you may follow these steps:

1. Turn the Power Switch "OFF".
2. Pull out the USB cable.
3. Turn "ON" the Power Switch or plug the USB cable back in.

Then the board will exit DFU mode when the power is completely cut off and back to normal when it's powered again.

### Lock Mode
In this mode, the board will ignore any key pressing, like it has been locked. This mode is very useful in some cases, like when you're trying to clean the keyboard and you don't want the keypress to mess up your works.   
To enable Lock Mode, you just need to press <kbd>LShift</kbd>+<kbd>RShift</kbd>+<kbd>L</kbd> at the same time, do it again the board will quit Lock Mode.

### VIA
The VIA is a GUI keystroke configurator for QMK keyboards, Please refer to <https://www.youtube.com/watch?v=WZKf2TvUZ7Q> for detail usage.


### BLE Module Factory Reset
Before performing BLE module reset, you will unpair the keyboard from your Bluetooth host, then keep in the Bluetooth devices searching interface, then press <kbd>LShift</kbd>+<kbd>RShift</kbd>+<kbd>R</kbd>, the device "PERCENT SKOG REBOOT BLE" will disappear for a few seconds then appear agian, check if the name of the device is exactly "PERCENT SKOG REBOOT BLE". If not, press the keys agian until the module is reset with a right name.

### Encoder
The Skog Reboot comes with a rotary encoder, which can bring interesting usage for you. There are 3 operations for this encoder: Clockwise Rotation, Counter-Clockwise Rotation, and Press. All these operations are programmable in the VIA. To the right of the VIA keymap of Skog Reboot, there are 3 keys, One in normal size and two in a smaller size. The normal one stands for the Press of the encoder, the upper smaller key stands for the Clockwise Rotation and the lower one stands for Counter-Clockwise Rotation. You can programm all these 3 operations with any keycodes, it's time to use your imagination now. Here are some examples might that inspire you:

**Cursor Locator:** Program the clockwise and counter-clockwise to Left and Right in layer 0, to Up and Down in layer 1, then program the Press to MO(1) which can momentarily turn layer 1 on. Then you got a cursor locator that can fast locate the cursor by rotating, move the cursor to left or right by rotating clockwise or counter-clockwise, move the cursor up or down by keep pressing while rotating. This could be very useful when you're coding or using spreadsheets.

### All Command Keys:
  | Command | Function  |
  | ------ | ------ |
  | <kbd>LShift</kbd>+<kbd>RShift</kbd>+<kbd>G</kbd> | Turn all RGB on                                              |
  | <kbd>LShift</kbd>+<kbd>RShift</kbd>+<kbd>H</kbd> | Turn all RGB off                                              |
  | <kbd>LShift</kbd>+<kbd>RShift</kbd>+<kbd>V</kbd> | Update the battery level in Windows 10's Bluetooth devices interface, this is not an accurate value  |
  | <kbd>LSfhit</kbd>+<kbd>RShift</kbd>+<kbd>R</kbd> | Performing a BLE mode factory reset |
  | <kbd>LShift</kbd>+<kbd>RShift</kbd>+<kbd>L</kbd> | Turn the keyboard into lock mode. |


### Change Logs
Date: 2021-08-2
- RGB strip will turn on as capslock indicator and layer indictor, even the RGB strip is off.
- All the RGB lights will turn off after the keyboard idle for around 60 seconds.
- The keyboard now can be powered and charge by a USB adapter or power bank.
- Better Encoder perform.
