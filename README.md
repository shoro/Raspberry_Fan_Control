# Raspberry Fan Control

### Download script
We'll use **_'curl -O'_** so we can overwrite if the file already exists.
```
curl -O  https://github.com/shoro/Raspberry_Fan_Control/blob/main/tfan.py
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

### Paste
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
