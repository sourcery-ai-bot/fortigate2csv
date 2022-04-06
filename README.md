# FortiGate to CSV Converter

This is a playground for extending the original upstream `fortigate2csv` tool. Currently it is not meant for real usage.

## The original documentation:

FortiGate web UI has no easy way to export a CSV (unless you also use FortiManager), so this script can be used to fetch JSON data over the REST API and export it as a CSV.

Some common objects are included, and you can easily modify and extend to your requirements.

## Usage

Command line arguments

* `-f` - Firewall IP/FQDN
* `-u` - Username
* `-v` - VDOM
* `-i` - Items *(interface, policy, snat, address, service, dnat, pool, addrgrp)*
* `-o` - CSV Outfile *(optional)*
* `-t` - Translate network object names to IPv4 *(optional)*

### Example

```
% python fortigate2csv.py -f 1.2.3.4 -u dan -v management -i address -o address.csv
Connecting to 1.2.3.4 (management) as dan
Successfully logged in as dan
Fetching data...
Logging out of firewall
Saving to address.csv
Done!
```

Output:

```
name,type,subnet,fqdn,associated-interface,visibility,allow-routing,comment
hst-1,ipmask,10.10.10.1 255.255.255.255,,v123,enable,disable,description of host 1
hst-2,ipmask,10.10.10.2 255.255.255.255,,v123,enable,disable,description of host 2
login.microsoft.com,fqdn,,login.microsoft.com,,enable,disable,comment goes here
...
```
