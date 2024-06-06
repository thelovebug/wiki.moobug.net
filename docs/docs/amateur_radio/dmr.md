---
title: "To Do: DMR"
---

!!! information
    This is a living document as I'm on my DMR journey now.  It will start as a to-do list, and ultimately become a reference, but it may change frequently.

## Configuration

* Codeplug - basically the radio's configuration: zones, channels, contacts, talkgroups
* Some of the config can be done on the radio, but most things require CPS
* Running CPS in a Windows 10 VM under Linux works a treat, just need to enable the USB redirection each time the radio restarts.
* Pi-Star: DMR Gateway allows connection to multiple DMR networks through the use of TG mapping.

## Networks

* **Brandmeister**
  * TG 2356 Chris MW7CCS has a net on Saturdays
* **FreeDMR**
  * [Repeater Simple mode](http://freedmr.uk/index.php/repeater-simple-mode) (Mark 2E1CEQ)
* **DMR+/Phoenix**
* **FreeStar**
* **TGIF**

## Learnings

* Using Duplex mode on Pi-Star makes Brandmeister think you're running a repeater, rather than a hotspot.  This means that any dynamic TG that you connect to will be timed out after 10 minutes of inactivity and you'll be disconnected from that TG.  You could specify a static TG for this purpose, but if you want to switch between TGs it starts to get a little more complex.  I've switched back to Simplex mode for now.
