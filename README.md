# Raspberry Fan Control
> [!TIP]
> Optionally, you can download **_'tmon.py'_**, which is only used for monitoring the temperature.

### Download script
We'll use **_'curl -O'_** so we can overwrite if the file already exists.
```
curl -O 
```

### Edit script
To change the fan pin and temperature threshold. Make sure to replace 'path' with your path
```
sudo nano /'path'/tfan.py
```

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
