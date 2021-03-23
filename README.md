# Raspberry-Zero-Mouse-Simulation
Simulate mouse and keyboard via Raspberry Pi OTG 

_There are many tutorials how to simulate keyboard input with the Raspberry Pi zero, but no good how to simulate mouse movement. Here is a reliable way._

1. Preparation:
```
echo "dwc2" >> /etc/modules
echo "libcomposite" >> /etc/modules
```

2. Copy HID file:
```
cp usb-hid /usr/bin/
```

3. Add `/usr/bin/usb-hid` to `rc.local`
4. Reboot
5. Clone https://github.com/aagallag/hid_gadget_test
6. `make`
7. `chmod +x hid-gadget-test`
8. Use hid-gadget-test to use the mouse:
```
# move mouse (100,100)
echo ' 100 100' | ./hid-gadget-test/dev/hidg0 mouse > /dev/null
# move mouse (100,100) and hold button b1
echo '--hold --b1 100 100' | ./hid-gadget-test /dev/hidg0 mouse > /dev/null
```
