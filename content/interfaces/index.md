+++
title = '2. WHAD devices'
draft = false
description = "Discover how WHAD manages its hardware devices"
author = "Damien Cauquil"
date = "2025-10-20T09:00:00+01:00"
type = "page"
icon = "fa-solid fa-microchip"
color = "blue"
width = "4"
+++

{{< info title="In this lesson, you will learn">}}
- how _WHAD_ communicates with a compatible hardware device
- how to list or find active devices
- how to get extra information about a specific device
{{< /info >}}

# How does it work under the hood _(beginner version)_

*WHAD* requires a compatible hardware device to interact with the outside world
and perform various tasks, and in order to achieve these tasks this hardware
device needs to match some criterions:
- it must be detected by *WHAD* and able to understand WHAD's requests as well as sending received data back to the framework
- it must support the required communication protocol, modulation or base frequency
- it must be able to send, receive or capture data from air depending on the task

Many hardware devices are compatible with *WHAD* but not all of them do support the
correct required frequency range or wireless protocol or modulation, so we have to
pick one that fits our needs and tell *WHAD* to use it. *WHAD* will then check that
the specified device does effectively meet all the requirements, and start all the
tasks it need to do. How is it possible? Well, that's because of a custom communication
protocol used to exchange data between the framework core and any compatible device.

## Domains, capabilities and commands

Hardware devices compatible with *WHAD* must support our *WHAD* protocol to successfully
be detected by the framework. No need to know how this protocol works under the hood,
the only aspects we need to know about a hardware device are:
- what *domains* (or *wireless protocols*) a device support
- the device's capabilities for each supported *domain*
- the device's supported *commands* for each supported *domain*

This *WHAD* protocol includes a specific feature to ask any device for all
of this information. The framework can, once a communication channel opened with the
specified hardware device, ask the device to tell what *domains* it support and for
each of them what *capabilities* it provides and what *commands* are supported. This
discovery feature is what *WHAD* uses to ensure a specific hardware device can be used
to achieve a specific task, and rest assured it will show an error if the specified
device does not meet all the requirements.

# Identifying devices

*WHAD* provides a command-line tool to automatically discover all supported devices
and query a specific hardware device for its supported *domain(s)*, *capabilities*
and *commands*.

## Listing all supported hardware devices

To list all supported hardware devices, just run `wup` as follows:

```sh
$ wup
[i] Available devices
- hci1
  Type: Hci
  Index: 1
  Identifier: hci1

- hci2
  Type: Hci
  Index: 2
  Identifier: hci2
```

In this example, two *HCI* devices (i.e. *Bluetooth adapters*) have been identified,
`hci1` and `hci2`. 

## Getting more information about a device

If we want to get more information about the `hci1` device, we simply pass the device
name to `wup`:

```sh
$ wup hci1
[i] Connecting to device ...
[i] Device details

 Device ID: c3:a7:c3:ba:c3:99:c2:84:6e:c2:a8:54:50:2d:4c:69:6e:6b:20:42:6c
 Firmware info:
 - Author : Realtek Semiconductor Corporation
 - URL : <unknown>
 - Version : 5.1.57286

[i] Discovering domains ...
[i] Domains discovered.

 This device supports Bluetooth LE:
 - can scan devices
 - can simulate a role in a communication
 - can not read/write raw packet

 List of supported commands:
  - SetBdAddress: can set BD address
  - ScanMode: can scan devices
  - AdvMode: can advertise as a BLE device
  - SetAdvData: can set advertising PDU details
  - CentralMode: can act as a Central device
  - ConnectTo: can initiate a BLE connection
  - SendPDU: can send a PDU
  - Disconnect: can terminate an active connection (in Central mode)
  - PeripheralMode: can act as a peripheral
  - Start: can start depending on the current mode
  - Stop: can stop depending on the current mode
  - SetEncryption: can enable encryption during a connection
```

`wup` displays a short summary including the device identifier, some information about
its firmware (in the example above, no information is available because we are using
an onboard bluetooth adapter), and its version:

```text
 Device ID: c3:a7:c3:ba:c3:99:c2:84:6e:c2:a8:54:50:2d:4c:69:6e:6b:20:42:6c
 Firmware info:
 - Author : Realtek Semiconductor Corporation
 - URL : <unknown>
 - Version : 5.1.57286
```

{{< info >}}
Some hardware devices running a custom firmware provides the URL of the related project
where an up-to-date version of this firmware can be found.
{{< /info >}}

It then discovers the domains supported by this device as well as its capabilities for
each of them:

```text
 This device supports Bluetooth LE:
 - can scan devices
 - can simulate a role in a communication
 - can not read/write raw packet
```

In our case, it supports the *Bluetooth Low Energy* domain and is able to scan, simulate
a role in a communication (initiating a connection and receiving a connection) but it
cannot send or receive raw packets. Packet sniffing is not possible either.
Last but not least, a list of every supported command and their roles is showed:

```text
 List of supported commands:
  - SetBdAddress: can set BD address
  - ScanMode: can scan devices
  - AdvMode: can advertise as a BLE device
  - SetAdvData: can set advertising PDU details
  - CentralMode: can act as a Central device
  - ConnectTo: can initiate a BLE connection
  - SendPDU: can send a PDU
  - Disconnect: can terminate an active connection (in Central mode)
  - PeripheralMode: can act as a peripheral
  - Start: can start depending on the current mode
  - Stop: can stop depending on the current mode
  - SetEncryption: can enable encryption during a connection
```

These commands are used by *WHAD* to interact with the hardware device and show some
of the features this hardware device provides.

# Practice time

Use `wup` to list all the supported devices available on your machine. If you own a
USB Bluetooth dongle, feel free to plug it in and run the command again to see if it
is correctly detected.

Then use `wup` followed by one of the detected device's name and discover what *domain*
it supports and what are its *capabilities*.


