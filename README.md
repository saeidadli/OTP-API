# OpenTripPlanner API for Python

This package uses OpenTripPlanner(OTP)API to run network analysis of public transportation (PT).

Below briefly explains how to set up OTP, what the scripts input and return, and how to run them.

---

## Setting up OTP

OTP is an open source multi-model transportation routing engine ([official website](http://www.opentripplanner.org/), [online documentation](http://docs.opentripplanner.org/en/latest/)). 

To use OTP API it is necessary to setup OTP server. The following shows the steps to setup the OTP server:

### Install Java

OTP is written in Java. It is necessary to intall download and install 64-bit Java Runtime Environment (not 32-bit). This can be downloaded here:

```
wget https://java.com/en/download/manual.jsp
```

### Download OTP

The OTP can be downloaded in the executable .jar file format. The version I used for this repo is ```otp-1.1.0-shaded.jar```. This can be downloaded here:

```
wget https://repo1.maven.org/maven2/org/opentripplanner/otp
```

### Download network files

To use OTP for PT network analysis we need an Open Street Map (OSM) file of the street nework and a General Tansit Feed Specification (GTFS) for the PT data.

The OSM can be downloaded from:

```
wget https://www.openstreetmap.org
```

The GTFS can be downloaded from:

```
wget https://transitfeeds.com
```

### Run OTP server

To run the OTP sever, put the OSM, GTFS and OTP .jar files into a folder (e.g. ```D:\otp```) and use the following commands to build a routable graph.

```shell
java -Xmx2G -jar otp-1.1.0-shaded.jar --build D:\otp --inMemory
```

The ```4``` in the ```-Xmx4G``` refers to how much memory should be alocated to the build.

Check out ```http://localhost:8080/``` to test if it's routing properly.

---

## Use the OTP web API

I have found two ways to use the OTP API:
1 - Routing: finds the best PT route connecting two locations.
2 - Isochrone: finds the area accessible from a location by PT.

examples of both routing and isochrone can be found in the ```ipynb\example.ipynb```.

---
