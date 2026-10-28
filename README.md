Build a DIY IR Remote Tester with a WeMos D1 Mini, an IR receiver, and an OLED display. Press any button on any remote and instantly see the protocol, hex code, and decoded command — no guessing, no serial monitor required.

In this tutorial, we wire up a VS1838B IR receiver and a 0.96" SSD1306 OLED to a WeMos D1 Mini, then walk through the code line by line. The sketch focuses on the NEC protocol — the most common one used by TVs, soundbars, and cheap remotes — decodes the address and command bytes, and looks up friendly button names.

Whether you're reverse-engineering a remote, building a universal remote, or just curious what's hiding in that IR beam, this is the project to start with.

Chapters
0:00 – Intro

0:20 – Parts you'll need

0:50 – Wiring the IR receiver and OLED

1:40 – Code: libraries and setup

2:20 – Code: decoding NEC and ignoring repeat frames

3:10 – Code: display layout and button name lookup

3:50 – Testing it live

4:20 – Next steps and wrap-up

Parts Used
Part	Notes
WeMos D1 Mini (ESP8266)	Any ESP8266 board works
VS1838B or TSOP38238 IR receiver	38 kHz demodulator
0.96" SSD1306 OLED	128×64, I2C, address 0x3C or 0x3D
Breadboard + jumper wires	—
Any IR remote	NEC remotes work best
Libraries
Install all three via the Arduino IDE Library Manager:

IRremoteESP8266 — IR decoding

Adafruit SSD1306 — OLED driver

Adafruit GFX Library — graphics primitives

Wiring
IR Receiver	WeMos D1 Mini
OUT	D5 (GPIO14)
VCC	3.3V
GND	GND
OLED	WeMos D1 Mini
SDA	D2 (GPIO4)
SCL	D1 (GPIO5)
VCC	3.3V
GND	GND
Quick Troubleshooting
Blank screen? Try I2C address 0x3D instead of 0x3C, and add a delay(250) at the top of setup().

Garbage in Serial Monitor? The D1 Mini is happiest at 9600 baud during boot.

Codes not showing? Check the IR receiver legs — OUT, GND, and VCC are not in the order you might expect.

Wrong button names? Press each button and read the Cmd:0x.. value, then add it to the necCmdName() switch.

Code
Full sketch is shown in the video. Paste it into the Arduino IDE, select LOLIN(WEMOS) D1 R2 & mini as your board, and upload.

What's Next
Store IR codes and transmit them with an IR LED

