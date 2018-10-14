# Kostal Inverter Binding

Scrapes the web interface of the inverter for the metrics of the supported channels below.

![Kostal Pico](doc/kostalpico.jpg)

## Supported Things

Tested with Kostal Inverter Pico but might work with other inverters from kostal too.

## Discovery

None

## Channels

-   acPower
-   totalEnergy
-   dayEnergy
-   status
-   str1Voltage
-   str1Current
-   str2Voltage
-   str2Current
-   l1Voltage
-   l1Energy
-   l2Voltage
-   l2Energy
-   l3Voltage
-   l3Energy

## Thing Configuration

demo.things

```
Thing kostalinverter:kostalinverter:inverter [ url="http://192.168.0.128" ]
```

If the thing goes online then the connection to the web interface is successful.
In case it is offline you should see an error message.
You optionally can define a `userName` and a `password` parameter if the access to the webinterface is protected and a desired `refreshInterval` (the time interval between updates, default 60 seconds).

## Items

demo.items:

```
* solar power (AC) */
Number:Power SolarPower "Solar power [%.1f %unit%]"                     <energy> { channel="kostalinverter:kostalinverter:inverter:acPower" }

/* solar energy */
Number:Energy SolarEnergyDay         "Solar day energy [%.3f %unit%]"   <energy> { channel="kostalinverter:kostalinverter:inverter:dayEnergy" }
Number:Energy SolarTotalEnergy       "Solar total energy [%.3f %unit%]" <energy> { channel="kostalinverter:kostalinverter:inverter:totalEnergy" }

String        SolarStatus            "Solar status [%s]"                <energy> { channel="kostalinverter:kostalinverter:inverter:status" }

/* solar inverter String 1*/
Number:Energy solar_Str1_voltage     "String1 voltage [%d V]"                    { channel="kostalinverter:kostalinverter:inverter:str1Voltage" }
Number:Energy solar_Str1_current     "String1 current [%.2f A]"                  { channel="kostalinverter:kostalinverter:inverter:str1Current" }

/* solar inverter String 2*/
Number:Energy solar_Str2_voltage     "String2 voltage [%d V]"                    { channel="kostalinverter:kostalinverter:inverter:str2Voltage" }
Number:Energy Solar_Str2_current     "String2 current [%.2f A]"                  { channel="kostalinverter:kostalinverter:inverter:str2Current" }

/* solar inverter output voltage and power phase 1 (L1) */
Number:Energy solar_out_L1_voltage   "L1 voltage [%d V]"                         { channel="kostalinverter:kostalinverter:inverter:l1Voltage" }
Number:Energy solar_out_L1_power     "L1 power [%d W]"                           { channel="kostalinverter:kostalinverter:inverter:l1Energy" }

/* solar inverter output voltage and power phase 2 (L2) */
Number:Energy solar_out_L2_voltage   "L2 voltage [%d V]"                         { channel="kostalinverter:kostalinverter:inverter:l2Voltage" }
Number:Energy Solar_out_L2_power     "L2 power [%d W]"                           { channel="kostalinverter:kostalinverter:inverter:l2Energy" }

/* solar inverter output voltage and power phase 3 (L3) */
Number:Energy solar_out_L3_voltage   "L3 voltage [%d V]"                         { channel="kostalinverter:kostalinverter:inverter:l3Voltage" }
Number:Energy solar_out_L3_power     "L3 power [%d W]"                           { channel="kostalinverter:kostalinverter:inverter:l3Energy" }
```
