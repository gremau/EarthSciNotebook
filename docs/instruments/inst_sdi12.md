# Using SDI12 sensors

## General

SDI12 is a protocol for addressing and interacting with sensors in a network configuration. SDI12 devices have a unique address that 

## Wiring for Campbell dataloggers

SDI12 devices generally have at least 3 wires - power, ground, and serial communication. For a Campbell device the power will come from a 12V port (12V or SW12V), ground is G, and the serial wire connects to one of the COM ports (C1-C8). there may also be ground and shield wires for the serial circuit that should be connected to a G terminal.

## Changing SDI12 addresses

SDI12 devices on a circuit (connected to same serial port) need to have unique addresses. Potential addresses are "0-9","a-z", and "A-Z" (62 total). If the datalogger has multiple serial ports available these addresses may be reused in SDI12 commands through these additional ports.

SDI12 commands can be sent through a terminal program using the SDI12 protocol. The serial port location of the sensor must be specified. The basic SDI12 command that can be sent once connected to the SDI12 port through a terminal are:

    ?!   # Query the current SDI12 address of the connected sensor
    cAx! # Assign device to new address - "c" is current and "x" is new address

* For addressing sensors with a Campbell datalogger see the pdf linked from [here](http://www.decagonsdi12.com/system-set-up/addressing-sensors/)
* Info on this should also be in the sensor manual (esp Campbell sensors)


## Datalogger programming

The `aM!` and `aMx!` SDI12 commands, where `a` is the SDI12 address and `x` is a command modifier, are used to poll the sensor. Command `aM!` returns three values: VWC, EC, and T. Note that some sensors use internal logical tests to remove erroneous values (outside operational limits or accuracy specs) and return errorvalues such as 99999. Depending on the sensor, these logical tests may be ignored by sending the correct `Mx!` command.

In a CR Basic, the command to read an SDI12 sensor is `SDI12Recorder()`. The

 
