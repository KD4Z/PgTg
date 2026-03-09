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

These services implement a timer watchdog feature that acts as a safety mechanism.  When a channel mapped to PTT in PgTgBridge, the value of "15" is sent every ten seconds. If the network connection drops, the amplifer will return to Recieve mode when the timeout expires.

You may find using these services handy for other remote controlling applications. They accept a simple JSON string for commands making it easily accessible for control from Node-Red.

These projects are ready-to-use services that support commands from PgTg.  Goto Releases to find the download link for the deb file, or compile it yourself.

These are useful to key the PTT line of the Elecraft KPA500 from a relay hat on a Raspberry Pi. 


### PgTgPiGpio Service for PgTgBridge
TCP/JSON GPIO relay control service targeting Raspberry Pi 4 (Debian Trixie, libgpiod ≥ 2.0). Specifically for use with PgTgBridge built-in plugin PgTg PiGpio.

[View on GitHub](https://github.com/KD4Z/PgTgPiGpio)

### PgTgPiSequent — I2C Relay Control Service
TCP/JSON I2C relay control service targeting Raspberry Pi 4 (Debian Trixie) with a Sequent Microsystems 16-relay HAT, Sequent Microsystems 8-relay HAT, or Sequent Microsystems 4-relay HAT. Board type is selected via the board config key; a single binary supports all three. Specifically for use with PgTgBridge built-in plugin PgTg PiGpio. Can be used as a smart wrapper to the relay board that is accessible using JSON strings such as from Node-Red.

Sequent offers a 16 relay hat with solid state relays and is highly recommended for fast, low latency and silent CW keying.

[View on GitHub](https://github.com/KD4Z/PgTgPiSequent)
