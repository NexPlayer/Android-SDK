# Renderers

Depending on the Android OS version and device specifications, NexPlayer SDK offers support for different renderers to render and display video as summarized in the list below.

- Android: NEX\_USE\_RENDER\_AND
- OpenGL: NEX\_USE\_RENDER\_OPENGL
- HW Renderer: NEX\_USE\_RENDER\_IOMX

NexPlayer SDK also offers **NexVideoRenderer**, a video renderer that automatically handles video rendering tasks for an application by choosing the most appropriate renderer based on the device and version of the operating system. Usage of this renderer greatly simplifies the handling of video rendering tasks and it is highly recommended.

?> Please see NexPlayer.setVideoRendererListener and NexVideoRenderer for more information.

If the video surface is destroyed suddenly while NexPlayer is playing content, and it uses **NEX\_USE\_RENDER\_IOMX**, NexPlayer will call PAUSE or STOP immediately to prevent any collisions or crashes with the H/W Decoder. Through this process, UI will receive onAsyncCmdComplete:NEXPLAYER\_ASYNC\_CMD\_PAUSE.

### OpenGL Renderer

This version of the NexPlayer engine supports OpenGL ES 2.0 rendering. 

!> When testing an application, please note that the OpenGL renderer does not work in the Android emulator provided with the Android SDK. Testing content using the OpenGL renderer must happen on an actual device, not through the emulator.*

To use the OpenGL renderer, the application must create an instance of the GLRenderer class (supplied as part of the NexPlayer SDK). GLRenderer is a GLSurfaceView subclass, and the video frame will be displayed within it.

By default, the frame is stretched to fill the entire surface. The rectangle in which the video is drawn can be changed by calling **setOutputPos**. This rectangle is in screen pixels (not in the OpenGL coordinate space) but the position is relative to the GLRenderer.

In addition, an application must also do the following in order to support the OpenGL renderer:

1. Call NexPlayer’s **init** method, passing the model name of the current device (you can attempt to force the use of the OpenGL renderer for debugging purposes by passing NEX\_DEVICE\_USE\_OPENGL instead of the device name).

2. After initializing the NexPlayer instance, In **onVideoRenderPrepared**, check which renderer is being used to determine if it is the OpenGL renderer. Any special code to support the OpenGL renderer should be conditional based on the renderer in use. To determine the current renderer in use, call **GetRenderMode** and check the result, as follows:

```java
if(mNexPlayer.GetRenderMode() == NexPlayer.NEX_USE_RENDER_OPENGL) {
	UseOpenGL = true;
}
```

3. Create an instance of the GLRenderer class and add it to the main view for the activity or some other visible view in your layout:

```java    
if(UseOpenGL) {
	mContext = this;
	mGLListener = this;
	glRenderer = new GLRenderer(mContext, mNexPlayer, mGLListener, colorDepth);
	FrameLayout v = (FrameLayout)findViewById(R.id.gl_container);
	v.addView(glRenderer);
}
```

?> Once the GLRenderer has been created, the onSurfaceCreated and onSurfaceChanged methods of GLSurfaceView will be called when the surface has been crated and it has suffered any change (for example, due to a device orientation change), respectively.

4. In the implementation of *GLSurfaceView.Renderer.onSurfaceChanged*, **NexPlayer.GLInit** must be called to inform NexPlayer of the new size of the surface:

	```java
	public void onSurfaceChanged(GL10 gl, int width, int height) {
		mNexPlayer.GLInit(width, height);
	}
	```		

5. In **onVideoRenderCreate**, the dimensions of the video frame are known, so scaling calculations can be performed and the correct output size can be set:

	```java
	if(nRenderMode != NexPlayer.NEX_USE_RENDER_JAVA) {
		int left = (mSurfaceWidth - mVideoWidth) / 2;
		int top = (mSurfaceHeight - mVideoHeight) / 2;
		mNexPlayer.setOutputPos( left, top, mVideoWidth, mVideoHeight );
	}
	```

6. When NexPlayer is ready to display a new frame, it calls **onVideoRenderRender**. For OpenGL render mode, it is necessary to request a rendering pass from the GLRenderer as follows:
    
	```java
		if(UseOpenGL) {
			glRenderer.requestRender();
		}
	```	

This causes the GLRenderer to render its contents.

