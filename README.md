# PgTgBridge
PgTgBridge (PgTg) is a software bridge between FlexRadio® FLEX-6000/FLEX-8000/Aurora™ series radios and the Elecraft® KPA1500 amplifier, KPA500 amplifier and KAT500 tuner.
PgTg has a plugin architecture so support for other amplifier and tuner models can be added. C# software developers can create their own amplifier/tuner plugins for use by PgTg.

PgTgBridge is available on [KD4Z.com](https://kd4z.com)


## Plugin projects

Reference implementations for developing third-party plugins for the PgTgBridge amplifier/tuner service. Each project demonstrates a complete plugin template using the MyModel/Internal architecture pattern.  Use these projects as a reference when creating PgTg plugins for other brands of amplifiers and tuners.

[View PgTgSamplePlugins on GitHub](https://github.com/KD4Z/PgTgSamplePlugins)

### SampleAmp — Amplifier-Only Plugin
[View on GitHub](https://github.com/KD4Z/PgTgSamplePlugins?tab=readme-ov-file#sampleamp--amplifier-only-plugin)

### SampleTuner — Tuner-Only Plugin
[View on GitHub](https://github.com/KD4Z/PgTgSamplePlugins?tab=readme-ov-file#sampletuner--tuner-only-plugin)

### SampleAmpTuner — Combined Amplifier+Tuner Plugin
[View on GitHub](https://github.com/KD4Z/PgTgSamplePlugins#sampleamptuner--combined-amplifiertuner-plugin)


## Raspberry Pi services for use with the GPIO plugin in PgTgBridge

PgTgBridge includes a plugin for controlling GPIO on a Raspberry Pi via TCP.  Configurable trigger events are wired into the PgTgBridge logic for PTT, Amplifier operate/standby status, and Tuner enable/bypass. These events are mapped to generic output channels and are sent to the defined IP/port of the service running on the Raspberry Pi. 

These services implement a timer watchdog feature that acts as a safety mechanism.  When a channel mapped to PTT in PgTgBridge, the value of "15" is sent every ten seconds. If the network connection drops, the amplifier will return to Receive mode when the timeout expires.

You may find using these services handy for other remote controlling applications. They accept a simple JSON string for commands making it easily accessible for control from Node-Red.

These projects are ready-to-use services that support commands from PgTg.  Goto Releases to find the download link for the deb file, or compile it yourself.

These are useful to key the PTT line of the Elecraft&trade; KPA500 from a relay hat on a Raspberry Pi. 


### PgTgPiGpio Service for PgTgBridge
TCP/JSON GPIO relay control service targeting Raspberry Pi 4 (Debian Trixie, libgpiod ≥ 2.0). Specifically for use with PgTgBridge built-in plugin PgTg PiGpio.

[View on GitHub](https://github.com/KD4Z/PgTgPiGpio)

### PgTgPiSequent — I2C Relay Control Service
TCP/JSON I2C relay control service targeting Raspberry Pi 4 (Debian Trixie) for relay hats from Sequent Microsystems.

Supports 4-relay HAT, 8-relay HAT, or 16-relay HAT. All three board types are supported. Configure the desired board in the config file.

Although specifically designed for use with PgTgBridge PgTgGpio built-in plugin, this service can be used as a smart wrapper to these relay boards making them easily accessible from Node-Red.

Sequent offers a version of the 16 relay hat with solid state relays and is highly recommended for fast, low latency and silent CW keying of the KPA500. 

[View on GitHub](https://github.com/KD4Z/PgTgPiSequent)

### Ser2net Configuration file

If you are setting up ser2net on your Pi following the PgTgBridge  Installation Guide, here is a direct link to the ser2net.yaml file mentioned in that guide.

[Download ser2net.yaml from GitHub](https://github.com/KD4Z/PgTg/blob/main/ser2net.yaml)

Or download directly to your Pi:
``` bash
wget https//github.com/KD4Z/PgTg/blob/main/ser2net.yaml
```
then copy it to /etc
```bash
sudo cp ser2net.yaml /etc
sudo service ser2net stop
sudo service ser2net start
```
