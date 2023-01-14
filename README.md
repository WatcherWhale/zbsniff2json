# Zigbee Sniff2Json

![logo](./logo.png)

## Requirements

Our project is based on the Killerbee project, primarily we altered the zbdump script to accomplish our results.

- https://github.com/riverloopsec/killerbee
- `requirements.txt`

## Usage

If all requirements are met, you can use the following command to start the script.
Below you find the different options to run the script with extra features.

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