?> Whenever the size of the surface changes, for example due to an orientation change, the GLRenderer must also pass the new dimensions to the application through the IListener interface by: `void onGLChangeSurfaceSize( int width, int height);`

### Java Renderer

NexPlayer engine supports Java-based rendering in addition to the usual video rendering methods. However, the Java renderer is never automatically selected; if you wish to use the Java-based renderer, you must explicitly request it when calling NexPlayer’s *init* method with **NEX\_DEVICE\_USE\_JAVA**. 

With Java-based rendering, NexPlayer doesn’t display the video after it is decoded, but rather passes each frame to the application, which then must display the frames as they are received.

Java-based rendering tends to be slower, particularly on low-end devices, but allows the application to perform post-processing or custom scaling operations on each frame.

To support the Java renderer, the application must do the following:

- In **onVideoRenderCreate**, the application must create a bitmap that NexPlayer can render frames into. NexPlayer can render in either RGBA8888 or RGB565. The color depth is specified in the call to NexPlayer’s **init** method. The bitmap you create here must match that color depth. Once the bitmap has been created, it must be registered with the player engine by calling **SetBitmap**. Here’s the recommended way to support the Java renderer in `onVideoRenderCreate`:

```java
private ByteBuffer mRGBBuffer = null;
private Bitmap mFrameBitmap = null;

public void onVideoRenderCreate(NexPlayer mp, int width, int height, Object rgbBuffer) {
	// ...other necessary onVideoRenderCreate code goes here...

	if(mNexPlayer.GetRenderMode() == NexPlayer.NEX_USE_RENDER_JAVA) {
		if(this.mScreenPixelFormat == PixelFormat.RGBA_8888) {
			mFrameBitmap = Bitmap.createBitmap(width, height, Config.ARGB_8888);
		} else {
			mFrameBitmap = Bitmap.createBitmap(width, height, Config.RGB_565);
		}
		mNexPlayer.SetBitmap( mFrameBitmap );
	}
}
```

- The application must implement **onVideoRenderRender**. The bitmap registered in `onVideoRenderCreate` will have been filled in with the rendered frame before this method was called. The application must draw that bitmap to the screen, taking into account scaling and other factors. This can be done using standard Android API calls and standard Java methods. Scaling should be taken into account. See the sample application that accompanies the SDK for an example implementation of this method.

To determine if the Java renderer is in use:

```java
if(mNexPlayer.GetRenderMode() == NexPlayer.NEX_USE_RENDER_JAVA) {
	// code for Java renderer only
}
```

## APIs

### GLRenderer Class

This is the view for displaying NexPlayer video output when using the OpenGL renderer.

For details see the OpenGL Renderer section of the general NexPlayer Engine documentation.

#### GLRenderer (Context context, NexPlayer np, IListener listener, int colorDepth)

The sole constructor.

**Parameters**

| Name  | Description  | 
|---|---|
| context | Android context object (if the caller is an activity, passing this is normal).| 
|np| The NexPlayer object that will provide the video frames to display in this view.|
|listener| An object that implements GLRenderer.IListener, for receiving notifications about changes to the size of the surface.|
|colorDepth| Video output image color depth (this must be the same value passed when initializing NexPlayer).<br>**1** : RGBA\_8888<br>**4** : RGB\_565|

#### void release ()

This method releases resources that are used by the instances of GLRenderer.
 
#### void setListener (IListener listener)

This method sets the IListener for GLRenderer events.

**Parameters**
 
| Name  | Description  | 
|---|---|
|listener| A IListener instance requesting the events that this GLRenderer generates.|

#### boolean mClearScreen = false

This causes the next rendering pass to clear the video image.

If this is set to `TRUE`, the next rendering pass will clear the video image instead of displaying the most recently rendered frame. After the next rendering pass, this is automatically reset to `FALSE`.

The typical method of erasing the current video image is to set this to true and then request a rendering pass, as follows:

```java
glRenderer.mClearScreen = true;
glRenderer.requestRender();
```

#### boolean mReInitRenderer = false

This method causes the next rendering pass to clear the video image and reinitialize the renderer.

If this is set to TRUE, the next rendering pass will call NexPlayer.GLinit instead of displaying the most recently
rendered frame. After the next rendering pass, this is automatically reset to FALSE.

?> When onVideoRenderPrepared is invoked, this should be set to true if the GLRenderer has already been created once.
 
