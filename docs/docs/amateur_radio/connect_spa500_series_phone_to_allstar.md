---
title: "Connecting a Cisco SPA500-series IP phone to your AllStar node"
---

!!! info
    This article was written by operator [Dave M7TLB][QRZ], for the Amateur Radio community.

    Reach out to me via [QRZ][QRZ] for any additions and omissions.

[QRZ]: https://qrz.com/db/M7TLB

In my [introductory post](to_radio_or_not_to_radio.md), I give some (translation: a lot of) detail into how I got involved with using internet-assisted technology to enhance and enrich the experience of Amateur Radio.

Now, I'm not going to get into the politics of whether using the internet for Amateur Radio is actually Amateur Radio or not... you'd get different answers from different people on this subject. I fall on the side of pragmatism: anything that advances the hobby has got to be a good thing, right?

I mentioned previously about purchasing a Cisco SPA514G IP phone for the Hamshack Hotline service, and that whilst I was waiting for my Hamshack number to be provisioned, I decided to try connecting my IP phone to my G7RPG microHUB to see if it's possible to use the phone as a "radio" in the shack, using the microHUB's AllStar node to get out on the air.

And this is how I did it.

This guide assumes that you have a spare line/extension available on your IP phone. Some Cisco SPA phones only have one line.

## Disclaimers

!!! warning
    Making changes to any configuration files or settings could b0rk your node and/or phone. Take backups or make detailed notes of what you change *before* you change it.

    Please don't overwrite an existing extension on your phone - particularly if you're using Hamshack Hotline. I'd hate for you to lose access to an existing service by following this guide.

    This is an experimental activity, and therefore not sanctioned. I've cludged these instructions from various sources around the web. Good luck!

    If it all goes wrong once you're set up, disconnect your node (`*73` or via your node's web interface) and hang up the call. Worst case, reboot your node.

## Set up the AllStar node

SSH into your AllStar node, and drop into a shell. If you're using a G7RPG microHUB, it's option 9 from the Admin Menu.

### sip.conf

Edit the file `/etc/asterisk/sip.conf` (using your editor of choice) and add the following to the end of the file.

```ini
[789]
type=friend
host=dynamic
user=789
secret=yoursupersecretpassword
dtmfmode=rfc2833
context=sip-phones
callerid="Your Name" <789>
```

> Change `789` to an number of your choice, but *not* your node number.  This becomes your extension number within Asterisk on your AllStar node.  Keep to 3 digits so as not to clash with Allstar node numbers,

### extensions.conf

Edit the file `/etc/asterisk/extensions.conf` and add the following to the end of the file.

```ini
[sip-phones]
exten => 789,1,Dial(SIP/789,60,rT)
exten => 12345,1,rpt(12345|P)
```

> Change `789` (2 instances) to your extension number from `sip.conf`\
> Change `12345` (2 instances) to your AllStar node number - *this is important!*

### modules.conf

Edit the file `/etc/asterisk/modules.conf` and make sure the following line *does* have a semi-colon (`;`) at the beginning of it. If it doesn't, add one.

```ini
;noload=chan_sip.so
```

It's kinda backwards, but putting the semi-colon at the start of the line prevents the SIP module from not being loaded. i.e. it will make sure that it *is* loaded.

### You're done

Once you've made and saved all of these changes, reboot your node.

## Set up the Cisco SPA500-series phone

For this, you will need the IP address of your IP phone. You may be able to do this from the menu system on the phone itself. For the purposes of this guide, we'll use `192.168.0.70`

Visit your phone's admin page at `http://192.168.0.70/admin/advanced`.

### Configure the SIP service

Click on the tab relating to one of your spare extensions - for example "Ext 4" (which is the one I'm using)

* Under General:
  * ensure that Line Enable is set to "yes"
* Under Proxy and Registration:
  * set Proxy to `192.168.0.81:5060`\
    *(using the IP address of your microHUB/AllStar node)*
  * set Outbound Proxy to `192.168.0.81`\
    *(using the IP address of your microHUB/AllStar node)*\
    *(note the* `:5060` on the first one, but not on the second)
* Under Subscriber Information:
  * set User ID to the extension number you chose in `sip.conf` above, in my example it was `789`
  * set Password to the password you chose in `sip.conf` above, in my example it was `yoursupersecretpassword`
  * set Use Auth ID to `no`

### Configure the phone interface itself

Click on the "Phone" tab in the admin interface, and locate a spare line key. This will be the location of where the link to your node will appear on the phone itself. I chose line 4, because no reason.

* Under Line Key 4:
  * Set Extension to `4`\
    *(or whichever Extension number you chose in the previous step)*
  * Set Short Name to whatever you'd like the text against that Line Key to say.\
    *(Mine says* `Allstar 12345`, based on my example node number, but it can be anything you like, within reason)

### Switch off text messaging (advised)

Click on the "User" tab in the admin interface. This is an optional step. I discovered that my AllStar node would sent a text message to the phone every few seconds, which was incredibly annoying, so this is how to turn it off.

* Under Supplementary Services:
  * Set Text Message to `no`

### And you're done

Once you've made all of the changes you want, click on the [Submit All Changes] button at the bottom of the admin page. This will save your changes and reboot your phone. If all goes well, you'll have a green light against your designated line key on the phone, and an associated description next to it (if your phone supports it).

## Connecting to your AllStar node

1. Pick up your handset, or press the speakerphone key, and then press your new line key. The key should turn red.
2. Dial the number of your node (in my example `12345`). After a short delay, it should show you as connected.
3. You should now be linked with your node, as if you were connected to it over RF using a radio.  You can now use DTMF tones (or your node's web interface) to switch connections:

  * `*73` to disconnect your node
  * `*73*352188` to connect to HUBnet
  * `*73*340894` to connect to HUBnet's Audio Test node
  * etc...

  > (it's good practice to put* `*73` at the start of all of your connection attempts, so you don't end up bridging multiple connections - which could be bad)

4. If you want to key-up, use `*99` to key, and `#` to un-key. You get no audible or visual notification whilst doing this, so experiment on a closed channel first, just so that you get the hang of it. Make use of the Audio Test node (`40894`) so you can test your audio and keying skills. Other users use this node as well, so please make sure you identify yourself as normal.
