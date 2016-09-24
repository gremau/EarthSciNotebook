# Communications system at Hidden Canyon

Communication with the [two
dataloggers](hiddencanyon:dataloggers) at [Hidden
Canyon](hiddencanyon:sitedescription) is made possible using
a wireless modem and three spread-spectrum radios.

## Devices and connectivity

### Sierra Wireless Raven XTG Modem (1)

` * Antenna is a dual band (800-1900 Mhz, with 5.12 and 6.12dB signal gain respectively) Wilson "Trucker" whip antenna mounted on the `[`Met`
`tower`](hiddencanyon:mettowers)`.
` * Connected to the internet via the AT&T wireless network
` * Fixed IP address
` * Modem can be configured with Sierra's AceManager program on a Windows machine.`

### Digi XBee-PRO PKG RF Modems (3)

` * A base radio (connected to Raven modem) communicates with each datalogger radio (2) on a separate radio channel.
` * Configuration of modems is through Digi's X-CTU software on a Windows machine (lab computer or laptop in the field).
` * All 3 use firmware version 10CD
` * All 3 use standard antennas
` * Command Sequence Character (CC) for all is 2D ("-")
` * PAN ID (ID) for all is 3171
` * Sleep mode (SM) for all radios is 1 (hibernation mode) - this means that when idle they should enter low-power hibernate mode. This doesn't seem to work on the 2 radios connected to dataloggers due to constraints in how the dataloggers' RS-232 ports operate.`

Connections and configuration settings
--------------------------------------

` - **Base radio**
`   - Connected to Raven XTG modem with RS-232 cable and null modem adapter
`   - MAC Address: 0013A2004063B85A
`   - Coordinator enable (CE) = 0
`   - Channel (CH) = C
`   - Source Address (MY) = 1
`   - Destination High (DH) = 0
`   - Destination Low (DL) = Switched between 2(Met radio), 3 (Forest radio), and 0 (Idle)`

` - **Met1 radio**
`   - Connected to Met1 datalogger with RS-232 cable and null modem adapter
`   - MAC Address: 0013A2004063B8D6
`   - Coordinator enable (CE) = 0
`   - Channel (CH) = C
`   - Source Address (MY) = 2
`   - Destination High (DH) = 0
`   - Destination Low (DL) = 1`

` - **Forest1 radio**
`   - Connected to Forest1 datalogger with RS-232 cable and null modem adapter
`   - MAC Address: 0013A200406AA06E
`   - Coordinator enable (CE) = 0
`   - Channel (CH) = C
`   - Source Address (MY) = 3
`   - Destination High (DH) = 0
`   - Destination Low (DL) = 1`

## LoggerNet software configuration

Communication and data transfer with the Hidden Canyon network over the
internet is initiated from a workstation in the Bowling lab using
LoggerNet software (Campbell Scientific Inc). The configuration for this
to work is as follows:

` * IPPort configured for the static IP of the Raven, port 3001.
` * Two Generic devices below the IPPort are the radios - configured to Raise DTR
` * One of the CR-23x is connected to each Generic device
` * When connecting to each datalogger, LoggerNet runs a unique dial script to change the channel of the base radio (using the ATDL command) to the address of the appropriate endpoint radio.
` * An end script changes the base radio back to an idle channel.
` * Communication system is available for three half-hour periods per day (see below).`

Dial script
-----------

` D3000                    # wait 3000 ms
` T"---" R"OK"4000         # enter command mode
` T"ATDL2^m" R"OK"4000     # change destination to 2 (or 3 for Forest logger)
` T"ATCN^m" R"OK"4000      # exit command mode`

End script
----------

` D3000
` T"---" R"OK"4000
` T"ATDL0^m" R"OK"4000    # change destination to 0 for idle
` T"ATCN^m" R"OK"4000`

## Power relays and program control

Running all three radios and the modem at all times would drain too much
power, so in addition to running in low-power mode when they are on, the
entire communication system operates from relay controllers (one at each
datalogger). These relays are switched on or off at programmed time
intervals using the datalogger control ports. Table 2 in the EDLOG
programs running on each datalogger is devoted to operating the relays.
Essentially all devices are switched on for thirty minutes every eight
hours, so the dataloggers should be available from 00:00 to 00:30am,
8:00 to 8:30am, and 16:00 to 16:30pm.

Table 2 EDLOG code
------------------

` ; run table every half hour
` *Table 2 Program
` 02: 1800    Execution Interval (seconds)
` 
` ; set control port 1 high every 8 hours
` 1:  If time is (P92)
`  1: 0        Minutes (Seconds --) into a
`  2: 480       Interval (same units as above)
`  3: 41       Set Port 1 High
`  
` ; set control port 1 low 30 minutes later
` 2:  If time is (P92)
`  1: 30        Minutes (Seconds --) into a
`  2: 480       Interval (same units as above)
`  3: 51       Set Port 1 Low`