The typical method of reinitializing the video renderer is to set this to true and then request a rendering pass, as follows:

```java
glRenderer.mReInitRenderer = true;
glRenderer.requestRender();
```

### GLRenderer.IListener Interface

The application must implement this interface in order to receive notification when the size of the OpenGL surface (the video rendering surface) changes. This is specified in the constructor for `GLRenderer`.

> Do not confuse this with `NexPlayer.IListener`, a separate interface.

#### void onGLChangeSurfaceSize ( int width, int height )

This method is called when the size of the OpenGL surface has changed.

Whenever the width or height in `GLRenderer` changes, the changed values are passed through the `IListener`.

**Parameters**
 
| Name   | Description                    |
|--------|------------|
| width  | New surface width, in pixels.  |
| height | New surface height, in pixels. |

### NexVideoRenderer Class

A prebuilt FrameLayout containing the video view associated with a NexPlayer instance.

NexVideoRenderer can be used to simplify the video rendering tasks in an application integrating with the NexPlayer SDK. It handles the different renderer types that can be used by NexPlayer  but depend on the device.

To use it:

1. Pass in a Context to the constructor.
```java
mVideoRenderView = new NexVideoRenderer(mContext);
```
2. Set up IListener to receive events from NexVideoRenderer. IVideoRendererListener is set internally.
```java
NexVideoRenderer.IListener mVideoRendererListener = new NexVideoRenderer.IListener() {

		@Override
		public void onDisplayedRectChanged() {
			...
		}

		@Override
		public void onFirstVideoRenderCreate() {
			...
		}

		@Override
		public void onSizeChanged() {
			...
		}

		@Override
		public void onVideoSizeChanged() {
			...
		}
	};
	mVideoRenderView.setListener(mVideoRendererListener);
```
3. Create an instance of NexPlayer.
```java
mNexPlayer = new NexPlayer();
mNexALFactory = new NexALFactory();
```
4. Perform the necessary setup for NexPlayer (such as NexPlayer.setNexALFactory and NexPlayer.init).
```java
...
mNexALFactory.init(...);
mNexPlayer.setNexALFactory(mNexALFactory);
mNexPlayer.init(...);
...
```
6. Add the NexVideoRenderer instance as a view to your layout.
```java
...
mVideoRenderView.init(mNexPlayer);
mVideoRenderView.setVisibility(View.VISIBLE);
...
```

For additional details on how to use this video renderer, please refer to the sample code provided with the SDK.

 
**Classes**
 
#### NexVideoRenderer( Context context ) 

Constructor for NexVideoRenderer.

After creating an instance, you may call getColorDepth to pass to NexALFactory.init.

**Parameters**

| Name            | Description              |
|-----------------|------|
| context | The Context instance associated with the activity that will contain this view. |

#### NexVideoRenderer( Context context, AttributeSet attrs )

Constructor for NexVideoRenderer.
 
#### NexVideoRenderer( Context context, AttributeSet attrs, int defStyle )

Constructor for NexVideoRenderer.

#### int getColorDepth ( )

The color depth associated with this view.

This is associated with the screen pixel format which can be retrieved by getScreenPixelFormat and set with setScreenPixelFormat.

**Returns**
 
One of the constants specified in android.graphics.PixelFormat.
 
#### Rect getDisplayedRect ( )

The android.graphics.Rect that will be displayed by this layout.

This is the position and size of the rectangle within the layout that will display the media content.

This can be changed with a call to setOutputPos.
 
#### Bitmap getLastCapturedFrame ( )

This method gets the last captured video frame.

**Returns**

 
A android.graphics.Bitmap describing the last captured frame.

#### int getScreenPixelFormat ( )

This method gets the current screen pixel format.

**Returns**

 
One of the constants specified in android.graphics.PixelFormat.
 
 
#### void getVideoSize ( Point outSize )

This method gets the current media’s video size.

**Parameters**

| Name            | Description              |
|-----------------|------|
| outSize | [out] A valid instance of android.graphics.Point whose values will be set by this method. | 

#### void init ( NexPlayer nexPlayer )

This method initializes the NexVideoRenderer instance.

**Parameters**

| Name            | Description              |
|-----------------|------|
| nexPlayer | An instance of NexPlayer after its init method has been called. | 

#### boolean isInitialized ( )

This method checks NexVideoRenderer’s current initialization status.

