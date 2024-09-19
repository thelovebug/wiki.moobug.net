---
title: "&quot;... but it's not radio!&quot;"
status: new
---

!!! info
    This article was written by operator [Dave M7TLB][QRZ], for the Amateur Radio community.

    Reach out to me via [QRZ][QRZ] for any additions and omissions.

## Someone is wrong

One of the downsides of being a part of any SIG is the inevitable clashes over what is right or wrong within that particular field of interest.  Examples like: which Linux Desktop Environment is best, `vim` or `emacs`[^1], or - one of the most contentious of debates - beans first or cheese.

All of these can be umbrella'd quite nicely by the now-infamous [xkcd 386][386-lnk].

!["The image is of XKCD comic number 386 which shows someone typing furiously at a keyboard.  Off-panel, a second person says 'Are you coming to bed?' Person one replies, 'I can't. This is important.' Person two, 'What?' Person one, 'Someone is wrong on the internet.' (the word 'wrong' is underlined in emphasis)"][386-img]

## What is Amateur Radio, anyway?

I have enjoyed many a discussion on the above three debate topics (and others) that have been both entertaining and intriguing.  But never have I seen as much vitriol as I have under the subject of Amateur Radio and what actually constitutes "radio" in that context.

The Wikipedia page for [Amateur Radio][wiki-amateur] describes the hobby as:

!!! quote "Quote"
    Amateur radio, also known as ham radio, is the use of the radio frequency spectrum for purposes of non-commercial exchange of messages, wireless experimentation, self-training, private recreation, radiosport, contesting, and emergency communications.

... or as I like to say: **"educate, experiment, entertain"**.

The scope and field of Amateur Radio is huge.  Starting from something as simple and straight-forward as picking up a radio and talking to another Amateur operator a mile away over the air, progressing through to something as complex as using a digital radio which connects to a hotspot which then connects to a central hub via the internet which is then picked up by an internet-connected repeater in another continent which is then picked up and heard by another operator with an analogue radio in the middle of a field somewhere.  You've also got your computer-to-computer (or data) modes, which allow you to send very narrow coded symbols over much larger distances than you could do with voice.  Then, of course, there's the ultimate person-to-person data mode, CW or Morse Code.

## ... but it's not radio

I have been witness to some very measured (and, in other cases, incredibly vile) arguments regarding what "radio" actually is.  There are very many different interpretations around what "radio" means - particularly in the context of Amateur Radio.  Technically, none of them are wrong (although there is one particular use-case exception which I'll touch on in a bit).  Now, I want to qualify this by saying that, in the context of Amateur Radio, I'm defining "radio" as the use of the recognised Amateur Bands as defined by the ITU (and illustrated in [this Wikipedia article][wiki-amateurbands]).  I also want to make it clear that although some of the 13cm band overlaps with the 2.4GHz WiFi and Bluetooth allocations, I'm not counting the use of WiFi and Bluetooth as "radio" in this context.

## Yes, it is

In my opinion, and in the spirit of Amateur Radio [as defined above](#what-is-amateur-radio-anyway), any communication utilises the Amateur Radio bands at some point between the transmitter and the receiver, is "radio".

## Having said that

For as many different arguments and opinions of what "radio" is, there are as many about what a valid use of "radio" is in the context of the hobby.  I realise that this term may be offensive to some, but the spectrum of purism in the hobby is as wide as the scope of the hobby itself.  There are some who believe that if you're not talking over the air - direct radio to radio - with another operator, that's not "radio".  This discounts most of the data modes (because you're not actually having a conversation), the voice modes that are internet-assisted (because it's not radio end-to-end), any of the phone apps (Echolink, Droidstar, DVSwitch, etc) because they are basically internet, any of the SIP-based Voice Over IP mechanisms (which I mentioned over at my [SIP Services](sip_services.md) page).

And you know what... to a certain extent, I agree!  But does it actually matter?

There is nothing more gratifying than picking up a microphone at your house and having a voice conversation - over the air - with another operator 1,000 miles away in Croatia (like I did earlier this week).  But sometimes the bands are quiet and there's no-one on there, or you're not in a position to be able to speak, or you want to do radio when you're in the middle of a field with a hand-held radio (rather than with your home radio and antenna that peaks 10 meters into the air), or you want to challenge yourself and see if you can make some kind of contact with a station over the other side of the world.  Depending on your circumstances (and license class), that simply may not be possible.  

Let's say I want to speak with either of my friends [Allan G7VQV][qrz-g7vqv] or [Mark 2E1CEQ][qrz-2e1ceq] over the radio.  They only live a couple hundred miles south of me, so it must be possible, right?  Wrong.  The conditions have to be right, and the equipment at either end has to be right for the conditions.  Well, basically, I don't have that.  So if I want to speak to them, I can either pick up my desk phone and call them on HamsOverIP, or I can pick up a radio and chat to them over Allstar (radio both ends, internet in the middle), or I could ping them on Jitsi (no radio at all) but where's the fun in that.

A lot of these mechanisms that I've just mentioned - whilst they have the capability to interface with the Amateur Radio bands - are not inherently radio.  Services like Echolink, Peanut, SIP... but they have the _capability_ of being interfaced with Amateur Radio.  I can pick up my phone, dial `25006` and be connected to the FreeSTAR Network.  By using my phone's keypad, I can "key up" and be heard around the world over the Amateur Bands.  So I may not _start_ with radio, but it's in there somewhere.

At the start of this article, I used the words **"educate, experiment, entertain"** to describe what I feel is the spirit of Amateur Radio.  It's certainly the reason why I got involved in it.  I have (educate) learned so much in the 3½ years that I've had my license, I have (experiment) built my own antenna which has allowed me to be heard in Tazmania (~10,000mi away), I have (entertain) had an awful lot of fun in the process, and I have made some (excellent) friends on that journey.

## What's my point?

My point is very simple.

What is "radio" for some may not be "radio" for others.  Live with it.  If you don't like how someone does radio, then step away.  If they're breaking rules or license terms, then there are official channels for that.  No-one has the right to tell anyone else that what they are doing is wrong.  

Particularly when they're objectively not.

[QRZ]: https://qrz.com/db/M7TLB
[wiki-amateur]: https://en.wikipedia.org/wiki/Amateur_radio
[wiki-amateurbands]: https://en.wikipedia.org/wiki/Amateur_radio_frequency_allocations
[qrz-g7vqv]: https://qrz.com/db/G7VQV
[qrz-2e1ceq]: https://qrz.com/db/2E1CEQ
[386-lnk]: https://xkcd.com/386/
[386-img]: https://imgs.xkcd.com/comics/duty_calls.png

[^1]: Neither of these is correct, the right answer is in fact `nano`.
*[SIG]: Special Interest Group
*[CW]: Continuous Wave
