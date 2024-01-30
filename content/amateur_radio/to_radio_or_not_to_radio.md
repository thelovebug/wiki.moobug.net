+++
title = "To radio, or not to radio"
+++

In April 2021, I passed my Amateur Radio Foundation exam, and hold a valid Amateur Radio licence.  For this, I bought myself a Baofeng UV-5RTP as a transceiver to speak to other people in my local area.  In the first four weeks of holding my licence, I spoke to 7 individuals, the furthest being just shy of 40 miles away.  As it happens, that was my first ever QSO (amateur radio contact), and I've not managed to beat that distance over-the-air yet.

I'd heard about "repeaters" - essentially bridging stations that receive your transmission and then throw it out from there, giving you a greater range.  I was already messing around with a service called Echolink, which allows you to connect to some of these repeater stations over the internet.  This concept blew my mind when I first heard about it, thinking that using the internet to extend the range of traditional RF transmissions was an incredibly modern extension to the hobby.

Then, by accident, I discovered a local repeater (with Echolink) called MB7ALC, based a few miles away from here.  I noticed that this was a really busy repeater, with unusually high traffic than I'd experienced on Echolink previously.  What really caught me by surprise was that someone on there was talking to someone else down in the South West of England (I'm in the North of England), so I'm thinking that this South West person must be pushing some power to be able to reach this far up the country.  During that conversation, I heard mention of AllStar and something called HUBnet.  Doing some research into HUBnet, I discovered that it's a network of repeaters and gateways on the AllStar network.  This essentially meant that although I was using my phone or laptop to connect into a local Echolink repeater, I was actually transmitting all over the country out of this network!  Suddenly I felt very small, in the middle of a very large community.

In my first week of (unintentionally) using HUBnet, I managed to speak to other Amateur Radio operators in Weston-super-Mare (SW England), Liverpool (NW England), Dudley (Central England), Bolton (NW England), Kent (SE England), Pennsylvania (US), London, and... wait, what?  The US?  So at this point, I'm realising that this is an _international_ network of repeaters and gateways.  This removes pretty much every possible barrier to communicating with the rest of the world, as long as they can access an AllStar node (over the air or over the internet) that's connected to HUBnet.  At the time of writing this, I'm counting 135 nodes - worldwide - connected to this network.

The interesting thing about AllStar is that you can use it to connect one node to another - kinda like a telephone call - or you can bridge nodes together to form a network - which is how HUBnet works.  But you can also attach RF transmitters to these nodes and (with the right licence - that I don't currently have) make them available to any other Amateur operator within range, or just a really low-powered RF transmitter with a close range for personal use (my licence does cover that).

I recently discovered a little gizmo box called the G7RPG microHUB.  G7RPG is the callsign of Pete, who designed and builds them - on request - for anyone that wants one.  I ordered one from him, and it took about a week to arrive.  It was £135 all-in, and I literally plugged it in and it was working.  The microHUB is a Raspberry Pi running Asterisk (which is basically an IP telephony package), with a low-powered transceiver built in.

So, at this moment, I can "radio" in the following different ways:

* Traditional over-the-air RF radio using my little Baofeng
* Internet-assisted over-the-air using the Baofeng and the microHUB (at home only)
* Internet-assisted over-the-air using the Baofeng and a "public" repeater/gateway
* Internet-assisted using Echolink on my phone/tablet, or QTel on my laptop
* Many more different internet-assisted methods, like M17, using DudeStar/DroidStar

*I put "public" in quotes, as Amateur Radio still requires you to hold a valid licence to operate.*

In addition to Amateur Radio (internet-assisted or not), there are other technologies that have been made available to Amateur operators that don't - in and of themselves - use the Amateur Radio network.  One of them is Voice over IP (VoIP).  It's an telephone system, like your normal landline, but it's a closed system with private extension numbers issued to each phone on the network.  I currently have accounts on five different [SIP Services](/Amateur_Radio/SIP_Services).

So recently purchased a Cisco SPA525G2 IP phone (I previously had an SPA514G, but now my XYL/SWL has that) to connect to all my various services.  I already had a Sipgate phone number, so I assigned that to the SPA, plus four of the other five services.  IP telephony is a portable system, as it's based on the phone itself, not on the location of the phone.  So I could unplug the phone, take it to my mum's house, plug it into her network, and it would just carry on working.

Then I got to thinking that AllStar service (and therefore the microHUB) is essentially an Asterisk server itself, so I wanted to see if it was possible to connect my Cisco IP phone to the microHUB as an alternative to using my Baofeng UV-5RTP to connect to it... therefore making the phone my rig in the "shack"!

If you want to know the steps I went through to make this happen, go [here](/Amateur_Radio/Connect_SPA500_series_phone_to_AllStar).

You can view most of my shack kit on my [QRZ page](https://www.qrz.com/db/M7TLB).

73 de Dave M7TLB