The application should check this method before calling any method other than init or one of the get methods.

**Returns**

TRUE if NexVideoRenderer is initialized, and otherwise FALSE.

#### boolean isUsingOpenGL ( )

This method checks to see if NexVideoRenderer is currently using OpenGL.

**Returns**

TRUE if NexVideoRenderer is using OpenGL, otherwise FALSE.
 
#### void keepScreenOn ( boolean enable )

This method can keep the screen turned ON or OFF.

**Parameters**

| Name            | Description              |
|-----------------|------|
| enable | TRUE: Keep the screen turned ON. FALSE:Screen turnsOFF after a while. :TRUE. | 

#### void onConfigChanged ( Configuration newConfig )

This method sends a signal to notify NexVideoRenderer of a Configuration change.

Overriding Activity’s onConfigurationChanged or Fragment’s onConfigurationChanged is recommended and a pass-through to this method is required to receive timely notifications of any change of size.

**Parameters**

| Name            | Description              |
|-----------------|------|
| newConfig | The new android.content.Configuration. | 

#### void onPause ( )

This method informs the view that the activity is paused.

The owner of this view must call this method when the activity is paused. Calling this method will pause the rendering
thread.

#### void onResume ( )

This method informs the view that the activity has resumed.

The owner of this view must call this method when the activity is being resumed. Calling this method will recreate
the OpenGL display and resume the rendering thread.
 
#### void release ( )

This method releases resources that are used by the instance of NexVideoRenderer.

This should be called before the NexPlayer.release method is called when the instance is no longer needed.

#### void resetSurface ( )

This method resets the surfaceView or GLSurfaceView of NexVideoRenderer.

This method informs the NexVideoRenderer that the holder of NexVideoRenderer has changed. After this method is called, onSizeChanged() may be called.

#### void setActivityPaused ( boolean bPaused )

This method notifies NexVideoRenderer of an onPause callback.

This is to prevent NexVideoRenderer from performing unnecessary operations that could potentially lead to a crash after the activity or fragment is in the background.

**Parameters**

| Name            | Description              |
|-----------------|------|
| bPaused | TRUE when the Activity is paused, otherwise FALSE. |

#### void setListener ( IListener listener )

This method sets the IListener.

**Parameters**

| Name            | Description              |
|-----------------|------|
| listener  | An IListener instance requesting the events that this NexVideoRenderer generates. |

#### void setOutputPos ( int left, int top, int width, int height )

This method sets the displayed rectangle’s position and size.

Within the NexVideoRenderer layout, these parameters will be used to set the output position and size of the media content.

Any time the size of the layout is changed, a rotation occurs, or the size of the content changes, the application should call this method to reset the display boundaries.

The parameters left and top define the top left-hand corner of the rectangle where video contents will be displayed, while width and height define the size of this display rectangle.

**Parameters**

| Name   | Description                                                                                                                                                     |
|--------|-----------------|
| left   | The horizontal position in pixels of the top left-hand corner of the desired rectangle within the NexVideoRenderer layout to start rendering the media content. |
| top    | The vertical position in pixels of the top left-hand corner of the desired rectangle within the NexVideoRenderer layout to start rendering the media content.   |
| width  | The width in pixels of the desired rectangle within the NexVideoRenderer layout to render the media content.                                                    |
| height | The height in pixels of the desired rectangle within the NexVideoRenderer layout to render the media content.|

#### void setPostGLRendererListener ( GLRenderer.IListener postGLRendererListener )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering
process.

**Parameters**

| Name   | Description                                                                                                                                                     |
|--------|-----------------|
| postGLRendererListener   | An instance of the GLRenderer.IListener that requests the callbacks from GLRenderer to handle them after NexVideoRenderer has finished performing its operations. |

#### void setPostNexPlayerVideoRendererListener ( NexPlayer.IVideoRendererListener postNexPlayerVideoRendererListener )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering
process.

**Parameters**

| Name   | Description                                                                                                                                                     |
|--------|-----------------|
| postNexPlayerRendererListener   | An instance of the GLRenderer.IListener that requests the callbacks from NexPlayer to handle them after NexVideoRenderer has finished performing its operations. |

#### void setPostSurfaceHolderCallback ( SurfaceHolder.Callback postSurfaceHolderCallback )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering
process.

**Parameters**


