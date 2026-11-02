# Starbie

A small star-shaped desk pet. A tiny OLED screen shows a character that wanders around, and it reacts when you tilt the board, shake it, or press its two buttons. I designed the whole PCB myself in KiCad, following the Hack Club Starbie Week 1 guide.


![Starbie PCB, 3D view](pcb-3d.png)

![Starbie PCB, 3D view from another angle](pcb-3d-2.png)


## What it does

- **Button 1** opens a radial menu with four actions: NAP, PLAY, FEED and PET.
- **Tilting** the board moves a selector ball around the menu. The MPU6050 motion sensor reads the tilt.
- **Button 1 again** picks the highlighted action, and the pet reacts with a nap, hearts or a jump.
- **Button 2** shows or hides a stats screen with joy, energy and fullness, plus the room temperature and humidity from the DHT11.
- **Shaking** the board makes the pet wiggle.

## Hardware

| Part | Job |
| --- | --- |
| XIAO ESP32-C3 | the microcontroller (the brain) |
| 0.96 inch 128x64 I2C OLED | the screen |
| MPU6050 module | motion sensor for tilt and shake |
| DHT11 | temperature and humidity sensor |
| 2 x Cherry MX style switches | the two buttons |
| 10k resistor | pull-up on the DHT11 data line |

## How it is wired

| Part | XIAO pin |
| --- | --- |
| OLED and MPU6050 SDA | D4 |
| OLED and MPU6050 SCL | D5 |
| DHT11 data | D1 |
| Button 1 | D2 |
| Button 2 | D3 |

The OLED and the MPU6050 share the same two I2C wires. Everything runs on 3.3V, and the buttons connect their pin to GND when pressed.

![Schematic](schematic.png)

## PCB design

- Custom star-shaped board outline on the Edge.Cuts layer
- Signal wires routed on the copper layers
- GND copper pour on the front layer, so all the ground pins connect together
- The design rules check (DRC) shows only 2 courtyard errors, which come from the supplied OLED footprint and do not affect the board

![PCB layout](pcb-editor.png)

### Bill of Materials (BOM)

| Part | Description | Qty | Unit Price | Total Price | Vendor | Link |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **XIAO ESP32-C3** | Microcontroller | 1 | $3.24 | $3.24 | Daraz | [Buy on Daraz](https://www.daraz.pk/products/i1966086027.html) |
| **GY-521 MPU-6050** | 6-Axis Gyro / Accelerometer | 1 | $1.98 | $1.98 | Daraz | [Buy on Daraz](https://www.daraz.pk/products/i254765267.html) |
| **0.96 inch OLED Display** | I2C Display Module (128x64) | 1 | $2.52 | $2.52 | Daraz | [Buy on Daraz](https://www.daraz.pk/products/i1966086027.html) |
| **Cherry MX Switches** | Key Switches | 1 | $3.19 | $3.19 | AliExpress | [Buy on AliExpress](https://www.aliexpress.us/item/3256810219228347.html) |
| **DHT11 Sensor** | Temperature & Humidity Sensor | 1 | $1.49 | $1.49 | Daraz | [Buy on Daraz](https://www.daraz.pk/products/i254765267.html) |
| **10K Resistors (1/4W)** | Pull-up Resistors | 1 | $0.42 | $0.42 | Daraz | [Buy on Daraz](https://www.daraz.pk/products/i465392816.html) |
| **Custom PCB (Starbie)** | Fabricated Circuit Board | 1 | $10.00 | $10.00 | JLCPCB | [JLCPCB Website](https://www.jlcpcb.com/) |
| **Tax & Shipping** | Shipping / Fees for whole order | 1 | $7.00 | $7.00 | — | — |
| **Total** | | | | **$29.84** | | *(Using $29.84 of $30.00 Tier 1 Funding)* |

## Files

- `MyProject.kicad_sch`: schematic
- `MyProject.kicad_pcb`: board layout
- `MyProject.kicad_pro`: KiCad project file
- `gerbers.zip`: gerber and drill files, ready to send to a PCB manufacturer
- `Firmware/Starbie/Starbie.ino`: Arduino starter code from the guide (its pins already match my board)
- `Firmware/Starbie/Starbie.ino`: Arduino starter code from the guide (its pins already match my board)

## Status

The PCB design is finished and the gerber files are exported. I have not built the board yet, so the firmware is untested on my hardware. Next steps are getting the board made, assembling it, and uploading the code.

## Credits
Firmware and project design are based on the Starbie guide from Hack Club by SharKingStudios (MIT license): https://github.com/SharKingStudios/Starbie
I built the KiCad schematic and PCB layout following the guide.

