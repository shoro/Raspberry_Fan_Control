# Raspberry Fan Control
> [!TIP]
> Optionally, you can download **_'tmon.py'_**, which is only used for monitoring the temperature.

### Create a new file
```
sudo nano tfan.py
```

### Paste in the code
Make sure to change the fan pin and temperature threshold.
```
#!/usr/bin/env python3

import time
import sys
import os
import RPi.GPIO as GPIO

# GPIO pin configuration
FAN_PIN = 14
TEMP_ON = 60.0
TEMP_OFF = 50.0

def setup_gpio():
    GPIO.setmode(GPIO.BCM)
    GPIO.setup(FAN_PIN, GPIO.OUT)
    GPIO.output(FAN_PIN, GPIO.LOW)

def get_temp():
    with open("/sys/class/thermal/thermal_zone0/temp") as f:
        return int(f.read().strip()) / 1000.0

def control_fan(temp):
    if temp >= TEMP_ON:
        GPIO.output(FAN_PIN, GPIO.HIGH)
    elif temp <= TEMP_OFF:
        GPIO.output(FAN_PIN, GPIO.LOW)

if __name__ == "__main__":
    try:
        setup_gpio()
        while True:
            temp = get_temp()
            os.system('clear')
            control_fan(temp)
            sys.stdout.write(f"CPU Temp: {temp:.2f} °C\n")
            sys.stdout.flush()
            time.sleep(1)
    except KeyboardInterrupt:
        sys.stdout.write("\n")
        os.system('clear')
```
Save & Exit: **_Ctrl+X -> Y -> Enter_**

### Autorun at startup
Edit **_'rc.local'_**
```
sudo nano /etc/rc.local
```

### Paste in:
Make sure to replace 'path' with your path
```
#RPI Fan Control
sudo python3 /'path'/tfan.py &
```
Save & Exit: **_Ctrl+X -> Y -> Enter_**

### Reboot
```
sudo reboot
```
