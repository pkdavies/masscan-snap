# MASSCAN-SNAP: Mass IP port scanner snap

This is the fastest Internet port scanner based on Robert David Graham's masscan tool:
https://github.com/robertdavidgraham/masscan

It can scan the entire Internet in under 6 minutes, transmitting 10 million packets per second.

It produces results similar to `nmap`, the most famous port scanner. Internally, it operates more like `scanrand`, `unicornscan`, and `ZMap`, using asynchronous transmission. The major difference is that it's faster than these other scanners. In addition, it's more flexible, allowing arbitrary address ranges and port ranges.

NOTE: masscan uses a **custom TCP/IP stack**. Anything other than simple port scans will cause conflict with the local TCP/IP stack. This means you need to either use the `-S` option to use a separate IP address, or configure your operating system to firewall the ports that masscan uses.

### Build Snap Manually
```sh
$ git clone https://github.com/pkdavies/masscan-snap.git
$ cd masscan-snap
$ snapcraft
```

### Installation
Simply call the snap package:
`sudo snap install masscan_*.snap --devmode --dangerous`

And then run it normally:
```sh
# masscan
usage:
masscan -p80,8000-8100 10.0.0.0/8 --rate=10000
 scan some web ports on 10.x.x.x at 10kpps
masscan --nmap
 list those options that are compatible with nmap
masscan -p80 10.0.0.0/8 --banners -oB <filename>
 save results of scan in binary format to <filename>
masscan --open --banners --readscan <filename> -oX <savefile>
 read binary scan results in <filename> and save them as xml in <savefile>
```

Follow the examples in Robert's repository.
