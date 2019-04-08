Volume Haptics Toolkit
==================

## Overview ##

The Volume Haptics Toolkit, VHTK for short, was developed during a research project aiming at bringing
haptics into volume data exploration interfaces and the volume data understanding process. During
this project the algorithms needed for both simple and effective volume haptics were designed and the
primary interface for VHTK was formed. The toolkit extends H3D API by introducing the scene-graph
nodes necessary for loading volumetric data, handling and processing the data and for using the data to
produce both visual and haptic feedback.

VHTK has been designed ground up to make full use of the features provided by H3D API. Thus, the
toolkit can be use in all three design levels of H3D API — structural design using X3D, interactive
dynamics using Python scripting and low-level setup and extensions in C++. Also the event handling
system is highly integrated in the functionality of VHTK. Changes in fields controling, for example,
filters propagates an event to every node involved, forming a conceptual multi-modal data pipeline,
similar to those of Visualization Toolkit, VTK, and AVS/Express.

## Releases ##

The latest release of Volume Haptics Toolkit is version 1.12.0 for H3D API.

Submitted:   Fri, 18-Nov-2016  

## Author ##
VHTK has been developped and submitted by Karljohan E. Lundin Palmerius.  
http://webstaff.itn.liu.se/~karlu20/

## License ##
This project is licensed under the GNU GPL license.
