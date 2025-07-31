
# Wireless 70% Keyboard: PCB & Firmware Documentation
_Made by: @Programer6 

| | |
|-------------------|-------------------|
| **Project Status** | In Development |
| **Total Time** | 25 Hours |
| **CAD Link** |  |
| **Repository** |https://github.com/Programer6/Custom-75-Keyboard|

---

## July 10, 2024 - Initial Schematic & Matrix Layout (4 hours)
Kicked off the project today by designing the core schematic in KiCad. The main focus was creating the key matrix for a custom 70% layout. I settled on a 6-row by 14-column matrix, which accommodates a function row, number row, three alpha rows, and a bottom modifier row.

Ensured, each switch (`MX1` through `MX74`) is paired with a diode (e.g., `D1`, `D2`). 
<img width="831" height="649" alt="Screenshot 2025-07-31 at 1 38 59 PM" src="https://github.com/user-attachments/assets/c93c260c-2279-4cf1-8fe7-deaa6d924bb3" />

---

## July 11, 2024 - Microcontroller Selection & I/O Expansion (3 hours)
Today was all about selecting the core components and figuring out the GPIO strategy. For a wireless build, the **`nice!nano`** was the obvious choice due to its built-in wireless capabilities and excellent ZMK firmware support.

However, the 20 pins required for the 6x14 matrix would stretch the `nice!nano`'s available GPIOs to the limit, making PCB routing a nightmare. To solve this, I added an **`MCP23017` I/O expander**. 
<img width="835" height="656" alt="Screenshot 2025-07-31 at 1 39 13 PM" src="https://github.com/user-attachments/assets/b6abf613-169b-49b9-abcc-ce828d9cf469" />

---

## July 12, 2024 - cad (5 hours)
After finalizing the PCB, I exported the 3D model from KiCad and imported it into Fusion 360. I designed a simple and functional two-part case: a main body that holds the PCB and a top frame that acts as a switch plate and bezel.
<img width="904" height="706" alt="Screenshot 2025-07-31 at 1 39 34 PM" src="https://github.com/user-attachments/assets/84f765b2-2b55-4909-a5f9-ffdce888337a" />

---

## July 29, 2024 - ZMK Repository Setup (2.5 hours)

I followed the ZMK documentation to create a new `zmk-config` repository. This process involved running a setup script that creates the basic folder structure and configuration files. I named the new board `70keyboard` and set up the initial `build.yaml` file to target the `nice!nano_v2` board.
<img width="311" height="420" alt="Screenshot 2025-07-31 at 1 41 33 PM" src="https://github.com/user-attachments/assets/bb319d75-d097-48e6-b84d-c88ea1c55eb2" />

---

## July 30, 2024 - Writing the Device Tree Overlay (5.5 hours)

I mapped the 14 matrix columns directly to the nice!nano's pins and assigned the 6 rows to the MCP23017 I/O expander, configuring the I2C bus to let them communicate. And of course, I defined the two pins for the rotary encoder to complete the hardware setup.
<img width="828" height="686" alt="Screenshot 2025-07-31 at 1 42 10 PM" src="https://github.com/user-attachments/assets/8a4d5212-a354-4ada-9f09-b13a46bfbc54" />

---

## July 31, 2024 - Creating the Keymap (4 hours)
I built the keymap by laying out all the standard keys, creating an Fn layer for Bluetooth and bootloader shortcuts, and configuring the encoder to control volume with a push-to-mute function.

<img width="875" height="506" alt="Screenshot 2025-07-31 at 1 42 01 PM" src="https://github.com/user-attachments/assets/66469c58-bf05-4a7b-8d0f-7edece2a3ef9" />
