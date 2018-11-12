oadrive - The Open Autonomous Driving Package
===========================================================

Made by FZI IDS/TKS. http://www.fzi.de

Please consider the license information provided with this repository.
You should have received a copy [LICENSE](LICENSE).


**This Readme is currently outdated. We released version 4.0 of the code, used by Team AlpaKa in the Audi Autonomous Driving Cup 2018. The code can be used. The documentation will be updated after the competition.**


This package provides basic autonomous driving functionalities
with only little dependencies to quite common open source libraries. It is mainly used by student teams participating in the Audi Autonomous Driving Cup, e.g. Team KACADU 2016 (https://github.com/fzi-forschungszentrum-informatik/aadc2016) and Team KATANA 2015 (https://github.com/KAtana-Karlsruhe/AADC_2015_KAtana).

Besides this main package a lot of additional material as well as publications describing the code and supplementary simulation frameworks can be found on the official website:

**Please visit [Audi Autonomous Driving Cup at www.fzi.de](http://url.fzi.de/aadc)**

**A docker image for quick start is available now! Please follow the instructions at https://hub.docker.com/r/fziispetks/oadrive/**

Core funtionality
-----------------------------------------------------------
The package is used to control electrical model cars in the
AADC (Audi Autonomous Driving Cup). It attempts to abide to
the rules defined for the Cup.


Dependencies
------------------------------------------------------------
- OpenCV:
    - At least Version 3.0 recommended. 2.4.11 is supported,
      but some features will be deactivated (mainly the semi-
      automatic camera calibration).
- Aruco (optional, but highly recommended) (https://downloads.sourceforge.net/project/aruco/OldVersions/aruco-1.3.0.tgz)
- redisclient (optional) (https://github.com/nekipelov/redisclient)
- icMaker (https://github.com/fzi-forschungszentrum-informatik/icmaker)
- icl_core (https://github.com/fzi-forschungszentrum-informatik/icl_core)


Installation
-------------------------------------------------------------
Build and install OpenCV, Aruco, redisclient. Use icmaker to create
a workspace including icl_core and oadrive. See
https://github.com/fzi-forschungszentrum-informatik/icmaker for
more information.


Usage
------------------------------------------------------------
The package can be built independently of the ADTF development
environment (which is required by the AADC).
We defined an Interface class (oadrive_interface/Interface.h).
All communication with oadrive must be passed through this
interface.
For example usage, see src/test/test_oadrive_interface.cpp.

This allows the package to be used from within other contextes
as well, like an offline simulation.
If Interface::startDebugDumping() is called at startup, the
Interface will write out debug data which can then be used for
offline configuration.


Calibration
-------------------------------------------------------------
Proper usage of the package requires calibration of the camera.
This camera calibration calculates a Bird-View perspective
transformation using a Matrix-Of-Circles pattern.
Use test_oadrive_birdViewCal.cpp to do the calibration.
Beforehand, the intrinsic camera calibration must be saved to
a file (which is then passed to the test_oadrive_birdViewCal).
