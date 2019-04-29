CHANGELOG
==================
- [v2.4.0](#v2-4-0)
- [v2.3.0](#v2-3-0)
- [v2.2.0](#v2-2-0)

## v2.4.0 ##
- [H3DAPI](#h3dapi-2-4-)
- [H3DUtil](#h3dutil-1-4-)
- [HAPI](#hapi-1-4-)
- [H3DPhysics](#h3dphysics-1-4-)
- [MedX3D](#medx3d-1-5-)
- [UI](#ui-2-4-)

### H3DAPI (2.4) ###
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

### H3DUtil (1.4) ###
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

### HAPI (1.4) ###
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

### H3DPhysics (1.4) ###
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

### MedX3D (1.5) ###
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

### UI (2.4) ###
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

## v2.3.0 ##
- [H3DAPI](#h3dapi-2-3-)
- [H3DUtil](#h3dutil-1-3-)
- [HAPI](#hapi-1-3-)
- [H3DPhysics](#h3dphysics-1-3-)
- [MedX3D](#medx3d-1-4-)
- [UI](#ui-2-3-)

### H3DAPI (2.3) ###
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

### H3DUtil (1.3) ###
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

### HAPI (1.3) ###
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

### H3DPhysics (1.3) ###
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
- IndexedTetraSet::renderMode
- SliderJoint::sliderForce
- H3DSoftBodyLoader::filename is now H3DSoftBodyLoader::url and is an MField. filename can be used a while longer at X3D level. On C++ level it can not.
- CollidableShape::clipPlanes
- CollisionCollection::collidableExceptionGroups

New nodes:
- CollidableExceptionGroup

### MedX3D (1.4) ###
- Generated header is moved to CMake build directory and can only be found in MedX3D/include after INSTALL project has been built.
- Speed optimizations that could affect some compilers.
- Updates to CMake build system to build properly when TortoiseSVN is installed but the current H3D build is not a TortoiseSVN checkout.
- Memory leak fixes which added some functions.
- Fixed MultiVolumeRaycaster since it had quite a few bugs in it.

Removed fields:
- Removed multiVolumeRayCaster::depthTexture field due to it being a forgotten debug output which no longer affected anything.

### UI (2.3) ###
- Generated header is moved to CMake build directory and can only be found in UI/include after INSTALL project has been built.
- Speed optimizations that could affect some compilers.
- Updates to CMake build system to build properly when TortoiseSVN is installed but the current H3D build is not a TortoiseSVN checkout.
- Renamed FindFreeType.cmake to FindH3DFreetype.cmake in order to use CMakes new FindFreetype module if it exists.

## v2.2.0 ##
- [H3DAPI](#h3dapi-2-2-)
- [H3DUtil](#h3dutil-1-2-)
- [HAPI](#hapi-1-2-)
- [H3DPhysics](#h3dphysics-1-2-)
- [MedX3D](#medx3d-1-3-)
- [UI](#ui-2-2-)

### H3DAPI (2.2) ###
- Added functionality for more convenient Import/Export use of Inlined files.
- Added a node clone function. Exposed in python.
- Some DynamicTransform now only updates when value actually change.
- MField::insert() functions fixes to take const_iterator.
- Fix so that ImportLibrary supports specification of several optional paths to
a library in the url field
- Many CMake updates to handle configuration settings for building with various
compilers.
- New stereo formats, HDMI_FRAME_PACKED_720P and HDMI_FRAME_PACKED_1080P
and NVIDIA_3DVISION
- Added support for tesselation shaders.
- Added Testsuit (well first version) which can be used to detemine if
rendering with vertex buffer objects is faster for a specific system.
- Added support for giving inline scripts as CDATA for xml files.
- TwoSidedMaterial::backTransparency is now properly used.
- Fixed bug in CoordinateDeformer. It was always deforming for device 0.
- Fixed issue with obtaining wrong ResourceResolver instance.
- Added force and torque limits to haptics devices.
- Added program settings functionality.
- VRML parser updates to work properly with DEF/USE.
- A DeformableShape instances first occurance in scene graph detemines its deformation.
- deviceInfo field common for all force effects. It is now a MFInt32.
- New base class H3DSingleTextureNode for texture nodes which specify a texture using a
single texture id.
- Fixed use of wrong coordinate system in ProximitySensor.
- Proper implementation of calibration field in PhantomDevice.
- Extrusion updates to comply with latest spec.
- H3DViewer navigation keyboard short-cut now need Alt button pressed.
- Support for including dynamic fields in writeNodeToX3D functions.
- Updates for better support of the X3D proto system.
- H-anim X3D component support.
- Fixed variuos bugs with textures.
- Added generated shader nodes framework.
- Updates to make it easier to configure correct stereo for head mounted displays.
- Support for float internal texture formats.
- Support for full screen anti-aliasing.
- UnityBuild option for users that frequently recompile the API and want to save time.
- H3DViewer use wxWidgets 2.9 and wxPropertyGrid feature.
- 64 bit builds of external libraries.
- DEF is no longer an alternative to moduleName for a PythonScript.
- Documentation now contains a page listing all nodes and their fields.
- Memory leak fixes.
- Support for rendering using vertex buffer object of nodes IndexedTriangleSet, Sphere, Cylinder,
ElevationGrid and SuperShape.
- Fixes to stereo modes HORIZONTAL_INTERLACED, VERTICAL_INTERLACED and VERTICAL_INTERLACED_GREEN_SHIFT.
- Tangent space normal maps in PhongShader node and automatic tangent vertex attribute
generation for IndexedTriangleSet/IndexedFaceSet.
- Support for haptics devices from Haption (VirtuoseDevice).
- PythonScript cleanup on destruction fixes.
- h3dload.ini is now stored in users location if user do not have access rights to
write to default location.
- GraphicsCachingOptions is now named GraphicsOptions.
- X3DPointingDeviceSensor updates to comply with X3D specification.
Also fixed other errors with X3DPointingDeviceSensors.
- Added support for geometry shaders.
- Fixed maxDistance issues with HapticLayeredGroup.
- SpiderMonkey updates. That is much better ECMAscript support.
- ToggleGroup and Clipplane can now be set to work per haptics device.
- Fix bugs with dual windows navigation
- Several new x3d example files to cover all nodes.
- Updates to get correct default headlight in stereo rendering.
- Updates to Shadow geometries and shadows can be done by shaders.
- Several updates to multiPassTransparency.
- Added resolveURLAsFolder functionality

New H3D nodes:
- ComposedGeneratedShader
- EntactDevice
- EnvironmentMapShader
- FrameBufferTextureGenerator
- FullScreenRectangle
- GeneralDirectionalLight
- GeneralPointLight
- GeneralSpotlight
- GeneratedTexture
- GeneratedTexture3D
- GraphicsHardwareInfo
- HAnimDisplacer
- HAnimHumanoid
- HAnimJoint
- HAnimSegment
- HAnimSite
- LayeredRenderer
- MLHIDevice
- MultiDeviceSurface
- MultiRenderTargetShader
- NormalShader
- PhongShader
- RenderTargetSelectGroup
- RotationalSpringEffect
- ShaderCombiner
- ShadowTransform
- VirtuoseDevice

Fields added to existing nodes:
- ClipPlane - hapticsOnDevice
- ComposedShader - transparencyDetectMode
- CoordinateDeformer - deviceAlgorithm
- FakeHapticsDevice - deviceName
- ForceField - torque
- GlobalSettings - x3dROUTESendsEvent, loadTexturesInThread, renderMode
- GraphicsOptions - useDefaultShadows, defaultShadowDarkness, preferVertexBufferObject, defaultShadowGeometryAlgorithm
- H3DHapticsDevice - forceLimit, torqueLimit
- H3DWindowNode - clipDistances
- Inline - importMode, traverseOn
- NavigationInfo - nearVisibilityLimit
- OrthoViewpoint - retainAspectRatio
- PhantomDevice - motorTemperatures
- RenderProperties - alphaFunc, alphaFuncValue, blendFuncSrcFactorRGB,
- blendFuncSrcFactorAlpha, blendFuncDstFactorRGB,
- blendFuncDstFactorAlpha, blendEquationRGB,
- blendEquationAlpha, blendColor
- RuspiniRenderer - alwaysFollowSurface
- SpringEffect - damping, positionInterpolation, interpolatedPosition
- ToggleGroup - hapticsOnDevice
- TransformInfo - outputGLMatrices, glModelViewMatrix, glModelViewMatrixInverse,
- glProjectionMatrix, glProjectionMatrixInverse

Deprecated nodes:
- GraphicsCachingOptions

New python functionality:
- Python created thread can run without H3D python code being run.
- Copy constructors to H3DInterface.Vec classes.
- new python functions:
  - throwQuitAPIException
  - getTopLevelFields
  - createNode
  - getNrHapticsDevices
  - getHapticsDevice
  - getNamedNode
  - TimerCallback.removeCallback
  - Field.getAccessType
  - MField.size
  - Node.clone
- Python doxygen documentation added.
- New constructor for Matrix4f/4d to construct matrix given
translation, rotation and scale.

Compatability issues:
- If deviceInfo field of force effect is not explicitly set then a force effect
will now affect all connected devices and not just the first one. In python
deviceInfo must be set using a list (SFInt32 -> MFInt32).
- preRender/postRender C++ functions must be updated due to change of handling
OpenGL attribute stack (it is quite small).

### H3DUtil (1.2) ###
- CMake updates to configure build for MinGW toolchain.
- New constructors to Matrix4f(d) to construct matrix from position,
rotation and scale parameters.
- Fixes to make a proper debian package.
- New constructors for 4 component constructs to use their 3 component version
plus a single value for the 4th component.
- Fixed bugs with Dicom image loading.
- Fixed a bug in assignment operator of AutoRefVector that would cause a crash
if NULL was added to the vector .
- Fixed a bug that could result in thread locking when a PeriodicThread was 
destructed.
- Updates to compile with gcc 4.5.
- Fixed bug that could cause a problem when deallocating PixelImage instances
created by the loadNrrdFile.
- Fixed a bug that could result in callbacks not being removed from 
removeAsynchronousCallback and clearAllCallbacks.
- Added nrPixelComponents and convertToNormalizedData function to Image class.

### HAPI (1.2) ###
- Able to build HAPIDemo with wxWidget 2.8 and 2.9
- Updates to configure build for MinGW build toolchain.
- Updates to make a proper debian package.
- Updates to ErrorHandler system for haptics devices.
- Many CMake updates for building using a top CMakeLists.txt.
- Fixed thread bugs with FalconHapticsDevice.
- Added alwayFollowSurface option to RuspiniRenderer.
- Added force and torque limits to haptics devices.
- Support for 64 bit dhd (forcedimension).
- Added torque to HapticForceField.
- Added HapticRotationalSpring
- Added damping and position_interpolation to HapticSpring
- Added HaptionHapticsDevice, support for devices from Haption.
- Added MLHIHapticsDevice, support for the Butterfly haptics magnetic 
levitation haptics device.
- Added EntactHapticsDevice, support for haptics devices from Entact Robotics.
- Updates to Chai3DRenderer to use new Chai3D version.
- Fixed a bug in SensableHapticsDevice that sent on torques in Nm instead of 
Nmm which is expected by the driver.
- Update CMake system to work with new 64-bit windows external libraries.
-Added rotation to HapticMasterDevice

New classes:
- HapticRotationalSpring
- HaptionHapticsDevice
- MLHIHapticsDevice
- EntactHapticsDevice

### H3DPhysics (1.2) ###
- H3DPhysics additions to H3DAPIs python interface to get utility functions
in python when using H3DPhysics.
- The package is now called H3DPhysics instead of RigidBodyPhysics.
It contains the X3D RigidBodyPhysics component as well as a well thought
through suggestion for SoftBody capabilities. Of course H3DPhysics offers
haptics capabilities for soft bodies as well.
- New physics engine implemented. PhysX3, still in alpha state.
- New physics engine implemented. SOFA, still in alpha state.
- Fixes to make sure that gravity does not affect scene before all object
are included at startup.
- Support for SoftBodies using Bullet and PhysX. This support is still in beta.
Bullet implementation is fairly stable.
- Improved bullet support. Joint types are now supported with Bullet.

### MedX3D (1.3) ###
- Fixes to raycaster for AMD cards.
- CMake updates to configure properly for several compilers.
- Made sure every node has an example file.
- Changed color fields of several node to RGBA because of specification update.
- Restructuring to set volume renderer through renderer field in X3DVolumeNode.
- Added support for the enabled field in BlendedVolumeStyle
- Added support for orthographic projection to ray caster code
- Fixed a bug that would make the volume rendering disappear if one moved 
into the volume.
- Added support for float textures in MarchingCubes node.

New nodes
- RayCaster
- MultiVolumeRayCaster
- SliceRenderer

Removed nodes:
- IsoSurfaceVolumeStyle

### UI (2.2) ###
- All UI nodes now have examples.
- Exposed appearance and textAppearance field for all labeled widgets.
- CMake update to support various compilers on various systems.
- Added isActive to SliderBar, indicates if sliderbar is in use.