| Name   | Description                                                                                                                                                   |
|--------|---------------|
| postSurfaceHolderCallback   | An instance of SurfaceHolder.Callback that requests the callbacks from the Surface to handle them after NexVideoRenderer has finished performing its operations.|

#### void setPreGLRendererListener ( GLRenderer.IListener preGLRendererListener )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering process.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| preGLRendererListener   | An instance of GLRenderer.IListener that requests the callbacks from GLRenderer to handle them before NexVideoRenderer has started performing its operations.|

#### void setPreNexPlayerVideoRendererListener ( NexPlayer.IVideoRendererListener preNexPlayerVideoRendererListener ) 

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering process.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| preNexPlayerVideoRendererListener   | An instance of NexPlayer.IVideoRendererListener that requests the callbacks from NexPlayer to handle them before NexVideoRenderer has started performing its operations.|                                                                                                                     

#### void setPreSurfaceHolderCallback ( SurfaceHolder.Callback preSurfaceHolderCallback )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering process.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| preSurfaceHolderCallback   | An instance of SurfaceHolder.Callback that requests the callbacks from the Surface to handle them before NexVideoRenderer has started performing its operations.|

#### void setScreenPixelFormat ( int screenPixelFormatToSet)

This method sets the current screen pixel format.

If the model is "Milestone", the screen pixel format will be forced to RGB\_565.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| screenPixelFormatToSet   | One of the constants specified in android.graphics.PixelFormat.|

#### void setShouldFilterBitmap ( boolean shouldFilterBitmap )

This method sets whether or not the bitmap should be filtered when the Java renderer is used.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| shouldFilterBitmap   | TRUE if the bitmap should be filtered, and otherwise FALSE.                                                                                                                                                            |

#### void setSurfaceSecure ( Boolean usesecure )

This method prevents the user from recording the screen on devices running the Android KitKat (4.4) OS and above.

Call this API right after init if screen recording should be prevented.


**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| usesecure   | Set to TRUE to turn on Secure mode to prevent screen recording; otherwise FALSE. This API works on devices running the KitKat OS and above.                                                                                                                                                            |

#### void setUseSurfaceTexture ( boolean useSurfaceTexture, boolean useRenderThread )

The developer can choose SurfaceTexture mode instead of SurfaceView.

SurfaceTexture mode provides a more flexible UI layout, but the performance of SurfaceView is better than that of
SurfaceTexture.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| useSurfaceTexture   | Set to FALSE if you want to display video frames using SurfaceView; otherwise TRUE. SurfaceView performs much better than SurfaceTexture.                                                                                                                                                         |
| useRenderThread   | Set to FALSE if you want to display video frames on the UI thread ; otherwise TRUE. if useRenderThread is TRUE, video frames will display on a separate thread. This parameter can only be applied when using SurfaceTexture. This API works properly on devices running the ICS OS and above.                                                                                                                                                  |

 
?> Call this API right before init.
 
#### void setVisibility ( int visibility )

This method sets the visibility of the NexVideoRenderer layout.

**Parameters**


| Name   | Description                                                                                                                                                   |
|--------|---------------|
| visibility   | A constant from android.view.View.                                                                                                                                                            |
 
### NexVideoRenderer.IListener Interface

The application must implement this interface in order to receive events from `NexVideoRenderer`.

?> These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within *IListener* callbacks. The safest way to update the UI is to use *android.os.Handler* to post an event back to the main application thread.
 
`NexVideoRenderer` will call the methods provided in this interface automatically during playback to notify the application when various events have occurred.

In most cases, the handling of these events is optional; NexPlayer will continue playback normally without the application doing anything special. For best results, handling all events is recommended.

See each individual *IListener* method for a recommendation on how to handle the event in the application.
 

#### void onDisplayedRectChanged ( )

This callback indicates that the displayed rectangle’s position or size has changed.

This event occurs when `NexVideoRenderer.setOutputPos` is called.

This would be a good time for the application to handle any related layout changes that need to be performed, such as changing the layout of subtitles or the player UI controls.


#### void onFirstVideoRenderCreate ( )

This callback indicates that the NexPlayer instance has performed its first of possibly many `onVideoRenderCreate` callbacks.

This event occurs when `NexVideoRenderer` first receives the `onVideoRenderCreate` callback from the associated NexPlayer instance.

On receiving this callback, the application should call `NexVideoRenderer.setOutputPos` to display the video at the desired resolution and aspect ratio.
 
