---
title: Reach
description: A python library that provides Apple's objective-c reachability.
author: J. Matt Peterson
created:  2013 Mar 19
modified: 2013 Mar 19

---

reach
=====

Python is now reachable. A python library that provides Apple's
objective-c reachability.

Install
-------

```bash
pip install -e git+git://github.com/jmatt/reach.git#egg=reach 
```

Use
---

```python
from Foundation import NSNotificationCenter
from AppKit import NSLog, NSObject, NSWorkspace
from reach.Reachability import Reachability, kReachabilityChangedNotification

reachability = Reachability()

class ReachabilityHandler(NSObject):
    """
    Handle reachability notifications from the network.
    """
    def handleChange_(self, notification):
        """
        Handle Reachability changes here.
        """
        NSLog("change!")

rhandler = ReachabilityHandler.new()

workspace = NSWorkspace.sharedWorkspace()
default_center = NSNotificationCenter.defaultCenter()
default_center.addObserver_selector_name_object_(
            rhandler,
            "handleChange:",
            kReachabilityChangedNotification,
            None)
reachability.startNotifier()
```

Tasks
-----

- [X] Move Reachability to it's own library.
- [ ] Implement additional functionality from [Apple's Reachability code](http://developer.apple.com/library/ios/samplecode/Reachability/Listings/Classes_Reachability_m.html).
