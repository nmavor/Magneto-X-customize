# Magneto-X-customize


## issues and fix

### Resize disk (if you SD card is bigger then 8G)
```angular2html
sudo wget https://raw.githubusercontent.com/canonical/cloud-utils/main/bin/growpart -P /usr/local/bin/
sudo chmod +x /usr/local/bin/growpart
sudo growpart /dev/mmcblk1 2
sudo resize2fs /dev/mmcblk1p2
```
if you using update OS (1.1.0 and up) you can run "RESIZE_FILESYSTEM" in the klipper console to do the same
### Set NTP
you will need to set the time zone by running sudo orangepi-config and in the menu under Personal select your timezone
### Set prob speed
the prob speed it too high update "speed: 2.0" to "speed: 0.5" under [probe]
prob speed at 2.0 
```

probe accuracy results: maximum -0.106250, minimum -0.146250, range 0.040000, average -0.125625, median -0.126875, standard deviation 0.015342
probe accuracy results: maximum -0.110000, minimum -0.150000, range 0.040000, average -0.131250, median -0.136875, standard deviation 0.014874
probe accuracy results: maximum -0.116250, minimum -0.153750, range 0.037500, average -0.134875, median -0.134375, standard deviation 0.014994
probe accuracy results: maximum -0.120000, minimum -0.153750, range 0.033750, average -0.136000, median -0.131875, standard deviation 0.010335
probe accuracy results: maximum -0.106250, minimum -0.153750, range 0.047500, average -0.129875, median -0.128750, standard deviation 0.013328
```
prob speed at 0.5
```
probe accuracy results: maximum -0.078750, minimum -0.090000, range 0.011250, average -0.084250, median -0.083750, standard deviation 0.003758
probe accuracy results: maximum -0.078750, minimum -0.090000, range 0.011250, average -0.083625, median -0.083125, standard deviation 0.003891
probe accuracy results: maximum -0.078750, minimum -0.090000, range 0.011250, average -0.084625, median -0.084375, standard deviation 0.003262
probe accuracy results: maximum -0.078750, minimum -0.088750, range 0.010000, average -0.084000, median -0.084375, standard deviation 0.003482
probe accuracy results: maximum -0.078750, minimum -0.091250, range 0.012500, average -0.083875, median -0.082500, standard deviation 0.004163
```
as you can see, if you drop the speed to 0.5  standard deviation drop from 0.015342-0.013328 to 0.003758-0.004163
as a reference prob, using klicky on voron 2.4
```
probe accuracy results: maximum 2.520000, minimum 2.507500, range 0.012500, average 2.517000, median 2.517500, standard deviation 0.003674
probe accuracy results: maximum 2.522500, minimum 2.510000, range 0.012500, average 2.520250, median 2.522500, standard deviation 0.003783
probe accuracy results: maximum 2.527500, minimum 2.512500, range 0.015000, average 2.524750, median 2.526250, standard deviation 0.004395
probe accuracy results: maximum 2.527500, minimum 2.512500, range 0.015000, average 2.524750, median 2.526250, standard deviation 0.004395
probe accuracy results: maximum 2.530000, minimum 2.512500, range 0.017500, average 2.525750, median 2.527500, standard deviation 0.005006
```

### Save your UPS 
the Magneto-X power kill my USP do to the amp drow you can workaround it but update the speed the hotbed heat up
just add "max_power: 0.7" to [heater_bed]

### Update your cancel_print macro (before 1.1.3)
The "cancel_print" just stops the print to make it more useful. Add the following to your macros.cfg
```
[gcode_macro CANCEL_PRINT]
description: Cancel the actual running print
rename_existing: CANCEL_PRINT_BASE
gcode:
    CLEAR_PAUSE
    SDCARD_RESET_FILE
    PRINT_END
    BASE_CANCEL_PRINT
```

### Pi fan temp
on day to day my Pi is sit on 55-57c so the Electronics fan kick every 5110 years the "fix" was to update the fan to work on 60c
```angular2html
[temperature_fan pi]
# Electronics fan PWM
pin: PD15
max_power: 0.60
control: watermark
max_delta: 5.0
sensor_type: temperature_host
min_temp: 10.0
max_temp: 80.0
target_temp: 60.0
shutdown_speed: 0.0
```

### add MCU temp 
to add the MCU temp add the follow to printer.cfg 
```angular2html
[temperature_sensor mcu_temp]
sensor_type: temperature_mcu
min_temp: 0
max_temp: 100
```

### add MAG_TOOL temp
to add the MAG_TOOL MCU temp add the follow to printer.cfg 
```angular2html
[temperature_sensor mag_tool_temp]
sensor_type: temperature_mcu
sensor_mcu: MAG_TOOL
min_temp: 0
max_temp: 100
```

### speed up QGL
after you pass the first QGL and the bed is close to be good you can drop horizontal_move_z from 20 to 5 
it will cut 1-2Min from QGL 
```angular2html
[quad_gantry_level]
gantry_corners:
  0,0
  290,390

points:
  25,25
  25,380
  290,380
  290,25

speed: 250
horizontal_move_z: 5.0
retries: 3
retry_tolerance: 0.025
max_adjust: 50
```

### webcam framerate
the webcan is hard code to use 10 FPS you can turn it up to 20~25 easy by edit crowsnest.conf and set max_fps to 25