#### void onSizeChanged ( )

This callback indicates that the size of the `NexVideoRenderer FrameLayout` has changed.

This event could occur when the device is rotated or the application requests the view to change size.

On receiving this callback, the application should call `NexVideoRenderer.setOutputPos` to display the video at the
desired resolution and aspect ratio.
 
#### void onVideoSizeChanged ( )

This callback indicates that the size of the media content has changed.

This event will occur at least once when first starting playback.

On receiving this callback, the application should call `NexVideoRenderer.setOutputPos` to display the video at the desired resolution and aspect ratio.


### NexPlayer.IVideoRendererListener Interface

The application must implement this interface in order to receive video renderer-specific events from NexPlayer.

?> These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within *IListener* callbacks. The safest way to update the UI is to use *android.os.Handler* to post an event back to the main application thread.


?> This interface replaces the deprecated methods in `IListener` that received video renderer-specific events from NexPlayer. Note that in existing older applications, the video renderer related methods of `IListener` (now deprecated) can be reused.
 
NexPlayer will call the methods provided in this interface automatically during playback to notify the application when various video renderer-specific events have occurred.

In most cases, the handling of these events is optional; NexPlayer will continue playback normally without the application doing anything special. See each individual *IVideoRendererListener*  method for a recommendation on how to implement it in your application.

**See Also**

- `NexPlayer.setVideoRendererListener`
- `NexVideoRenderer`


#### void onVideoRenderCapture (NexPlayer mp, int width, int height, int pixelbyte, Object bitmap)

Called when a frame of video has been captured.

After calling `captureVideo` to set up video capture, this function will be called whenever a frame is captured, and can process the captured frame as necessary.

```java
	Bitmap bitmap = Bitmap.createBitmap(width, height, pixelbyte==2?Config.RGB\_565:Config.ARGB\_8888 );
	ByteBuffer RGBBuffer = (ByteBuffer)rgbBuffer;
	RGBBuffer.asIntBuffer();
	bitmap.copyPixelsFromBuffer(RGBBuffer);
```

**Parameters**

| Name      | Description                                               |
|-----------|-------------------|
| mp        | The NexPlayer object to which this event applies.    |
| widht     | The width of the captured frame.                          |
| height    | The height of the captured frame.                         |
| pixelbyte | The number of bytes per pixel (2 for RGB565; 4 for RGBA). |
| bitmap    | The object where the captured video frame data is stored. |

Implemented in `NexEventReceiver`.

#### void onVideoRenderCreate (NexPlayer mp,int width,int height,Object rgbBuffer)

This method is called when NexPlayer needs the application to create a surface on which to render the video.

The application must respond to this by calling `setDisplay`.

Generally speaking, the application will actually create the surface earlier, during GUI layout, and will simply use the existing handle in response to this call. There are, however, some threading considerations. See `setDisplay` for details.

**Parameters**

 
| Name      | Description                                                                                         |
|-----------|---------------------|
| mp        | The NexPlayer object to which this event applies.|
| widht     | The width of the source video.|
| height    | The height of the source video.|
| pixelbyte | Direct RGB Buffer(RGB565 format). This RGB buffer is shared with NexPlayer Engine native code. | 

Implemented in `NexEventReceiver`.

#### void onVideoRenderDelete (NexPlayer mp)

This method is called when NexPlayer no longer needs the render surface.

If a surface was created in *onVideoRenderCreate*, this is the place to destroy it. However, if (as in most cases) an existing surface was used, then this function need not take any special action, other than updating whatever state the application needs to track.


**Parameters**

 
| Name | Description                                            |
|------|----------------|
| mp   | The NexPlayer object to which this event applies. | 

Implemented in `NexEventReceiver`.

#### void onVideoRenderPrepared (NexPlayer mp)

This method is called when NexPlayer recognizes which type of video renderer will be used.

At first, NexPlayer does not know which renderer will be used. When this method is called, the application can determine the video renderer mode by calling `GetRenderMode` and prepare for the specified video renderer, as in the following example code:

