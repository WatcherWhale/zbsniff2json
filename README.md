# Zigbee Sniff2JSON
Welcome to our Sniff2JSON tool. This project was developed for the course "Wireless technologies". It sniffs for Zigbee traffic and outputs a JSON file with all the specifics.

![logo](./logo.png)


## Requirements

This project is based on the Killerbee project, primarily we altered the zbdump script to accomplish our tool. It still depends on some of the packages of Killerbee, so be sure to have those available as well.

- CC2531 usb dongle
- The Killerbee project: `https://github.com/riverloopsec/killerbee`
- `requirements.txt`


## Usage

When all requirements are met, you can use the following command to start the sniffing.

```shell
$ sudo ./zbsniff2json -c <CHANNEL> -o <OUTPUT FILE> -u
```

```
usage: zbsniff2json [-h] [-i DEVSTRING] [-d DEVICE] -o OUTPUT [-c CHANNEL] [-s SUBGHZ_PAGE] [-u]

zbsniff2json - a sniffing tool for ZigBee/IEEE 802.15.4 networks

options:
  -h, --help            Show this help message and exit.
  -i DEVSTRING, --iface DEVSTRING, --dev DEVSTRING
                        (Required) String: Path to the interface of the device being used.
  -d DEVICE, --device DEVICE
                        (Required) String: Name of the hardware device being used. E.g. apimote.
  -o OUTPUT, --output OUTPUT
                        (Required) Output file path.
  -c CHANNEL, --channel CHANNEL
                        (Required) Int: Channel value to listen on, from 11-26.
  -s SUBGHZ_PAGE, --subghz_page SUBGHZ_PAGE
                        (Optional) Int: Page value to listen on.
  -u, --update          (Optional) Update MAC vendor lookup table.
```

## Output

The output is a JSON file that contains multiple JSON objects. An example json capture file;

```JSON
{"type": "new_scn", "cha": 25, "frq":2475.0, "dev": null, "dvl": ["CC2531 USB Dongle (1:6)"], "pag":0}
{"type": "new_nwk", "pan": "0x7187", "cha": 25}
{"type": "nez_dev", "pan": "0x7187", "dev": "00:17:88:01:09:b2:36:e4", "man": "Philips Lighting BV", "cha": 25}
```

- new_scn; A new scan is starting.
  - Cha \
  The channel the tool is currently sniffing.
  - Frq \
  The frequency the tool is on.
  - Dev \
  The MAC address of the sniffing tool
  - Dvl \
  The hardware this script is using to sniff.
  - Pag \
  Pagina
    
- new_nwk; A new network is discovered that has not been discovered before.
  - Pan \
  PAN-ID of the network.
  - Cha \
  The channel that hosts this network.
- new_dev; A new device is found that has not discovered before.
  - Pan \
  The PAN-ID of the network this device is connected to.
  - Dev \
  The MAC address of the device.
  - Man
  If found: The manufacturer of this device.
  - Cha
  The channel that hosts this device.
