# ESP32-bluetooth-speakers
A set of dual-channel bluetooth speakers for a PC using an ESP32 and 5 inch speaker drivers.

I made this project to learn how to use the bluetooth capabilities of the ESP32, as well as handling audio. Not having speakers for my PC made this a great project to learn. 

# **CAD**

The only CAD for this project is the speaker case. The speaker case is designed as a box with two compartments. 
<img width="661" height="773" alt="image" src="https://github.com/user-attachments/assets/3e6b57b8-cf58-4ec5-be62-07abe83e434f" />
The bottom, larger compartment is for the speaker driver, which needs to be large for sound quality. The smaller electornics compartment on top is where all the electronics sit, and wires run between the speaker compartments to deliver the signal.
<img width="369" height="460" alt="image" src="https://github.com/user-attachments/assets/cd9ea2da-4744-4b59-8c75-364ff784b808" />



# **Electronics**

The ESP32 is the centre of thi project. It's bluetooth capability removes the requirement for a bluetooth audio module. The MCU recieves audio signal from the PC/Phone etc and sends it to the PCM5102, a digital to analog converter. From here, the analog signal is sent to the TPA3116 Amplifier, and then in turn to the speaker drivers. The speakers are dual-channel. The TPA3116 outputs this as dual channel, meaning only one amplifier is needed. To wire the speaker driver then, a small cable (Only a signal and ground) runs between the two speakers. This is because one speaker is the active, housing all electronics, and the other is passive, with only a speaker. 
<img width="688" height="577" alt="image" src="https://github.com/user-attachments/assets/f386a3ba-a2d4-4a93-9b36-64f874811658" />


To interface with the UI, there is a rotary encoder and 0.96" 128x64 Oled display to control things like equalization, volume and bluetooth.
<img width="875" height="432" alt="image" src="https://github.com/user-attachments/assets/79b2428e-3d12-4e2f-94e8-e9051ea17515" />


# **Firmware**

For audio handling, I used the official ESP-IDF program as firmware, which can be found here: https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/index.html 

For basic audio, I only had to configure it to my pins in board_pins.h . But for other features like equalization, volume control, rotary encoder, buttons, display etc I had to write files. The idea of the firmware is that the ESP32 connects via bluetooth, at which point it displays paired on the Oled. After this it can recieve audio, which passes through the equalization and volume control, of which I have made presets before being passed to the DAC. The rotary encoder can be used to: cycle through EQ presets, control volume and mode, which are visible on the Oled.

# **BOM**

### Printed parts

|Part| Image| Quantity|
|----|------|---------|
|Speaker case| <img width="661" height="773" alt="image" src="https://github.com/user-attachments/assets/7c4fa583-0fa8-4502-8fe3-f3b8357b83ff" /> | 2|

### Electronics

| Part| Quantity|
|-----|---------|
| ESP32 Devkit V1| 1|
| PCM5102 DAC| 1|
| TPA3116 Amplifier| 1|
| 3S 18650 Battery holder| 1|
| 5 inch speaker driver| 2|
| EC11 Rotary encoder| 1|
| 0.96" Oled display| 1|
| LM2596 Buck converter| 1|
