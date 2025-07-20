This page describes the installation and flashing process using the Arduino IDE.

## Prerequisites

1. Install Arduino IDE. Follow the [instructions from the official page](https://www.arduino.cc/en/Guide/).
2. After installing, launch the IDE and open the [tipsy.ino](tipsy/tipsy.ino)
3. Add an additional board manager URL. Go to `File -> Preferences` and paste the following url into the `Additional board manager URLs` field: `https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json`. Click "OK".
   ![Adding an additional board manager URLs](assets/board_manager_url.png)
4. Open the "Board Manager" and install `Raspberry Pi Pico/RP2040/RP2350` board:
![Board Manager steps](assets/board_manager.png)
![Install Raspberry Pi Pico board](assets/rpi_pico_install.png)
5. Select the `Raspberry Pi Pico` Board from the board manager menu. Go to `Tools -> Board -> Raspberry Pi Pico/RP2040/RP2350 -> Raspberry Pi Pico`
![Selecting the Raspberry Pi Pico board](assets/board_selection.png)
6. Install a few libraries. Go to `Sketch -> Include Library -> Manage Libraries`. Click "Install All" when prompted.

* Adafruit GFX Library 
* Adafruit ST7735 and ST7789
* 

![Manage Libraries Menu](assets/manage_libraries_menu.png)

**BEFORE FLASHING, Select Board Partition**

## Partitioning

Connect the board using the USB-C connector. Select the board in `Tools -> Port -> UF2_Board` (after flashing this might change).
![Port Selection](assets/port_selection.png)

**Note: after initial flashing, the port name will change  to something like `/dev/ttyACM0` (the number may be different)**

![Changed Port Name](assets/changed_port_name.png)

Partition the board by going to `Tools -> Flash Size -> 2MB (Sketch: 1MB, FS: 1MB)`
![Partitioning](assets/partitioning.png)

## Compile and flash

To compile and flash make sure the board and the port are selected.

Open `tipsy.ino` and click "Upload" button in Arduino IDE:
![Compile and Flash](assets/compile_and_flash.png)

## Copy device asset files

After the device is flashed it will automatically mount as a mass storage device. Initially it will only
contain `settings.bin` file. For correct device operation you need to upload the `tipsy/data` files to the mass storage device.

Copy the files in `tipsy/data` to the mass storage device so you end up with a structure like this:
```
# device tree on the removable volume
mass storage device
├── settings.bin
├── qrcode.tga
├── slash.tga
├── TipsyManual.url
├── blingpic
|   ├── airplane.tga
|   ├── assange.tga
|   ├── {more files...}
```