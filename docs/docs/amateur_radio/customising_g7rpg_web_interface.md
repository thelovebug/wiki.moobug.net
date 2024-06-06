---
title: "How to customise the G7RPG web interface to your own liking"
---

!!! information
    This article was written by operator [Dave M7TLB][QRZ], for the Amateur Radio community.

    Reach out to me via [QRZ][QRZ] for any additions and omissions.

[QRZ]: https://qrz.com/db/M7TLB

## Assumptions

This document assumes that you know how to access the following elements of your G7RPG microHUB, and are therefore out of scope:

* Web interface
* SSH Admin menu, and Bash shell interfaces

## Caution

!!! warning "Here be dragons!"
    You're potentially about to make changes to a key file on your microHUB. If you fluff it up, you may lose access to the web interface. *Caveat emptor!*

## File location

The file that we'll be modifying is at the following location:

* `/srv/http/index.php`

### Back up your file

!!! warning "Backup!"
    I would recommend backing up this file every time you need to make a change to it in case something goes wrong. I'd hate for you to lose access to the web interface. You can carry out a backup of this file using the following command:

* `cp /srv/http/index.php /srv/http/index.backup.php`

Of course, `index.backup.php` can be anything you wish, particularly if you're making cumulative changes and may wish to drop back to a particular point in time. Again, this is out of scope of this document.

## File sections

The `index.php` files is broken up into many sections, most of which are of no interest to us. However, there are two key sections that are of interest, both of which after line 147 (on my microHUB), and starts with the line:

```html
<!-- Command response area -->
```

### Actions

The first section are the actions - i.e. what happens when you click on a given button in the interface?

The first action in the list is likely to be this one:

```js
$('#discoall').click(function() { $.ajax({ url: '/cgi-bin/lsnodes_web?node=99999&command=*73', }); });
```

The node number `99999` should be your Allstar node number in your version of the file.

My advice is not to change any lines that already exist in that section, particularly not the ones towards the top as they are utility functions for the microHUB itself.

Two key parts to each of these lines:

1. `$('#discoall')`  
   The value in the single quotes - in this case `discoall` - must be unique across all of the action lines in this file.  It will be used by the buttons in the next section in the file, so having the same value appear twice could end up with unexpected results.
2. `'/cgi-bin/lsnodes_web?node=99999&command=*73'`  
   The value in the single quotes is the "what happens when this action is invoked" - in this case, it sends the command `*73` to the node, telling it to disconnect your node from all others.  Again, `99999` should be (and needs to be) your own Allstar node number.

The simplest way to add a new action is to duplicate the last line in the list.  If you're using `nano` then that would be to place your text cursor on the line you want to duplicate and press Ctrl-K, Ctrl-U, Ctrl-U.  This effectively cuts the line, and then pastes it back twice.  If you're using another editor, then it's highly likely to be a different action.

For creating a new action:

* change the unique identifier to be the Allstar node you want to connect to\
  *e.g. 42732 for F-troop*
* make sure the `node=` section has *your* Allstar node against it
* change the `command=` section to `*73*342732` \
  *that's* `*73` *to disconnect, followed by* `*3` *which means "connect to" and* `42732` *which is the node you want to connect to*

So your newly created line would look something like this:

```js
$('#42732').click(function() { $.ajax({ url: '/cgi-bin/lsnodes_web?node=99999&command=*73*342732', }); });
```

Where `99999` should be your... blah blah, you get it.

That's the action section done.

### Buttons

These are the coloured buttons that appear in your web interface.

If you scroll slightly down in your `index.php` file, just below the actions, you'll start to see four blocks of HTML, with headers as follows:

1. `<!-- 1 -->`
2. `<!-- 2 -->`
3. `<!-- 3 -->`
4. `<!-- 4 -->`

These headers represent the columns within the web interface.  If you look at the entries within column 1, for example, you'll see the following `<button>` references:

* `discoall` - Disconnect All
* `40894` - Audio Test
* `51288` - HUBnet 51288

And you should notice that these will correspond directly with the first three buttons in the first column of your web interface.

Things to highlight here:

* Each of the column blocks is broken into two by a blank line.  I would recommend not touching anything in the top half of that block, as those are the key functions for the microHUB.
* The `id=` section in the `<button>` statement, relates to the unique reference in the action above.  So the browser knows that when that button is clicked, it will carry out the action with that `id`.
* `<br>` means "line break", so it allows you to put your description on multiple lines
* The `class=` section in the `<button>` statement determines the colour of the button:
  * `buttonr` = red
  * `buttonb` = blue
  * `buttong` = green
  * `buttono` = orange
  * `buttongr` = grey (not really used, I believe)

Therefore, for the F-troop example that I highlighted in the actions section above, you would enter the following line at whatever position of whichever column you want it to appear:

    ```html
    <button class="buttong" id="42732">VK6-HUB F-troop<br />VK6RX<br />42732</button>
    ```

This would put a green button, which executes action "42732" (connect to F-troop), with the label:

> VK6-HUB F-troop  
> VK6RX  
> 42732

... on the button itself.

As before, I would recommend you duplicate an existing line rather than try and hand-craft your own, but that's entirely down to you.

You might want to duplicate one of the `bspace` lines to tidy up the layout of the page, but that's aesthetics and doesn't affect the functionality of the interface itself.

Once you've saved the file, the changes should appear the next time you refresh the microHUB home page.
