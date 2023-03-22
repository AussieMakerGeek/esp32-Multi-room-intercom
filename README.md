# Overview
This project is a work-in-progress (currently non-functional test/beta), multi-room intercom system based on the original esp32 Walkie Talkie code by Atomic14.

It uses i2S microphones and amplifiers, and transmits the audio over UDP broadcast

Platform.IO is not an environment I am used to coding in. There may be cringeworthy code in my changes. If you spot something, please point it out.

The theory of operation is to have 5 buttons on the console for 4 rooms and a 'broadcast' button. Each unit has it's own room number and will only play messages destined for it, or the broadcast address.

A single byte header is applied to every packet sent, ranging from 0x00 (broadcast) to 0x04 depending on button pressed.  There is no reason you could not add more, the only restriction being io pin availability for the tx button.  Each speaker is hard coded to an ID and only plays messages with the header of that ID or 0x00.

Audio data is transmitted over UDP broadcast

# Setup

Everything is configured from the `src/config.h` file.

Make sure you update the WiFi SSID and Password:

```
// WiFi credentials
#define WIFI_SSID << YOUR_SSID >>
#define WIFI_PSWD << YOUR_PASSWORD >>
```

The pins for the microphone and the amplifier board are all setup in the same `config.h` file.

# Building and Running

Open up the project in Platform.IO and connect your ESP32. You should be able to just hit build and run.

Obviously, you'll need two ESP32 boards and components to do anything :)
