# Open Smart Plug

This is a software for a smart plug to replace something like Tuya. It was specifically make for "Soundlogic Smart Plug". On other models, you might need to change the pin numbers.

## Usage

> **Warning:** It was developed for the chip `cb2s` ([CB2S](https://docs.libretiny.eu/boards/cb2s/)) and the model Soundlogic Smart Plug and might not work with other smart plugs.

### Flashing

For the hardware side of flashing, see [LibreTiny](https://docs.libretiny.eu/docs/platform/beken-72xx/#flashing) (Use an USB to UART adapter, solder the RX/TX pins of it to your chip).  
To build and flash, install [PlatformIO](https://platformio.org/) and [ltchiptool](https://github.com/libretiny-eu/ltchiptool). Run the following commands from the project root while the chip is connected:  
Backup the old firmware (replace BK7231N with your chips family, see [here](https://docs.libretiny.eu/docs/status/supported/#board-list)):
```
ltchiptool flash read -d /dev/ttyACM0 BK7231N backup.bin
```
Build and flash the new:
```
pio run
ltchiptool flash write -d /dev/ttyACM0 .pio/build/cb2s/firmware.bin
```
On windows, you need to replace `/dev/ttyACM0` with something like `COM3` and update the "/" to "\\" (Just ask ChatGPT for the windows version of the commands).

### Using

The plug will create a network called `SmartPlug-XXXX`. The default password is `password`. If you enter the network and go to its configuration page, you can control the state and change the WiFi name and password. If you press the button on the plug, you can also toggle it. If you hold it for 8 seconds, it will reset itself (WiFi name and password).



