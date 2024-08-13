# **Powkiddy X28 Analog Stick Cardinal Snapping Fix**

This guide is for users experiencing cardinal snapping issues with the analog sticks on the Powkiddy X28. The steps below will guide you through the process of unlocking the bootloader (a one-time procedure that will wipe the device) and flashing a custom boot image to address the snapping issue. Note that this fix is still a work in progress (WIP), and some trial and error may be required.

---

## **Prerequisites**

Before you begin, you'll need to install the following drivers and tools on your Windows PC:

### 1. **Install Universal ADB Driver**
   - Download and install the Universal ADB Driver from [this link](https://github.com/K3V1991/ADB-and-FastbootPlusPlus).
   - During installation, make sure to check the box labeled "Add to System Path Environment."
   - Reboot your computer after installation.

### 2. **Install Unisoc Drivers**
   - Download the Unisoc Drivers from [this link](https://github.com/TheGammaSqueeze/GammaOS/releases/download/GammaOS_v1_RG405M/UnisocDrivers.zip).
   - Extract the downloaded ZIP file.
   - Run the `DPInst64.exe` program from the relevant OS folder (Windows 10 drivers will also work on Windows 11).

---

## **Bootloader Unlocking (One-Time Setup)**

*Note: This step will wipe your device.*

### 1. **Enable USB Debugging on the Powkiddy X28**
   - Follow the instructions [here](https://developer.android.com/studio/debug/dev-options) to enable USB debugging on your device.

### 2. **Connect X28 to Your PC**
   - Connect your Powkiddy X28 to your PC or Mac using a USB cable while the device is booted into Android.

### 3. **Reboot to Bootloader**
   - Open a command prompt window on your PC.
   - Issue the following command to reboot the device into the bootloader:
     ```bash
     adb reboot bootloader
     ```
   - Your Powkiddy X28 will reboot, and you should see "fastboot mode" displayed next to the Powkiddy logo.

### 4. **Unlock Bootloader**
   - Open Google Chrome (Firefox is not supported) and navigate to [this site](https://thegammasqueeze.github.io/subut-rehost/).
   - Click **Connect**.
   - Click **fastboot gadget** and establish the connection.
   - Click **Unlock**.
   - Press the volume down button on your Powkiddy X28 to confirm the unlock.
   - Wait for the process to complete. Your X28 will display the message "Unlock bootloader success!"

### 5. **Close the Google Chrome Window**
   - Ensure that you close the Google Chrome window before proceeding to the next steps, as the next commands will not work if the window remains open.

### 6. **Reboot into Fastbootd Mode**
   - In your command prompt window, issue the following command:
     ```bash
     fastboot reboot fastboot
     ```
   - Your Powkiddy X28 will now boot into **fastbootd mode**. Confirm that "fastbootd" is displayed on your X28 before proceeding.

---

## **Flashing the Analog Stick Fix**

### 1. **Flash the Boot Image Fix**
   - Open a command prompt window in the directory where the `boot.img.fix` file is located.
   - Flash the fix by issuing the following command:
     ```bash
     fastboot flash boot boot.img.fix
     ```
   - Once the process is confirmed as complete, press the power button on your X28 to reboot the device.

---

## **Alternative Calibration for Sticks**

If your analog sticks do not reach the full outer edges or have issues with circular inputs, you can try flashing alternative boot images for better calibration.

### 1. **Reboot to Fastbootd Mode**
   - Before flashing the alternative calibration files, ensure your Powkiddy X28 is in Fastbootd mode.
   - If you’re not already in Fastbootd mode, enabled USB debugging and issue the following command:
     ```bash
     adb reboot fastboot
     ```

### 2. **Flash the Alternative Calibration Boot Images**

   - **Alternative Calibration 1:**
     - Open a command prompt window in the directory where the `boot.img.alternative` file is located.
     - Flash the alternative calibration by issuing the following command:
       ```bash
       fastboot flash boot boot.img.alternative
       ```
     - Press the power button on your X28 to reboot the device.

   - **Alternative Calibration 2:**
     - If the first alternative calibration doesn't yield the desired results, you can try a second alternative calibration.
     - Open a command prompt window in the directory where the `boot.img.alternative2` file is located.
     - Flash the alternative calibration by issuing the following command:
       ```bash
       fastboot flash boot boot.img.alternative2
       ```
     - Press the power button on your X28 to reboot the device.

---

## **Undoing the Fix**

### 1. **Enable USB Debugging**
   - Enable USB debugging on your Powkiddy X28 as described in the prerequisites.

### 2. **Reboot to Fastbootd Mode**
   - Reboot the device into fastbootd mode by issuing the following command:
     ```bash
     adb reboot fastboot
     ```

### 3. **Flash the Stock Boot Image**
   - Open a command prompt window in the directory where the `boot.img.stock` file is located.
   - Flash the stock boot image by issuing the following command:
     ```bash
     fastboot flash boot boot.img.stock
     ```
   - Press the power button on your X28 to reboot the device.

---

This guide should help you address the cardinal snapping issue with the analog sticks on your Powkiddy X28. If the initial fix doesn't fully resolve your issue, the alternative calibrations may provide better results. Since this is still a work in progress, your feedback is appreciated.
