Originally from andiburger/growatt2mqtt, heavily modified to easily work with new and multiple protocols, configurable protocols, and added propper mqtt discovery / functionality to work with home assistant

# growatt2mqtt

Growatt2MQTT is a small python-based service which connects via usb to the Modbus interface of Growatt inverters and published the collected data on MQTT.
The python service can be configured via a small config file.

The config file is structured as follows:

# Installation
Connect the USB-B port on the inverter into your computer / device
When connected, the device will show up as a serial port. 

### install requirements
```
apt install pip python3 -y
pip install -r requirements.txt
```

### Config file (growatt2mqtt.cfg) - rename .example.cfg to .cfg
Edit configuration.
```
cp growatt2mqtt.example.cfg  growatt2mqtt.cfg
nano growatt2mqtt.cfg
```

### install as service
```
cp growatt2mqtt.example.service  /etc/systemd/system/growatt2mqtt.service
nano /etc/systemd/system/growatt2mqtt.service
```
edit working directory in service file to wherever you put the files
```
nano /etc/systemd/system/growatt2mqtt.service
```
reload daemon, enable and start service
```
sudo systemctl daemon-reload
sudo systemctl enable growatt2mqtt.service
sudo systemctl start growatt2mqtt.service
systemctl status growatt2mqtt.service
```

### donate
![BitCoin Donation](https://github.com/HotNoob/growatt2mqtt-hotnoob/blob/main/donate_to_hotnoob.png?raw=true)

```(btc) bc1qh394vazcguedkw2rlklnuhapdq7qgpnnz9c3t0```

### Use Docker - untested
- ```docker build -t growatt2mqtt ```
- ```docker run --device=/dev/ttyUSB0 growatt2mqtt```
