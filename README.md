# PgTgBridge
PgTgBridge (PgTg) is a software bridge between FlexRadio® FLEX-6000/FLEX-8000/Aurora™ series radios and the Elecraft® KPA1500 amplifier, KPA500 amplifier and KAT500 tuner.
PgTg has a plugin architecture so support for other amplifier and tuner models can be added. C# software developers can create their own amplifier/tuner plugins for use by PgTg.

PgTgBridge is available on [KD4Z.com](https://kd4z.com)


## Plugin projects

Reference implementations for developing third-party plugins for the PgTgBridge amplifier/tuner service. Each project demonstrates a complete, working plugin using the MyModel/Internal architecture pattern.

[PgTgSamplePlugins](https://github.com/KD4Z/PgTgSamplePlugins)

### SampleAmp — Amplifier-Only Plugin
[View on GitHub](https://github.com/KD4Z/PgTgSamplePlugins?tab=readme-ov-file#sampleamp--amplifier-only-plugin)

### SampleTuner — Tuner-Only Plugin
[View on GitHub](https://github.com/KD4Z/PgTgSamplePlugins?tab=readme-ov-file#sampletuner--tuner-only-plugin)

### SampleAmpTuner — Combined Amplifier+Tuner Plugin
[View on GitHub](https://github.com/KD4Z/PgTgSamplePlugins#sampleamptuner--combined-amplifiertuner-plugin)


## Raspberry Pi services for use with the GPIO plugin in PgTgBridge

### PgTgPiGpio Daemon for PgTgBridge
TCP/JSON GPIO relay control service targeting Raspberry Pi 4 (Debian Trixie, libgpiod ≥ 2.0). Specifically for use with PgTgBridge built-in plugin PgTg PiGpio. Can be used as a smart wrapper to GPIOD that is accessible using JSON strings such as from Node-Red.

[View on GitHub](https://github.com/KD4Z/PgTgPiGpio)

### PgTgPiSequent — I2C Relay Control Service
TCP/JSON I2C relay control service targeting Raspberry Pi 4 (Debian Trixie) with a Sequent Microsystems 16-relay HAT, Sequent Microsystems 8-relay HAT, or Sequent Microsystems 4-relay HAT. Board type is selected via the board config key; a single binary supports all three. Specifically for use with PgTgBridge built-in plugin PgTg PiGpio. Can be used as a smart wrapper to the relay board that is accessible using JSON strings such as from Node-Red.

[View on GitHub](https://github.com/KD4Z/PgTgPiSequent)
