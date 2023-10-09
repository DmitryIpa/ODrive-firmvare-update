## ODrive-firmvare-update
Flashing with an STLink. This procedure is only necessary for ODrive v3.4 or earlier. You will need an STLink/v2 or compatible programmer for STM.
# 1. Install OpenOCD
  Linux: ``` sudo apt-get install openocd ```
  macOS: ``` brew install openocd ```

# 2. Download the latest firmware release form here[https://github.com/odriverobotics/ODrive/releases]. You will need the .elf file. Make sure you select the file that matches your board version.

# 3. Select DFU Mode on ODrive:

# 4. Wire up the ODrive and STLink/v2 programmer as shown in this picture and power up the ODrive.
![Image alt](https://github.com/DmitryIpa/Odrive_control/blob/main/odrive.png)

# 5. Run the following command (replace ```ODriveFirmware_v3.4-24V.elf``` with the name of your firmware file):
```
openocd -f interface/stlink-v2.cfg -f target/stm32f4x.cfg -c init -c "reset halt" -c "flash write_image erase ODriveFirmware_v3.4-24V.elf" -c "reset run" -c exit
```
If everything worked correctly, you should see something similar to this towards the end of the printout:
```
wrote 262144 bytes from file ODriveFirmware_v3.4-24V.elf in 10.194110s (25.113 KiB/s)
```
# Congratulations! ODrive updated firmware
