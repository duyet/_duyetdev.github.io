---
layout: post
title: Connect to OpenVPN Ubuntu
---

* First you need the `openvpn` package:

```sh
sudo apt-get install openvpn
```

* Download config file `.ovpn` 

* Connect to server

```sh
sudo openvpn --config /path/to/config.ovpn
```
