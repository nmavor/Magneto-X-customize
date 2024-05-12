# Magneto-X-customize


## issues and fix

### resize disk (if you SD card is bigger then 8G)
```angular2html
sudo wget https://raw.githubusercontent.com/canonical/cloud-utils/main/bin/growpart -P /usr/local/bin/
sudo chmod +x /usr/local/bin/growpart
sudo growpart /dev/mmcblk1 2
sudo resize2fs /dev/mmcblk1p2
```
### set NTP

### set prob speed
the prob speed it too high 
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

as reference prob using klicky on voron 2.4
```
probe accuracy results: maximum 2.520000, minimum 2.507500, range 0.012500, average 2.517000, median 2.517500, standard deviation 0.003674
probe accuracy results: maximum 2.522500, minimum 2.510000, range 0.012500, average 2.520250, median 2.522500, standard deviation 0.003783
probe accuracy results: maximum 2.527500, minimum 2.512500, range 0.015000, average 2.524750, median 2.526250, standard deviation 0.004395
probe accuracy results: maximum 2.527500, minimum 2.512500, range 0.015000, average 2.524750, median 2.526250, standard deviation 0.004395
probe accuracy results: maximum 2.530000, minimum 2.512500, range 0.017500, average 2.525750, median 2.527500, standard deviation 0.005006
```