```java
	public void onVideoRenderPrepared(NexPlayer mp) {
		if(mNexPlayer.GetRenderMode() == NexPlayer.NEX_USE_RENDER_OPENGL) {
			UseOpenGL = true;
			mHandler.post(new Runnable() {
				public void run() {
					mVideoSurfaceView.setVisibility(View.INVISIBLE);
					int colorDepth = 4;
					if(glRenderer == null)
					{
						glRenderer = new GLRenderer(mContext, mNexPlayer, this, colorDepth);
						FrameLayout view = 	(FrameLayout)findViewById(R.id.gl_container);
						view.addView(glRenderer);
					}
					else if(mInitGLRenderer == true)
					{
						glRenderer.mReInitRenderer = true;
						glRenderer.requestRender();
					}
					else
					{
						glRenderer.setVisibility(View.VISIBLE );
					}
				}
			});
		}
		else
		{
			UseOpenGL = false;
			mHandler.post(new Runnable() {
				public void run() {
					if(mNexPlayer.GetRenderMode() == NexPlayer.NEX_USE_RENDER_AND){
							mSurfaceHolder.setType(SurfaceHolder.SURFACE_TYPE_NORMAL);//For Gingerbread Android Renderer
					}
					else
					{
						mSurfaceHolder.setType(SurfaceHolder.SURFACE_TYPE_PUSH_BUFFERS);//For HW Renderer
					}
					if(glRenderer != null)
					{
						glRenderer.setVisibility(View.INVISIBLE );
						glRenderer = null;
					}
					mVideoSurfaceView.setVisibility(View.VISIBLE); // This invokes nexPlayer.setDisplay(mSurfaceHolderForSW, 0);
				}
			});
		}
	}
```

**Parameters**

 
| Name | Description                                            |
|------|----------------|
| mp   | The NexPlayer object to which this event applies. |

Implemented in `NexEventReceiver`.

#### void onVideoRenderRender (NexPlayer mp)

This requests to display Video frame data at JAVA application.

**Parameters**
 
| Name | Description                                            |
|------|----------------|
| mp   | The NexPlayer object to which this event applies. |

Implemented in `NexEventReceiver`.

### NexTextureView.EGLManager Class

**Public Member Functions**

- void **initialize** (final GLSurfaceView.EGLConfigChooser chooser)
- EGLConfig **getConfig** ()
- EGLSurface **getSurface** ()
- EGLContext **getContext** ()
- void **resize** (SurfaceTexture surface)
- void **destroy** ()
- void **bind** ()
- void **unbind** ()
- void **releaseThread** ()
- int **swapBuffers** ()


### NexTextureView Class

#### void clearCanvas ( )

This method requests that the NexTextureView display a blank canvas (black).
 
#### Rect getDisplayedRect ( )

The android.graphics.Rect that will be displayed by this layout.

This is the position and size of the rectangle within the layout that will display the media content.

This can be changed with a call to setOutputPos.
 
#### void getVideoSize ( Point outSize )

This method gets the current media’s video size.

**Parameters**

| Name            | Description              |
|-----------------|------|
| outSize | [out] A valid instance of android.graphics.Point whose values will be set by this method. |

#### void init ( NexPlayer nexPlayer )

This method initializes the NexTextureView instance.

**Parameters**

| Name            | Description              |
|-----------------|------|
| nexPlayer | An instance of NexPlayer after its init method has been called. |

#### boolean isInitialized ( )

This method checks NexTextrueView’s current initialization status.

The application should check this method before calling any method other than init or one of the get methods.

**Returns**

TRUE if NexTextrueView is initialized, and otherwise FALSE.
 
#### void onPause ( )

This method informs the view that the activity is paused.

The owner of this view must call this method when the activity is paused. Calling this method will pause the rendering
thread.

#### void onResume ( )

This method informs the view that the activity has resumed.

The owner of this view must call this method when the activity is being resumed. Calling this method will recreate
the OpenGL display and resume the rendering thread.
 
#### void resetSurface ( )

This method resets the SurfaceTexture of NexTextureView.
 
#### void setActivityPaused ( boolean bPaused )

This method notifies NexTextureView of an onPause callback.

This is to prevent NexTextrueView from performing unnecessary operations that could potentially lead to a crash
after the activity or fragment is in the background.

**Parameters**

| Name            | Description              |
|-----------------|------|
| bPaused | TRUE when the Activity is paused, otherwise FALSE. |

#### void setEGLConfigChooser ( GLSurfaceView.EGLConfigChooser eglConfigChooser )

Config Chooser.

**Parameters**

| Name            | Description              |
|-----------------|------|
| eglConfigChooser | |

