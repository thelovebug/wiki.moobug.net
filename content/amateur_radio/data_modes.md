+++
title = "Data modes"
+++

{{% notice style="info" %}}
This article was written by operator [Dave M7TLB][QRZ], for the Amateur Radio community.

Reach out to me via [QRZ][QRZ] for any additions and omissions.

[QRZ]: https://qrz.com/db/M7TLB

{{% /notice %}}

{{% notice style="warning" %}}
This is a new article, and thus a work in progress.
{{% /notice %}}

## What are Data Modes

A Data Mode is a term given to any communication over the Amateur Bands that isn't voice.  There are loads of them.  Seriously loads.  Wikipedia has a good article on the various [amateur radio modes](https://en.wikipedia.org/wiki/List_of_amateur_radio_modes) but only lists a small number of the more popular data modes, like FT8, FT4, JS8, RTTY, and PSK.  In typical "me" fashion, I've only listed those that I have had any experience with.  Actually, it could be argued that CW (Morse Code) is a data mode.

## Types of Data Mode

In simple terms, there are typically two different types of data mode: structured and freeform.

### Structured

Structured data modes are the type where there is a set pattern of communication - i.e. a "conversation" is limited by its structure and typically it's not possible to have a proper chinwag.

FT8 and FT4 are good examples of this type of data mode.  Each message contains (usually) three pieces of information: your callsign, my callsign, the message.  There are exceptions to this, but that's something that you can learn as you go along.

A typical structured conversation can go something like this:

| Direction | Message              | Meaning                                                                   |
| :-------: | -------------------- | ------------------------------------------------------------------------- |
|    Out    | `CQ M7TLB IO93`      | Calling anyone, I'm M7TLB, and I'm located at IO93                        |
|    In     | `M7TLB 2E1CEQ -06`   | Hello M7TLB, I'm 2E1CEQ, and your signal to me is -06                     |
|    Out    | `2E1CEQ M7TLB R-09`  | Hi 2E1CEQ, this is M7TLB again, thanks for that, your signal to me is -09 |
|    In     | `M7TLB 2E1CEQ RR73`  | Hey M7TLB, yup it's 2E1CEQ, thanks for your report, best wishes           |
|    Out    | `2E1CEQ M7TLB 73`    | Thanks 2E1CEQ, best wishes from M7TLB                                     |

On FT8, this conversation takes place over 5 messages taking 15 seconds each to transmit/receive, so 75 seconds in total.
On FT4, it's 7.5 seconds per message, so 37.5 seconds in total.

But that's essentially it.  It is possible to put a small amount of free text into a message - up to 13 characters, I believe - but certainly not sufficient to have a meaningful conversation.  Structured data modes are an excellent way of getting contacts as they can traverse long distances with low power.  My record up to this point (2022-07-27) is from the UK to Australia... approximately 10,000 miles, with 10 watts and a piece of wire.

The gold standard software for things like FT4 and FT8 is [WSJT-X](https://physics.princeton.edu//pulsar/K1JT/wsjtx.html), which supports something like 10 different data modes overall.  So once you have that set up correctly, you can - in theory - use any of those modes.  WSJT-X interfaces with your radio using a soundcard and an interface cable.

I wrote another article on [Setting up FT8 on Linux with the Xiegu G90](/FT8_on_Linux_with_Xiegu_G90), but I'm sure it serves as a general purpose guide for setting WSJT-X up for any hardware configuration.. but it doesn't tell you how to use it.  It's also a work in progress.  Isn't everything?

### Freeform

Freeform data modes offer a lot more freedom.  Yes, there is ettiquette around calling CQ - as is the case with any Amateur mode or band - but once the formality is out of the way, it's free text all the way.  Txtspk can work in your favour, as the fewer the letters in your message the quicker it can be sent.  Again, there are exceptions to this, but that's the fun part to find out.

Aside from CW - which I've never used - most of the freeform data modes also use a computer connected to your radio using a soundcard and interface cable.  If you're set up for WSJT-X, then you're probably good to go... you just need different software.

For JS8, you'll need [JS8Call](https://js8call.com/).
For RTTY, PSK, and a whole bunch of other modes, I'd recommend [fldigi](http://www.w1hkj.com/).

## What do data modes look like?

Check out these sites for visual and audible representations of the different data modes:

* [W1HKJ - Sights & Sounds](http://www.w1hkj.com/modes/index.htm)
* [Signal Identification Wiki - Amateur Radio](https://www.sigidwiki.com/wiki/Category:Amateur_Radio)
