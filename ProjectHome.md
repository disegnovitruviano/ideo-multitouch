**Multitouch Package for Flash & Processing** by labs.ideo.com

Created to enable designers to explore multitouch interactions quickly and easily, this package includes all requisite software to build a lightweight multitouch system.

This package is comprised of two parts:

**Multitouch Client** – A multitouch API for Flash including support for extensible touch actions, arbitrarily sized displays, and a limitless number of active fingers. Software simulated touch events are also supported to allow for software to be tested and developed on computers lacking multitouch hardware. The Multitouch Client API is built in ActionScript 2 and communicates with the Multitouch Server via network socket connection.

**Multitouch Server** – There are currently two alternatives for the back-end server:
### FTIR ###
A camera-based computer vision system that optically recognizes multitouch input, serializing it for transmission to the Multitouch Client. It has an interactive calibration routine to effectively overcome camera alignment and fisheye lens distortion. Implemented in [Processing](http://www.processing.org/), it uses open source libraries and Processing's net library.

Originally created for use with popular low-cost DIY [FTIR setups](http://www.cs.nyu.edu/~jhan/ftirtouch/) (see [nuigroup](http://www.nuigroup.com/) for information on assembling your own FTIR hardware), this software can also be easily modified to work with commercially available systems by implementing the Multitouch Server Protocol over a socket server.
![http://sites.google.com/site/ideolabsdocumentation/images/multitouchdiagram.png](http://sites.google.com/site/ideolabsdocumentation/images/multitouchdiagram.png)

### WiiMote ###
A wiiMote based multitouch server which uses the infrared camera in the wiiMote along with hand-held IR lights to track several points.
Information on building suitable light pens is available [here](http://www.kenmooredesign.com/labels/diy.html) and [here](http://ca.rroll.net/2008/05/26/simple-ir-pen-for-wiimote-whiteboard/) and [here](http://procrastineering.blogspot.com/2007/12/ir-led-pen-schematic-and-ir-keychain.html) and you can buy readymade pens [here](http://penteractive.us/?gclid=COW1w7muqpcCFSMgDQodFjlijQ) for $8.

![http://sites.google.com/site/ideolabsdocumentation/images/wiimultitouchdiagram.png](http://sites.google.com/site/ideolabsdocumentation/images/wiimultitouchdiagram.png)


---

**Example Code (Client)**

The following example illustrates how to enable a movieclip to be dragged using one finger or dragged, scaled, and rotated using two fingers. The screenshot below displays this example code as applied to a colored square.

```
import com.ideo.MultiTouch.*;
import com.ideo.MultiTouch.TouchActions.*;

// create finger manager
var fingerManager = new FingerManager(this);

// connect finger manager to finger server
var fingerClient = new FingerClient(fingerManager, "localhost", 11000);

// create finger simulator
var fingerSimulator = new FingerSimulator(fingerManager);

// create touch manager
var touchManager = new TouchManager(fingerManager);

// make movieclip touchable
touchManager.makeTouchable(myMovieClip);

// assign touch actions for movieclip
new OneFingerDragger(myMovieClip);
new TwoFingerManipulator(myMovieClip);
```

Refer to the [project wiki](http://code.google.com/p/ideo-multitouch/w/list) for [class documentation](http://code.google.com/p/ideo-multitouch/wiki/DocumentationActionScript2) and more [sample code](http://code.google.com/p/ideo-multitouch/wiki/ExamplesActionScript2).  Some more complex examples of interfaces built with this package are shown in [this video](http://www.vimeo.com/1506794).

**Multitouch Simulator**

Touch events can be simulated in the Flash environment to allow multitouch software to be developed without or while away from multitouch hardware. Touch events are simulated by way of keyboard chording. The number keys place virtual fingerprints on the stage that can be dragged with the mouse. Visible fingerprints are also useful for debugging multitouch hardware calibration and screen registration.

![http://sites.google.com/site/ideolabsdocumentation/images/multitouchsimulator.png](http://sites.google.com/site/ideolabsdocumentation/images/multitouchsimulator.png)