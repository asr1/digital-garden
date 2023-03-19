---
{"dg-publish":true,"permalink":"/software-and-technology/stop-responding-to-mouse-up/","tags":["software"],"noteIcon":3}
---


# Stop Responding to mouse up!

There's a common pattern in (especially) web UI where a fake popup appears on screen. Often this popup asks you to enter credentials, like an email address or contact information.

If you click outside of the popup, it dismisses, as it should.

But I'm begging you.

Please. 

Only listen for mouse down AND mouse up outside of the box.

I cannot count the number of times where I have tried to select the default text in a popup, only to move my mouse a couple pixels too far and have the popup dismiss itself, losing all of my data.

If you *are* going to listen for mouse-up, at least prompt the user that their data will be lost if they continue before just throwing it all away.
