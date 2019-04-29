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

This is the 2.4.0 version of H3D API.

Released on: Mon, 29-Apr-2019

## Libraries ##
Here follows a description of each library and their changes.
- [H3DAPI](#H3DAPI)
- [H3DUtil](#H3DUtil)
- [HAPI](#HAPI)
- [H3DPhysics](#H3DPhysics)
- [MedX3D](#MedX3D)
- [UI](#UI)

### H3DAPI ###
#### Changes for version 2.4.0 of H3DAPI: ####
- Added removeField functionality for dynamic nodes (ComposedShader).
- Added mip map filtering choices in TextureProperties.
- Performance improvements and added flags in CMake that can be used for
  optimizing performance of releases.
- Shadow improvements. Both in the normal case and also added a multi threaded
  option for calculating shadows.
- Support for exr images.
- Made metadata nodes a bit more useful.
- Added possibility of setting max frame rate for Scenes.
- Added new stereo render mode VERTICAL_SPLIT_KEEP_ASPECT_ONE_PASS, also
  referred to as single pass stereo rendering.
- Added support for bindless textures.
- Added support for direct state access, scissor box to limit rendering,
  stencil masking feature and a new value called 2D_MULTISAMPLE_ARRAY
  ( layered rendering of textures ) for outputTextureType field
  in FrameBufferTextureGenerator.
- Updates to DeviceLog and PlaybackDevice.
- ImageObjectInfo can now also be used for all H3DImageObject inherited classes
  instead of only X3DTexture3DNode.
- Added sRGB texture format in TextureProperties.
- Added option to share data between textures that use the same url.
- Added a couple of more default sections to be included when profiling.
- Fixes to compile for visual studio 2015 and 2017.
- Added SKIN_DLB to renderMode of HAnimHumanoid which can be used to get a
  different (better) skinning by using Dual Quaternion.
- Renamed many CMake cache variables and added functions to make it easier
  to setup H3D projects in similar fashions.
- Added CMake functionality for handling external checkouts that contain
  subdirectories built for different visual studio versions.
- Updates to increase the robustness of the implementation of python support.
- Added GL_R16, GL_R16F, GL_R32 and GL_R32F in texture nodes.
- Added support for texture compressed methods and file formats.
- Tesselation shader support for LineSet.
- Various bug fixes for url resolving.
- Fixed issues with syncing to the haptics thread and destruction of data.
- All kinds of H3DImageObjects and not just X3DTexture2DNode are allowed in
  HapticTexturesSurfaces node.
- Added support for precompiled headers.
- X3DTexture3DNode nodes can now have their current state saved as nrrd.
- Using a tesselation shader no longer disables haptics for that node. Although
  the haptic triangles will be calculated from the non-tesselated geometry.
- ImportLibrary now appends _vc suffix (on windows) automatically as fallback
  when trying to load dlls.
- Added Oculus rift stereo mode.
- Added support for vibration feature and auto calibration to
  ForceDimensionDevice. Gripper angle can now also be obtained.
  Desired communication rate between haptics device
  and haptic thread can be set.
- Added reading of angular velocity for H3DHapticsDevice.
- Exposing encoder values and adding access to inkwell status of PhantomDevice.
- Added field to scale force output in H3DHapticsDevice outside of
  calibration matrix.
- Added fields in GodObjectRenderer for more control over its behaviour.
- Fixed issues with PlanarReflector.
- Added support for automatic calibration of ForceDimensionDevice.
- Can now use field faceSize to set the font size in points in Fontstyle node.
- Fixed many compile warnings.
- Added a way to specify a local python virtual environment for H3DLoad and H3DViewer.
- Made it possible to use an NVSettings.x3d node to force specific graphics card
  settings for an application using H3D.

New H3D nodes:
- Capsule
- ClutchedDevice
- DDSImageLoader
- OpenEXRImageLoader
- MFNodeSplitter
- OculusRiftSensor
- ShaderImage2D
- ShaderImage3D
- ShaderChildNode
- ShaderConstants
- ShaderImageNode
- ShaderStorageBuffer
- ShaderAtomicCounter

Fields exposed on X3D level for existing nodes:
- useDSA, useSpecifiedClearColor, clearColor, useScissor, scissorBoxX, scissorBoxY,
  scissorBoxWidth, scissorBoxHeight, clearColors, nrLayers, splitScene,
  projectionWidth, projectionHeight, generateStencilMask, applyStencilMask and
  useInverseMasking in FrameBufferTextureGenerator.
- loadInThread in Image3DTexture and ImageTexture.
- deadmansSwitch, deviceAngularVelocity, trackerAngularVelocity and
  forceScale in H3DHapticsDevice.
- close in DeviceLog.
- width, height, widthInUse and heightInUse to ConvolutionFilterShader
  and GaussianFilterShader.
- bindlessTextures, bindlessTexturesUnusedTime, shareTextures,
  maxTextureDimension and textureCompression in GraphicsOptions.
- transparency, saveToUrl and saveSuccess to FBODebugger.
- enabled in H3DShadowObjectNode.
- elapsedTime in SimpleMovieTexture.
- swapEyes in StereoInfo.
- pointingDeviceRefreshMode and resetViewPoint in H3DWindowNode.
- angularSpeed in X3DParticleEmitterNode.
- set_pauseDeviceTransform and set_secondaryButton in H3DFakeHapticsDevice.
- printShaderWarnings in ComposedShader.
- pointSize in PointSet.
- enableForce, vibrationFrequency, vibrationAmplitude, gripperAngle,
  autoCalibrate, isAutoCalibrated, desiredComThreadFrequenc and gripperForce.
  to ForceDimensionDevice.
- gripperAngle, set_gripperAngle and gripperForce to FakeHapticsDevice.
- instanceCount in IndexedTriangleSet.
- centerOfMass in X3DGeometryNode.
- shaderString in ShaderPart.
- encoderValues and inInkwell in PhantomDevice.
- minDistance and enableSecondaryCollisions in GodObjectRenderer.
- faceSize in FontStyle node.

New python functionality:
- addURNResolveRule, exportGeometryAsSTL and log functions added.
- Python scripts used with PythonScript node can now implement an
  onExit function.
- isValidValue and getValidValues functions of SFString field.
- closestPoint, lineIntersect, removeField and clearField functions
  added for nodes.

H3DViewer updates:
- Added functionality to control expansion of nodes in tree viewer by using
  metadata nodes.
- Added LookAt right click menu item to center at nodes using the tree viewer.
- Added search functionality to tree viewer.
- Profiling of groups in H3DViewer tree viewer is added.
- The environment variable H3D_CONSOLE_LOGFILE can now be used to log console
  output to a file.
- Added image viewer window for tree viewer.
- Added a python console which can be used to set fields and do other
  operations on the currently loaded scene in real time.
- New command line options for H3DViewer, screen, window_position, rendermode,
  fullscreen, no_border, no_menu,  silent and logInitTime.
- Added support for environment variable H3D_RENDERMODE to set the stereo
  mode for H3DViewer.
- Added separate tabs for warnings and error messages in console window.
- Added setting to automatically align treeview and console around main
  window.
- Now allowed to show child windows when fullscreen.
- Autocomplete to find nodes when adding nodes into scene graph.
- Updates for visualizing node references as a debug feature.

Compatibility issues:
- X3DPointingDeviceSensorNode::onIsOver virtual function has changed (extra argument).
- Texture nodes inheritance
- Shadow nodes inheritance.
- Removal of using std in some headers means adding std:: in headers that
  previously relied on H3DAPI includes using std.
- MField::setValueFromVoidPtr now take const void * as input instead of void *
- SField::setValueFromVoidPtr now take const void * as input instead of void *
- Minimum supported visual studio compiler is now Visual Studio 2010.
- TriangleSet::AutoNormal::generateNormalsPerVertex is now named
  generateNormalsPerFace.
- Deprecated H3D_USE_DEPENDENCIES_ONLY used in CMake configuration. Replace
  by checking existing targets.
- Many CMake cache variables are now deprecated. Warnings should give
  instructions on what to do about them.
- GraphicsCachingOptions is now removed.
- One of the constructors for H3DDynamicFieldsObject is now removed.
- Fixed an issue with the NurbsCurve geometry ignoring the last control point.
- X3DEnvironmentTextureNode::cube_map_id is removed and
  H3DSingleTextureNode::texture_id is used instead.
- Previously a variable in PythonScript that pointed to a parent of the PythonScript
  node in the hierarchy could cause circular references. Now storing a field of such
  a parent will also cause circular references. The reason is due to fixing crashes
  caused by getting the value of a field that is contained in a temporary node.
- X3DSoundSourceNode::sound_buffer is now named X3DSoundSourceNode::soundBuffer
- FrameBufferTextureGenerator::resetPrintedFlag class is now named
  ResetPrintedFlag
- FrameBufferTextureGenerator::resetPrintedFlags class is now named
  ResetPrintedFlags
- HAnimHumanoid::joint_matrix_changed is now named jointMatrixChanged.
- PlaybackDevice::playback_url_changed is now named playbackURLChanged
- PlaybackDevice::default_values_changed is now named defaultValuesChanged

Deprecated code:
- H3DHapticsDevice::PosCalibration field template.
- H3DHapticsDevice::OrnCalibration field template.
- H3DWindowNode::takeScreenShot replaced with H3DWindowNode::takeScreenshot.


### H3DUtil ###
H3DUtil is a utility library from the makers of H3DAPI. It is the library used by HAPI. H3DUtil documentation is avaliable at the documentation page.

#### Changes for version 1.4.0 of H3DUtil: ####
- Added support for exr images.
- Asynchronous callbacks are now potentially executed earlier when
  being added to the thread.
- Fixes to compile for visual studio 2015 and 2017.
- Renamed many CMake cache variables and added functions to make it easier
  to setup H3D projects in similar fashions.
- New Image pixel type R.
- Added CMake functionality for handling external checkouts that contain
  subdirectories built for different visual studio versions.
- Updates to console to make it output more useful log messages.
- Fixed many compile warnings.
- Added support for loading compressed image data (DDS) from both files
  and input streams.
- Improved reading of nrrd files.
- Added support for using NVidia NSight for profiling.
- Added a threadpool that can be used to limit number of threads.
- Timestamps now use a nanosecond resolution timer on Linux instead of a microsecond resolution timer.
- Added CMake option to enable Visual Leak Detector for release builds.
- CMake fixes to support fastbuild.

New classes:
- DualQuaternion
- ThreadPool

New functions:
- epsilonCompare
- H3DClamp
- H3DSqr
- inverseSafe function in matrix classes.
- loadDDSImage
- loadOpenEXRImage
- nearEqual in all linear algebra types.
- saveOpenEXRImage
- Image::setAllPixels

Compability issues:
- Removal of using std in some headers means adding std:: in headers that
  previously relied on HAPI includes using std.
- Several CMake cache variables have been replaced with new ones.
- Deprecated H3D_USE_DEPENDENCIES_ONLY used in CMake configuration. Replace
  by checking existing targets.
- Many CMake cache variables are now deprecated. Warnings should give
  instructions on what to do about them.
- Previously deprecated constructor for SimpleThread is now removed.

### HAPI ###
HAPI is a haptics rendering C++ library from the makers of H3DAPI. It is the library used by H3DAPI but can be used separately. HAPI documentation is avaliable at the documentation page.

HAPI should be used when developing haptics applications (when H3DAPI is not desired). It is a modular library and is easily customized to the developers requirements.

#### Changes for version 1.4.0 of HAPI: ####
- Updates to minimize the sync time for transfer of new haptics data.
- Fixes to some collision functions.
- Renamed many CMake cache variables and added functions to make it easier
  to setup H3D projects in similar fashions.
- Added CMake functionality for handling external checkouts that contain
  subdirectories built for different visual studio versions.
- Improved DeviceLog and PlaybackHapticsDevice in many ways.
- Fixes to compile for visual studio 2015 and 2017.
- Fixed many compile warnings.
- HLThread updates to fix potential OpenHaptics crashes.
- std namespace is not included into global namespace in HAPI anymore
- Added possibility for user to make force effect instance
  creation/destruction thread safe.
- Added functions to ForceDimensionDevice to enable/disable force as
  well as setting vibration.
- Fixes to OpenHapticsRenderer matrix push/pop.
- Corrections to correctly handle rotation for different devices from
  ForceDimension.
- Fixes to use drd lib instead of dhd lib for ForceDimension
  if that is desired.
- Added support for precompiled headers.
- Updates to handle torque better.
- Added support for handling several buttons for ForceDimensionDevice.
- CMake fixes to support fastbuild.
- Now exposing encoder values for PhantomHapticsDevice.
- Added force scaling to devices.
- Made it possible to get and set minimum distance used between proxy
  and surface in GodObjectRenderer.
- Added option to include secondary collision pass in GodObjectRenderer
  to fix certain fall through issues.
- Added autocalibration feature to ForceDimensionDevice.
- Added a way to set communication thread frequency between HAPI and
  ForceDimensionDevice. Or to simply disable it and do communication
  directly in the haptics thread.
- It is now possible to check if a phantom device is in the inkwell.
- Added dof7_angle and dof7_force to HAPIHapticsDevice. For
  ForceDimensionDevice this would correspond to a gripper for those
  devices that have this.

New classes:
- ClutchedHapticsDevice

Compability issues:
- The close function of DeviceLog is now meant to be called outside the
  haptics thread.
- std namespace is not included into global namespace in HAPI anymore
- Deprecated H3D_USE_DEPENDENCIES_ONLY used in CMake configuration. Replace
  by checking existing targets.
- Many CMake cache variables are now deprecated. Warnings should give
  instructions on what to do about them.

### H3DPhysics ###
H3DPhysics is a cross-platform implementation of the Rigid body physics component of X3D for use with H3D API.

H3DPhysics add rigid body physics models for use in H3D API. Which means that the user can build scenes in which object behave in a physically correct manner. Rigid body physics means that the objects are treated as solid, unchangeable sets of mass with a velocity. These bodies can be connected with the use of various form of joints, that allow one body's motion to affect another.

H3DPhysics for H3D API is a wrapper around existing physics engines such as ODE, Bullet and PhysX3.

This toolkit used to be named RigidBodyPhysics.

For soft body physics Bullet is default. PhysX can also be used.

#### Changes for version 1.4.0 of H3DPhysics: ####
- Renamed many CMake cache variables and added functions to make it easier
  to setup H3D projects in similar fashions.
- Added CMake functionality for handling external checkouts that contain
  subdirectories built for different visual studio versions.
- Fixed many compile warnings.
- Added PID controller nodes for better coupling to haptics and also added
  some node to control collidables.
- Added more options to control the PhysX3 implementation.
- It is now possible to trigger rendering of collidables. Supposed to be
  used for debugging purposes.
- PhysX3 nodes have been much improved.
- Added support for precompiled headers.
- Added support for unity build.
- Bullet nodes have been much improved, new collision models, various
  bug fixes and more.
- Improved TriangleSetMapping
- Memory optimization with collidable shape.
- Some memory leak fixes for the bullet implementation.
- PhysX3CollidableOptions::convex field now has the same default value
  (true) as when there is no PhysX3CollidableOptions for a CollidableShape.
- PhysX3CollidableOptions can now be used to set contact reporting mode per
  collidable.

New fields:
- BulletRigidBodyOptions::softBodyCollisionOptions
- BulletSoftBodyOptions::collidesWith
- BulletSoftBodyOptions::collisionGroup
- BulletSoftBodyOptions::poseMatchingCoefficient
- BulletSoftBodyOptions::poseMatchingFrame
- BulletSoftBodyOptions::poseMatchingVolume
- BulletSoftBodyOptions::softKineticHardness
- BulletSoftBodyOptions::softRigidHardness
- BulletWorldOptions::collisionMargin
- BulletWorldOptions::maxVelocityAngular
- BulletWorldOptions::maxVelocityLinear
- CollidableShape::updateShapeBounds
- CollisionCollection::contactReportMode
- CollisionCollection::collidableSelectionGroups
- PhysX3CollidableOptions::contactOffset
- PhysX3CollidableOptions::resetOffset
- PhysX3CollidableOptions::setFlagsForAll
- PhysX3CollidableOptions::suppressDisabledContacts
- PhysX3CollidableOptions::contactShaderPairFlags
- PhysX3RigidBodyOptions::createAsStatic
- MassSpringPhysicsMaterial::stiffnessAngular
- MassSpringPhysicsMaterial::stiffnessVolume
- RigidBodyCollection::renderCollidables
- RigidBodyCollection::renderOnlyEnabledCollidables
- RigidBodyCollection::useStaticTimeStep
- RigidBodyCollection::syncGraphicsFrames
- RigidBodyCollection::syncPhysicsFrames
- SingleAxisHingeJoint::bias
- SingleAxisHingeJoint::softness

New nodes:
- ArticulatedRigidBody
- BodyPID
- CollidableSelectionGroup
- DistanceJoint
- JointPID
- PhysX3Joint6DOFLimitOptions
- PhysX3JointOptions
- PhysX3SliderJointOptions
- PIDCollection
- PIDController

Deprecated features:
- Cloth::SFX3DComposedGometryNode is now Cloth::SFX3DComposedGeometryNode.

Compatibility issues:
- Config.h and Config.cpp is now H3DPhysics.h and H3DPhysics.cpp.
- TriangleSetMapping has completely changed. Both on x3d field level and internally.
- Removal of using std in some headers means adding std:: in headers that
  previously relied on H3DAPI includes using std.
- BulletSoftBodyOptions::collisionOptions fields default value is now [SDF_RIGIDSOFT]
  instead of [ SDF_RIGIDSOFT, CLUSTER_SOFTSOFT ]. This will be an issue only for
  applications that explicitly sets that particular field to the old default value
  because CLUSTER_SOFTSOFT was previously not used internally in Bullet where as
  it is now used.
- CompositeGeometryNode is now removed.

### MedX3D ###
Source package for the toolkit MedX3D 1.5.0.

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

#### Changes for version 1.5.0 of MedX3D: ####
- Renamed many CMake cache variables and added functions to make it easier
  to setup H3D projects in similar fashions.
- Added CMake functionality for handling external checkouts that contain
  subdirectories built for different visual studio versions.
- Fixed many compile warnings.
- Added support for precompiled headers.
- Added support for unity build.
- Smaller bug fixes.
- Improved MarchingCubes to give it the capability of using a bit more
  complicated shaders.

New fields:
- MarchingCubes::alwaysGenerateOriginalFVA
- MarchingCubes::attrib
- MarchingCubes::normalRenderMode
- MarchingCubes::texCoord
- MarchingCubes::voxelsAllowedToBeReinitialized
- MarchingCubes::writeMarchingCubesAsITS

Compatibility issues:
- Removal of using std in some headers means adding std:: in headers that
  previously relied on H3DAPI includes using std.
- The field ShadedVolumeStyle::lightRayStepSize will now be capped to the
  range [0.0001, inf) in order to avoid openGL crashes when shadows is turned on.
- The fields rayStep, useSlicing, stopRaysAtGeometries, useEmptySpaceSkipping
  showNonEmptySpace and useStochasticJittering are now only accessible
  from C++. To modify those values in X3D a raycaster must be specified
  for the volume node.

### UI ###
This is the source package of UI 2.4.0. It is compatible with H3DAPI 2.4.0. It contains the source code needed to build the UI. Cross platform, works on Windows/Linux/Mac OS.  
It is a collection of nodes that can be used to add a haptic user interface in a H3D scene.

Allow for creation of buttons, slider bars etc touchable by haptics device or mouse..

#### Changes for version 2.4.0 of UI: ####
- Properly implemented enabled field for some widgets for which it was missed.
- Renamed many CMake cache variables and added functions to make it easier
  to setup H3D projects in similar fashions.
- Added CMake functionality for handling external checkouts that contain
  subdirectories built for different visual studio versions.
- Fixed many compile warnings.
- Added support for precompiled headers.
- Added support for unity build.
- Added a way to attach custom nodes to a widget to further customize the way
  it looks.
- Changes to the way that radio buttons with group = -1 are treated: they are
  now assigned a group automatically based on their closest parent Frame.
- Performance improvement fixes.

Compatibility issues:
- Removal of using std in some headers means adding std:: in headers that
  previously relied on H3DAPI includes using std.
- The change to enabled fields could cause issues with any node inheriting from
  the affectd widget nodes (PopupMenu for example).

