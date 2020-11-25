# <center><font size="32">Skog Reboot PCB Guide</font> <br> <font size="5">Percent Studio x Basic I/O Instruments</font></center>

## Introduction
Welcome to the Skog Reboot, this is an 87% customize keyboard designed by Percent Studio and powered by Basic I/O Instruments. This document is for the prototype version of the board and will be changed and updated along with the development progress.

## Features
 - USB and BLE(Bluetooth Low Energy, version 4.2) duo-mode.
 - QMK firmware, enabled with VIA.
 - Per-key RGB backlight.
 - RGB strip light and RGB logo light.
 - VIA Programmable Encoder.
 - Use BL-5C/BL-5J battery, Hundreds of hours battery life.
 - Separated BLE module daughterboard, improved signal reception.

## Hardware
A Complete Skog Reboot PCB set contains 1 Mainboard, 1 Encoder daughterboard, 1 BLE module daughterboard, and 1 Battery Module board. the BLE module and the Battery module duaghterboards are optional, in case you're not going to use the BLE feature of this board.

### Mainboard
- **Power Switch** is the main switch which controls the power from the battery, this switch is located beside the <kbd>Spacebar</kbd> key switch and indicated with labeled with "ON" and "OFF". 
>**NOTICE:** The battery still can be charged even if the power switch is OFF.

- **RGB Switch** is the switch that selects the power source for the RGB lights, including backlights, strip lights and logo lights. it's located beside the Power Switch, indicated with "BAT" and "USB". When the switch is in the "BAT" position, the power source of the RGB lights will comes from the battery. In contrast, the power will come from the USB when it's in the "USB" position.
>**NOTICE:** When this switch is in "**BAT**" position and the USB cable is plugged in, the power then will comes from the USB.

- **Reset Button**, press to bring the board into DFU mode.

- **Battery Connector**, This is a 2 pin JST SH connector, connected to the battery module with a 2 pin cable. This board has battery connection safety, if your battery connection is in the wrong polarity, it will prevent burning up the components on the board. But we still highly recommend that you should carefully connect your battery, Might the polarity!

- **Encoder Connector**, This is a 5 pin JST SH connector beside the Battery Connector, you will connect the Encoder daughterboard with a 5pin cable here.

- **BLE Module Connector**, This is a 10 pin Board-to-Board connector, indicated with a rounded-corner rectangular. When you connect the BLE Module Daughterboard here, please align the edge of the daughterboard to the rectangular mark.

- **RGB Backlights**, There are in total 92 RGB backlights on the board, each key switch has its own RGB backlight, these RGB lights are controlled by 2 IS31FL3737 controllers. You can control the RGB lights by QMK RGB keycodes.
- **RGB Strip and LOGO lights**, These are 10 WS2812 RGB lights, 5 to the Strip light above the arrow keys, and another 5 are under the LOGO on the bottom. They're controlled by key <kbd>F16</kbd>-<kbd>F20</kbd> (This feature is still under development while the writing of this documents).

### BLE Module Daugtherboard
To be done
### Encoder Daughterboard
To be done

### Battery Module Daughterboard
To be done

## Firmware
To be done.

## Usage
### USB Mode
The board will preferentially run in USB mode when it is connected to a USB host device via USB cable. Mode switching is under development.

### Bluetooth Mode
Once the board is powered, either by USB or battery, it will start broadcasting a device named "SKOG REBOOT BLE". To pair the board to your device, you just need to search for "SKOG REBOOT BLE" then pair it in the Bluetooth settings of your device. To unpair the board, just remove it from the paired devices(New unpair method is under development).

The Bluetooth interface of this board only working when your board is paired and no USB cable is connected, once the USB cable is connected, it will preferentially use the USB interface. As mentioned above, mode switching is coming soon.

### Bootloader(DFU) Mode
Once you want to upgrade the firmware or reset the EEPROM of the board, you will need to bring the board into bootloader or DFU mode first, and you will do it like this:

- Method 1:  
Simpliy Press the "Reset Button" on the mainboard.

- Method 2:
1. Turn off the power switch (all the power switches);
2. Pull out the USB cable (if it is attached);
3. Keep pressing the <kbd>ESC</kbd> and plug the USB cable back in agian.

When the board is in DFU mode, you can see the yellow text "Device Connected" on the QMK Toolbox Console.
Since this is a duo-mode board, so the board might be keep powered by the battery when the USB cable is pulled out. this will keep the board in DFU mode and it's unable to use as a keyboard. So if you want to exit the DFU mode, you may follow these steps:

1. Turn the Power Switch "OFF".
2. Pull out the USB cable.
3. Turn "ON" the Power Switch or plug the USB cable back in.

Then the board will exit DFU mode when the power is completely cut off and back to normal when it's powered again.

### Lock Mode
In this mode, the board will ignore any key pressing, like it has been locked. this mode is very useful when you're difficult to access the power switch and you want to put the board into your backpack. To enable Lock Mode, you just need to press <kbd>LShift</kbd>+<kbd>RShift</kbd>+<kbd>L</kbd> at the same time, do it again the board will quit Lock Mode.

### VIA
Please refer to <https://www.youtube.com/watch?v=WZKf2TvUZ7Q>

### Factory Reset
To be done