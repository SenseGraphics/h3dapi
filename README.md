README
==================

## Overview ##

H3D API is an open-source, cross-platform, scene-graph API.
H3D is written entirely in C++ and uses OpenGL for graphics rendering and HAPI for haptics rendering.

HAPI is an open-source, cross-platform, haptics rendering engine written entirely in C++. 
It is device-independent and supports multiple currently available commercial haptics devices. You can write your
application once and not have to modify any code to use another haptics device. Choose between different
rendering algorithms, different force effects and several kinds of surfaces to create the feeling that you
want or create your own custom made effects.
HAPI has been designed to be a fully modular haptic rendering engine, allowing users to easily add,
substitute or modify any component of the haptics rendering process.


## H3D Releases ##

This is the 2.1.1 version of H3D API.

Released on: Tue, 06-Apr-2010

## Changelog ##
This release contains fixes for bugs found in H3D 2.1.0.

### Changes for version 2.1.1 of H3DAPI: ###
- CMake updates for handling builds with Visual studio 2010 and CMake 2.8.0. Still considered test-verison since Visual studio 2010 is not released yet.
- Various minor bug fixes.
- Exported some more classes. In case some application needs it.
- Added clear button to console dialog of H3DViewer.
- Added reload menu and some keyboard shortcuts to H3DViewer.
- Varios other updates to H3DViewer.
- Memory leak fixes.
- Updates to compile on 64 bit ubuntu and gcc 3.1.1.
- Added collision detection functions for Lod and Switch.
- ClipPlane now works properly for lineIntersect functions.
- Fix to nrrd loader in order to not accidently load jpg files using nrrd loader.
- Updates which improves haptics layers performance.
- Fog behaviour now matches X3D specification.
- FogCoordinate now works.
- Updates to work properly with FTGL 2.1.3 if that is used (default on latest ubuntu release).
- Improvements to CMake system which groups variables belonging to a certain external library. Makes it easier to find these when setting manually.

### Changes for version 2.1.1 of H3DViewer standlaone for Windows: ###
- Added clear button to console dialog.
- Added reload menu and some keyboard shortcuts.
- Memory leak fixes.

### Changes for version 1.1.1 of HAPI: ###
  - CMake support for OpenHaptics 3.0.
  - Memory leak fixes.
  - Various bug fixes in the renderers.
  - Updates to compile for Visual Studio 2010 and gcc 3.1.1.
  - PhantomHapticsDevice now reports usable work space in meters.
  - CMake build updates. Variables that points to include directories and libraries are now grouped together for each external library.
