CHANGELOG
==================

## v2.2.0 ##
- [H3DAPI](#h3dapi-2-2-)
- [H3DUtil](#h3dutil-1-2-)
- [HAPI](#hapi-1-2-)
- [H3DPhysics](#h3dphysics-1-2-)
- [MedX3D](#medx3d-1-3-)
- [UI](#ui-2-2-)

### H3DAPI (2.2) ###
#### Changes for version 2.2 of H3DAPI: ####
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

### H3DUtil (1.2)###
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

### H3DPhysics (1.2)###
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

### MedX3D (1.3)###
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

### UI (2.2)###
- All UI nodes now have examples.
- Exposed appearance and textAppearance field for all labeled widgets.
- CMake update to support various compilers on various systems.
- Added isActive to SliderBar, indicates if sliderbar is in use.

