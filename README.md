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

This is the 2.3.0 version of H3D API.

Released on: Fri, 13-Jun-2014

## Libraries ##
Here follows a description of each library and their changes.
- [H3DAPI](#H3DAPI)
- [H3DUtil](#H3DUtil)
- [HAPI](#HAPI)
- [H3DPhysics](#H3DPhysics)
- [MedX3D](#MedX3D)
- [UI](#UI)

### H3DAPI ###
#### Changes for version 2.3 of H3DAPI: ####
- Generated header is moved to CMake build directory and can only be found in H3DAPI/include after INSTALL project has been built.
- Speed optimizations that could affect some compilers.
- Updates to CMake build system to build properly when TortoiseSVN is installed but the current H3D build is not a TortoiseSVN checkout.
- Added a InstallH3DAPIAndExternals.cmake package file which can be used by applications to package up needed files by the current H3DAPI build.
- Added profiling of haptics and graphics thread if built with profile support. Profiling is not enabled in the released binaries.
- A lot of performance improvements. H3DAPI should render faster in many cases now.
- Scene::findNode* functions now handle Inline. FindNode* functions are now static.
- Updates to fix artifacts with GPU shadows.
- X3DTextureNode nodes can now have their current state saved as PNG.
- Fixed issues with QUAD_BUFFERED_STEREO.
- Updates to handle protos better.
- If GLUT gameMode is used then GLUTWindow now still handle keyboard inputs properly.
- Many updates to FrameBufferTextureGenerator. Such as setting local NavigationInfo, handling shadows, support for new DEPTH_BUFFER types and support for external color and/or depth buffer for buffer storage. It should also now work properly with QUAD_BUFFERED_STEREO mode.
- Memory leak fixes.
- Some field types had unitialized default values, this is fixed now.
- Added optional COPY option for USE statement. Can be useful when there are nodes which does not handle the DEF/USE system that well.
- Use F11 to switch to/from fullscreen in H3DLoad.
- Renamed FindTeem.cmake to FindH3DTeem.cmake in order to use CMakes new FindTeem module if it exists. Did the same for FindFreeType.cmake.
- DirectShowDecoder now plays wmv files.
- PointSet, LineSet, IndexedLineSet now have vertex attribute support.
- Doxygen documentation now links to python documentation as well.
- Extrusion now calculates normal per triangle face instead of per quad face.
- Improved the static and dynamic database so getField function is now faster.
- H3DWindowNode has a takeScreenShot static function.
- Made it possible to put multiple objects in a ShadowTransform node.

New H3D nodes:
- FBODebugger
- GaussianFilterShader
- GeometryGroup
- PlaybackDevice
- NoiseTexture
- NoiseTexture3D
- RazerHydraSensor
- SimpleAudioClip

New python functionality:
- Added getTypeName, getValueAsString, setValueAsString, setName, getName, getFullName, isUpToDate, upToDate, replaceRoute, replaceRouteNoEvent, unrouteAll, getOwner and setOwner functions for fields.
- Added takeScreenshot and findNodes function.

H3DViewer updates:
- Can now copy current log text to clipboard.
- Added dialog to show profiling information if profiling is enabled.
- TreeViewer only expand X3DGroupingNode at first view now.
- QUAD_BUFFERED_STEREO should work properly again.
- Updates to handle QUAD_BUFFERED_STEREO on an NVIDIA_3DVISION ready display with a non-quadro card. Note that this requires a special built wxWidgets. WxWidgets adopted a patch supplied by us so in the future this should work for standard releases of WxWidgets.
- Faster startup due to optimizations.

Compatability issues:
- Changed default depth buffer type of FrameBufferTextureGenerator.
- Not binary compatible due to changes to database and inheritance for some nodes.
- ShadowTransform::shadowVolume is now of MFNode type, was SFNode.
- Fields beamWidth and cutOffAngle in SpotLight node now have default values which makes sense as per update of X3D specification 3.3.


### H3DUtil ###
H3DUtil is a utility library from the makers of H3DAPI. It is the library used by HAPI 1.3. H3DUtil documentation is avaliable at the documentation page.

#### Changes for version 1.3 of H3DUtil: ####
- Generated header is moved to CMake build directory and can only be found in H3DUtil/include after INSTALL project has been built.
- Added profiling capabilities through H3DTimer.
- Renamed FindTeem.cmake to FindH3DTeem.cmake in order to use CMakes new FindTeem module if it exists.
- Speed optimizations that could affect some compilers.
- Fixes to properly remove threads in all cases.
- Added a InstallH3DUtilAndExternals.cmake package file which can be used by applications to package up needed files by the current H3DUtil build.
- Properly pack ACKNOWLEDGMENTS file.
- Memory leak fixes.
- Added CMake option to include visual leak detector in H3DUtil.
- Updates to CMake build system to build properly when TortoiseSVN is installed
but the current H3D build is not a TortoiseSVN checkout.
- Added enable/disable functions in Console which allow thread-safe disabling of console output.

New classes:
- H3DTimer

New functions:
- saveFreeImagePNG
- Image::setByteAlignment

### HAPI ###
HAPI is a haptics rendering C++ library from the makers of H3DAPI. It is the library used by H3DAPI 2.3 but can be used separately. HAPI documentation is avaliable at the documentation page.

HAPI should be used when developing haptics applications (when H3DAPI is not desired). It is a modular library and is easily customized to the developers requirements.

#### Changes for version 1.3 of HAPI: ####
- Generated header is moved to CMake build directory and can only be found in HAPI/include after INSTALL project has been built.
- Speed optimizations that could affect some compilers.
- Updates to CMake build system to build properly when TortoiseSVN is installed but the current H3D build is not a TortoiseSVN checkout.
- Added profiling of haptic thread.
- Moved fparser to be included as stand alone library.
- Added a InstallHAPIAndExternals.cmake package file which can be used by applications to package up needed files by the current HAPI build.
- Improved thread safety of GodObjectRenderer and RuspiniRenderer.
- Fixed crashes on Windows caused by trying to use PhantomHapticsDevice on a system without OpenHaptics.

New classes:
- PlaybackHapticsDevice

### H3DPhysics ###
H3DPhysics is a cross-platform implementation of the Rigid body physics component of X3D for use with H3D API. This version of H3DPhysics is tested against H3D API 2.3.0.

This toolkit used to be named RigidBodyPhysics.

H3DPhysics add rigid body physics models for use in H3D API. Which means that the user can build scenes in which object behave in a physically correct manner. Rigid body physics means that the objects are treated as solid, unchangeable sets of mass with a velocity. These bodies can be connected with the use of various form of joints, that allow one body's motion to affect another.

H3DPhysics for H3D API use ODE (Open Dynamics Engine) for Rigid body physics by default but can also be compiled with support for PhysX or Bullet as physics engines. Also support for PhysX3 is implemented.

For soft body physics Bullet is default. PhysX can also be used.

#### Changes for version 1.3 of H3DPhysics: ####
- Generated header is moved to CMake build directory and can only be found in H3DPhysics/include after INSTALL project has been built.
- Speed optimizations that could affect some compilers.
- Updates to CMake build system to build properly when TortoiseSVN is installed but the current H3D build is not a TortoiseSVN checkout.
- Updates to build on MinGW.
- Memory leak fixes.
- Doxygen documentation now links to python documentation as well.
- Fixes to handle sliderJoint better for most physics engines.
- Fixes to CollisionSpace and ODE.
- Changed signature of some callback functions that are never used as callbacks. They now have return type void.
- IndexedHexaSet, IndexedTetraSet, IndexedPointSet and IndexedElementSet are now more properly implemented and behaves like for example IndexedTriangleSet when it comes to colors, normals and texture coordinates.
- The SoftBody node no longer assumes that its geometry is of type IndexedTetraSet but accepts all nodes with coord and index field.

New fields:
IndexedTetraSet::renderMode
SliderJoint::sliderForce
- H3DSoftBodyLoader::filename is now H3DSoftBodyLoader::url and is an MField. filename can be used a while longer at X3D level. On C++ level it can not.
CollidableShape::clipPlanes
CollisionCollection::collidableExceptionGroups

New nodes:
CollidableExceptionGroup

### MedX3D ###
Source package for the toolkit MedX3D 1.4. Source builds against H3DAPI 2.3.0.

MedX3D is an implementation of Volume Rendering component of X3D.

MedX3D contains nodes for visual rendering of volume data, such as medical data from CT/MRI-scans. A correct X3D file using X3D volume rendering component nodes must specify a volume data node, a volume style node and the data for which to apply this style.
The existing volume data nodes are:
- VolumeData
- SegmentedVolumeData
- IsoSurfaceVolumeData

The styles to choose from are:
- BlendedVolumeStyle.
- BoundaryEnhancementVolumeStyle
- CartoonVolumeStyle
- ComposedVolumeStyle
- EdgeEnhancementVolumeStyle
- ISOSurfaceVolumeStyle
- MIPVolumeStyle, deprecated, use ProjectionVolumeStyle instead.
- OpacityMapVolumeStyle
- ProjectionVolumeStyle
- ShadedVolumeStyle
- SilhouetteEnhancementVolumeStyle
- ToneMappedVolumeStyle

The formats for volume data supported by MedX3D toolkit are:
- raw
- DICOM
- nrrd

MedX3D also supports preintegrated volume rendering, cubic filtering and stochastic jittering.

The MedX3D toolkit also contains various extra nodes not specified in the specification for the volume rendering component, such as an implementation of the Marching cubes algorithm and various nodes to extend the functionality of MedX3D.

MedX3D does not contain any specific haptic features.

#### Changes for version 1.4 of MedX3D: ####
- Generated header is moved to CMake build directory and can only be found in MedX3D/include after INSTALL project has been built.
- Speed optimizations that could affect some compilers.
- Updates to CMake build system to build properly when TortoiseSVN is installed but the current H3D build is not a TortoiseSVN checkout.
- Memory leak fixes which added some functions.
- Fixed MultiVolumeRaycaster since it had quite a few bugs in it.

Removed fields:
- Removed multiVolumeRayCaster::depthTexture field due to it being a forgotten debug output which no longer affected anything.

### UI ###
This is the source package of UI 2.3.0. It is compatible with H3DAPI 2.3.0. It contains the source code needed to build the UI. Cross platform, works on Windows/Linux/Mac OS.  
It is a collection of nodes that can be used to add a haptic user interface in a H3D scene.

Allow for creation of buttons, slider bars etc touchable by haptics device or mouse..

#### Changes for version 2.3 of UI: ####
- Generated header is moved to CMake build directory and can only be found in UI/include after INSTALL project has been built.
- Speed optimizations that could affect some compilers.
- Updates to CMake build system to build properly when TortoiseSVN is installed but the current H3D build is not a TortoiseSVN checkout.
- Renamed FindFreeType.cmake to FindH3DFreetype.cmake in order to use CMakes new FindFreetype module if it exists.

