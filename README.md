# GSP
## Multi-Effect Guitar Sound Processing

### 1. Overview

The Guitar Sound Processing (GSP) is a multi-effect platform suited to stage performance, based on Electrosmith Daisy Seed. Its main highlights are:

  -	Easy using and easy effect changing
  -	Configurable effect sequence
  -	Chain sequences and setup stored in non-volatile memory
  -	Minimum lag time (latency)
  -	CD audio quality
  -	Wireless support for pedal switching, volume and effect configuration

GSP can be configured by commands in ASCII format through serial lines or USB. To accomplish for the minimum lag time, all the effects process audio signal in real time. CD audio quality means that the adopted sampling rate is equal or greater than 44.1 kHz, which restricts the lag time to less than 0.03 ms. Wireless communication can be established by interfacing the Daisy Seed (DS) with any external device by serial line (UART), like ESP32 WROVER or WROOM modules. These devices may also incorporate Blue Tooth, Wireless (IOT), and Flash SSD support for effect storage. Additional peripherals can also be attached, like nRF24L01 modules, for example, to provide interfaces with expression pedals.
![GSP peripherals](/../resources/gsp_periph.jgp)
GSP comprises hardware and software. The GSP Driver is composed by an ElectroSmith Daisy Seed board, and a customized electronics. The software is based on libDaisy library. Figure 1 shows the expected GSP connections available for peripheral interfaces. The GSP Driver shall receive configuration commands coming from a PC computer through USB line, WiFi or Blue Tooth (BT), as well as from smartphones with BT, or a customized GSP console (yet to be developed) connected by USB line or BT. Action pedals (potentiometer or any variable voltage source) shall be directly attached to GSP Driver, or by Blue Tooth interface. In Figure 1, the software to handle commands through the dashed lines was not yet implemented.
