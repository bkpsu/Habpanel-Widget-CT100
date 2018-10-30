# HABpanel-Widget-CT100

![CT100](https://github.com/bkpsu/Habpanel-Widget-CT100/raw/master/CT100.png "CT100 Widget for HABPanel")

*Adapted from Tim Rogers's ecobee Habpanel widget

For configuration, you only need to point it to the existing HVAC items, my sample items:

```
/* Thermostat */
Group gHVAC
Number HVAC_HeatSetPoint "Heat Set [%.0f F]" <temperature_hot> (gHVAC){channel="zwave:device:12345678:node1:thermostat_setpoint_heating"} 
Number HVAC_CoolSetPoint "Cool Set [%.0f F]" <temperature_cold> (gHVAC) {channel="zwave:device:12345678:node1:thermostat_setpoint_cooling"}
Number Temperature_HVAC "Temperature [%.1f F]" <temperature> (gHVAC,Temp_Chart) {channel="zwave:device:12345678:node1:sensor_temperature"}
Number Humidity_HVAC "Humidity [%.1f %%]" <humidity> (gHVAC,Hum_Chart) {channel="zwave:device:12345678:node1:sensor_relhumidity2"}
Group gHVACStatus
Number HVAC_Mode "Mode" <flow> (gHVACStatus) {channel="zwave:device:12345678:node1:thermostat_mode" }
Number HVAC_Fan_Mode "Fan Mode [MAP(thermostatFanMode.map):%s]" <fan> (gHVACStatus) {channel="zwave:device:12345678:node1:thermostat_fanmode" }
Number HVAC_Operating_State "Op State [MAP(thermostatOpState.map):%s]" <flow> (gHVACStatus) {channel="zwave:device:12345678:node1:thermostat_state"}
Number HVAC_Fan_State "Fan State [MAP(thermostatFanState.map):%s]" <fan> (gHVACStatus) {channel="zwave:device:12345678:node1:thermostat_fanstate"}
Number HVAC_Battery "Battery State [%d %%]" <battery> (gHVACStatus) {channel="zwave:device:12345678:node1:battery-level"}
```

For the map files, I’m using:

thermostatFanMode.map

```
0=Auto Low
1=On Low
2=Auto High
3=On High
4=Unknown
5=Unknown
6=Circulate
```

thermostatFanState.map

```
0=Idle
1=Running
2=Running High
```

thermostatMode.map:

```
0=Off
1=Heat
2=Cool
3=Auto
4=Aux Heat
5=Resume
6=Fan Only
7=Furnace
8=Dry Air
9=Moist Air
10=Auto Changeover
11=Heat Econ
12=Cool Econ
13=Away
```

thermostatOpState.map:

```
0=Idle
1=Heating
2=Cooling
3=Fan Only
4=Pending Heat
5=Pending Cool
6=Vent / Economizer
```
