+++
title = '3. Explore BLE devices'
draft = false
description = "Scan, connect and interact with BLE devices using off-the-shelf tools"
author = "Damien Cauquil"
date = "2025-10-19T09:00:00+01:00"
type = "page"
icon = "fa-brands fa-bluetooth-b"
color = "blue"
width = "4"
+++

{{< info title="In this lesson, you will learn">}}
- how to discover Bluetooth Low Energy devices and connect to them
- how to explore a BLE device, enumerate its exposed services and characteristics
- how to read the value of a given characteristic
- how to write data into a characteristic value
- how to subscribe for notifications and indications
{{< /info >}}

# wble-central, the perfect tool for BLE exploration

*WHAD* provides a tool called `wble-central` that acts as a *Central* device and allows:
- scanning for *Bluetooth Low Energy* devices in the viscinity,
- connect to a *BLE* device
- explore a device's GATT attributes and its associated services and characteristics,
- interact with a device's characteristics

{{< info title="Bluetooth specification" >}}
In the *Bluetooth specification*, a *Central* device is defined as a device able to
listen to any advertising device and to initiate a connection to any device that is
advertised as *connectable*.
{{< /info >}}

This tool also implements an interactive shell that is very useful to explore devices
in the viscinity without having to write some Python code. To run `wble-central` in
interactive mode, simply execute the following command:

```shell
(whad)$ wble-central -i hci0
```

The `-i` option passed to `wble-central` specifies a *Bluetooth Low Energy* hardware
device that will be used by this tool. This option is mandatory as *WHAD* CLI tools
are not designed to automatically search for a compatible interface to avoid messing
up with compatible devices possibly used by other applications. You should be greeted
with the following prompt:

```shell
wble-central>
```

## Searching for devices

The `scan` command starts an active scan and lists every advertising device based on the
received advertisements, with their names extracted from their advertising information:

```shell
wble-central> scan
TODO: example of scanned devices
```

Every device discovered during a scan is kept in a cache with all its corresponding details
including its *Bluetooth Device* address, its address type and its name if provided. The
list of cached devices can be displayed at any time thanks to the `devices` command:

```shell
wble-scan> devices
TODO: example of cached devices
```

{{< info title="Bluetooth Device address" >}}
In the Bluetooth specification, a *Bluetooth Device* or *BD* address is a unique identifier
for a specific device, that not only identifies a specific device at a specific time but also
gives some additional information about the type of address. Some devices use *resolvable*
addresses that have some specific bits set. These addresses are often mistakenly called *MAC*
addresses as a reference to the well-known network *Media Access Control* addresses used by
network interfaces as their unique identifiers, but the name "*BD* address" is preferred to
avoid confusion.
{{< /info >}}

This cache is used by `wble-central` to feed its auto-completion feature and make it easier
to select a device *BD* address thanks to this feature. Typing the first digits of
an address followed by a press on the [TAB] key will spawn a drop-down list containing all
the matching devices. 

## Exploring a target device

### Connecting to the device

The `connect` command is used to initiate a connection to a given device based on its advertised
name or its *BD* address:

```shell
wble-central> connect TODO
```

Initiating a connection can take from a few milliseconds to many seconds depending on the
target device advertising settings. If no connection can be established within 30 seconds,
the operation fails and a timeout error is shown. If a connection has successfully been
established, the prompt will reflect this state:

```shell
wble-central [TODO]>
```

### Enumerating services and characteristics

### Reading a characteristic's value

### Writing data into a characterstic's value 

### Subscribing for notifications or indications

### Disconnecting


