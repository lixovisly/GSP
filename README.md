# GSP
## Multi-Effect Guitar Sound Processing

### 1. Overview

The Guitar Sound Processing (GSP) is a multi-effect platform suited to stage performance, based on Electrosmith Daisy Seed. Its main highlights are:

  -	Easy using and easy effect setup changing
  -	Configurable effect sequence
  -	Chain sequences and setup stored in non-volatile memory
  -	Minimum lag time (latency)
  -	CD audio quality
  -	Wireless support for pedal switching, volume and effect configuration

GSP can be configured by commands in ASCII format through serial lines or USB. To accomplish for the minimum lag time, all the effects process audio signal in real time. CD audio quality means that the adopted sampling rate is equal or greater than 44.1 kHz, which restricts the lag time to less than 0.03 ms. Wireless communication can be established by interfacing the Daisy Seed (DS) with any external device by serial line (UART), like ESP32 WROVER or WROOM modules. These devices may also incorporate Blue Tooth, Wireless (IOT), and Flash SSD support for effect configuration storage. Additional peripherals can also be attached, like nRF24L01 modules, for example, to provide interfaces with expression pedals.

GSP comprises hardware and software. The GSP Driver is composed by an ElectroSmith Daisy Seed board, and a customized electronics. The software is based on libDaisy library. Figure below shows the expected GSP connections available for peripheral interfaces. The GSP Driver shall receive configuration commands coming from a PC computer through USB line, WiFi or Blue Tooth (BT), as well as from smartphones with BT, or a customized GSP console (yet to be developed) connected by USB line or BT. Action pedals (potentiometer or any variable voltage source) shall be directly attached to GSP Driver, or by Blue Tooth interface. 
![GSP peripherals](gsp_periph.jpg)
Next figure shows the GSP internal block. The input signal from guitar is conditioned by an analog electronics that amplifies the signal and applies an analogue compressor before being sent to ADC converter of Daisy Seed. After being processed the signal is delivered back to the electronics for amplification and analog expander. DS communicates with external devices by two serial lines: one to send and to receive commands and other to receive expression pedal data. The external device can be a ESP32, for instance, which provides direct access to BT drivers or any microcomputer such as Arduino. They can interface with nRF24L01 module to receive wireless data from expression pedals. These pedals must have a microprocessor with nRF24L01 incorporated to process and send potentiometer data to GSP. The multi-effect GSP can also be commanded by USB either through DS (except for stored configurations) or an external device, yet to be developed. The effects setup and chain configuration can be stored in SSD in the external device. Here the name “chain” will be used to indicate the effect sequence order, sometimes also named as signal path, pedal board, or guitar rig. 

GSP has several software modules. These modules can be selected to achieve a desired solution or configuration. For instance, there are modules to provide interpreted commands for chain configuration, or to print and to read console commands. The modules are grouped in

  -	GSP_EM - effect modules
  -	GSP_ML - main loop
  -	GSP_CC - control commands
  -	GSP_PT - potentiometer modules
  -	GSP_CH - chain configuration

GSP_EM comprises all possible effects algorithms to be included in the chain. GSP_ML has the main loop that provides ADC readings and DAC writings, as well as initialization of software modules and hardware. 
EM and ML modules run on Daisy Seed only. The following two (control commands and potentiometer) need part of software to run off DS. The last one runs off DS only. All modules will be described in proper documentation.

$$y_{lfo} = \frac{1 + \sin \phi}{2}$$
$$\begin{pmatrix}
1 & 2 & 3\\
a & b & c\\
\alpha & \beta & \gamma
\end{pmatrix}	
$$

