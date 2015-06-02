---
layout: post
title: Build RTB Project - Logs
author: Van-Duyet Le
---

2 source: 
  - OpenRTB2x: [https://github.com/openrtb/openrtb2x](https://github.com/openrtb/openrtb2x) --> source đủ SSP, DSP: đang tìm hiểu 
  - openrtb-core: [https://github.com/google/openrtb](https://github.com/google/openrtb) --> core rtb của google, tuân theo chuẩn của IAB, chỉ là API, phải tự build server.
  
----------------------
# 02/06/2015

### Cài đặt Maven 

(Ubuntu)

```
sudo apt-get install maven
```

### Cài đặt *protobuf*

`protoc` giao thức truyền thông điệp của Google

- Cài đặt Libtool: `sudo apt-get install libtool`
- Clone source: [https://github.com/google/protobuf.git](https://github.com/google/protobuf.git)
- Compile and install 

```
$ ./autogen.sh
$ ./configure
$ make
$ make check
$ make install
```

Update: không nhận lib 
***export LD_LIBRARY_PATH=/usr/local/lib***

Update không nhận protoc trong maven: 

```
git clone https://github.com/usmanismail/maven-protoc-plugin.git
cd maven-protoc-plugin
mvn clean install

```

## Cài đặt OpenRTB-Core 

Đây là bộ RTB Core của Google, Download và Build bằng Maven 

- Clone source Google openrtb-core

```
git clone https://github.com/google/openrtb
cd openrtb
```

- Build, deploy các kiểu

```
mvn clean build 
```


## Cài đặt TomCat 7

Cần Tomcat để chạy ***dsp-web*** và ***ssp-web***

Xem ở đây: [http://note.lvduit.com/running-tomcat/](http://note.lvduit.com/running-tomcat/)

------------