#### void setListener ( NexVideoRenderer.IListener listener )

This method sets the IListener.

**Parameters**

| Name            | Description              |
|-----------------|------|
| listener | An IListener instance requesting the events that this NexVideoRenderer generates. |

#### void setOutputPos ( int left, int top, int width, int height )

This method sets the displayed rectangle’s position and size.

Within the NexTextrueView layout, these parameters will be used to set the output position and size of the media content.

Any time the size of the layout is changed, a rotation occurs, or the size of the content changes, the application should call this method to reset the display boundaries.

The parameters left and top define the top left-hand corner of the rectangle where video contents will be
displayed, while width and height define the size of this display rectangle.

**Parameters**

| Name            | Description              |
|-----------------|------|
| left | The horizontal position in pixels of the top left-hand corner of the desired rectangle within the NexTextrueView layout to start rendering the media content. |
| top | The vertical position in pixels of the top left-hand corner of the desired rectangle within the NexTextrueView layout to start rendering the media content.              |
| width | The width in pixels of the desired rectangle within the NexTextrueView layout to render the media content.              |
| height | The height in pixels of the desired rectangle within the NexTextrueView layout to render the media content.              |

#### void setPostNexPlayerVideoRendererListener(NexPlayer.IVideoRendererListener postNexPlayerVideoRendererListener )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering process.

**Parameters**

| Name            | Description              |
|-----------------|------|
| postNexPlayerVideoRendererListener | An instance of the NexPlayer.IVideoRendererListener that requests the callbacks from NexPlayer to handle them after NexVideoRenderer has finished performing its operations. |

#### void setPreNexPlayerVideoRendererListener ( NexPlayer.IVideoRendererListener preNexPlayerVideoRendererListener )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering process.

**Parameters**

| Name            | Description              |
|-----------------|------|
| preNexPlayerVideoRendererListener | An instance of the NexPlayer.IVideoRendererListener that requests the callbacks from NexPlayer to handle them after NexVideoRenderer has started performing its operations. |

 
#### void setSurfaceSecure ( Boolean usesecure )

This method prevents the user from recording the screen on devices running the Android KitKat (4.4) OS and above.

Call this API right after init if screen recording should be prevented.

**Parameters**

| Name            | Description              |
|-----------------|------|
| usesecure | TRUE if the screen is to be "secure" and to prevent screen recording, otherwise FALSE. This API works with devices running the KitKat OS and above. |

#### void setSurfaceSpec ( int pixelFormat, boolean hasDepth, boolean hasStencil )

EGL Config setup.

**Parameters**

| Name            | Description              |
|-----------------|------|
| pixelFormat | |
| hasDepth | |
| hasStencil | |

#### native int GetIFrameCount ( int startTS )

This method returns the I-Frame count.

**Parameters**

| Name            | Description              |
|-----------------|------|
| targetTS | A point to the timestamp of target. |

**Returns**

 
Zero or I-Frame count if successful, negative number if there was an error.
 
#### native int GetIFrameInfo ( int startTS, int[ ] info )

This method get the I-Frame timestamp information.

int[] info is I-Frame timestamp array.

**Parameters**

| Name            | Description              |
|-----------------|------|
| startTS | A point to the start timestamp.|

 
**Returns**

 
Zero or negative number.
 
#### native int GetIFramePos ( int targetTS )

This method returns the nearest I-Frame timestamp in front of target position.

It can get the nearest timestamp of I-Frame in front of target posion to use highlight function.

**Parameters**

| Name            | Description              |
|-----------------|------|
| targetTS | A point to the timestamp of target. |

**Returns**
 
Zero or positive number if successful, negative number if there was an error.
 
#### Bitmap GetThumbData ( int width, int height, int etype, long timestamp )

A Bitmap containing a representative video frame, which can be null, if such a frame cannot be retrieved.

**Parameters**

| Name            | Description              |
|-----------------|------|
| width | |
| height            |              |
| etype            | OUTPUT\_TYPE\_RGB565 or OUTPUT\_TYPE\_RGB888              |
| timestamp            |              |

#### ThumbnailInformation getThumbnailInformation ( )

Call this function after getFrameAtTime.

On failure, a RuntimeException is thrown.

#### long getThumbnailTStamp ( )

Call this function after GetData()

**Returns**
 
Thumbnail timestamp value


