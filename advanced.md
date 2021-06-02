# Advanced Usage

### AsfPlayReadyDRMManager Class Reference

#### static native int initDRMManager (String strEngineLibName) [static]

Initializes and registers the **AsfPlayReadyDRMManager**.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initDRMManagerMulti (Object nexPlayerHandle, String strEngineLibName) [static]

Internal use only. Please do not use.

### NexLogsToFile.Builder Class Reference

**Public Member Functions**

- Builder **setLogLevels** (int jniLogs, int engineLogs, int codecLogs, int renderLogs, int protocolLogs)
- Builder **setFilePath** (String filePath)
- Builder **seBufferSize** (int bufferSize)
- Builder **seFileCount** (int fileCount)
- Builder **setPreset** (NexFileLogPreset preset)
- NexLogsToFile **build** ()

### NexClosedCaption.CaptionColor Enum Reference

This enumeration sets the text display and background colors of CEA 608 closed captions.

Each color option has an ARGB hexacode associated with the foreground color or background color of the caption to be displayed, as well as a unique value to be used to identify which color is to be selected.

#### static CaptionColor fromValue (int value) [static]

This gets the caption color to be used with CEA 608 closed captions in FULL mode from the integer value.

**Parameters**
 
| Name  | Description  | 
|---|---|
| value | An integer value indicating the caption color to be selected. This is a value between 0x00 and 0xFF.|
 
**Returns**

The caption color to be used.
 
**See Also**
 
The enumerator `CaptionColor` for more details on the possible captions and color values to be used.
 
#### int getBGColor ()

This gets the background color of the character to be displayed with CEA 608 closed captions in FULL mode.

**Returns**

The background color to be displayed as an ARGB hexacode. Please see the enumerator CaptionColor for
the possible hexacodes and their associated colors.
 
#### int getFGColor ()

This gets the text or foreground color of the character to be displayed with CEA 608 closed captions in FULL mode.

**Returns**
 
The text color to be displayed as an ARGB hexacode. Please see the enumerator CaptionColor for the possible
hexacodes and their associated colors.
 
#### int getValue ()

This gets the integer value of the CaptionColor enumerator, to be used with CEA 608 closed captions in FULL mode.

**Returns**

The integer value of the color to be used. This will be one of:
 
- **0x00** : White
- **0x01** : Semi-transparent white
- **0x02** : Green
- **0x03** : Semi-transparent green
- **0x04** : Blue
- **0x05** : Semi-transparent blue
- **0x06** : Cyan
- **0x07** : Semi-transparent cyan
- **0x08** : Red
- **0x09** : Semi-transparent red
- **0x0A** : Yellow
- **0x0B** : Semi-transparent yellow
- **0x0C** : Magenta
- **0x0D** : Semi-transparent magenta
- **0x0E** : Black
- **0x0F** : Semi-transparent black
- **0xFF** : Transparent

#### BLACK = (0x0E, 0xFF000000, 0xFF000000)

This sets the CEA 608 closed captions text or background color black.

#### BLACK\_SEMITRANS = (0x0F, 0xFF000000, 0x77000000)

This sets the CEA 608 closed captions text or background color semi-transparent black.

#### BLUE = (0x04, 0xFF0000FF, 0xFF000077)

This sets the CEA 608 closed captions text or background color blue.

#### BLUE\_SEMITRANS = (0x05, 0xFF0000FF, 0x770000FF)

This sets the CEA 608 closed captions text or background color semi-transparent blue.

#### CYAN = (0x06, 0xFF00FFFF, 0xFF007777)

This sets the CEA 608 closed captions text or background color cyan.

#### CYAN\_SEMITRANS = (0x07, 0xFF00FFFF, 0x7700FFFF)

This sets the CEA 608 closed captions text or background color semi-transparent cyan.

#### GREEN = (0x02, 0xFF00FF00, 0xFF007700)

This sets the CEA 608 closed captions text or background color green.

#### GREEN\_SEMITRANS = (0x03, 0xFF00FF00, 0x7700FF00)

This sets the CEA 608 closed captions text or background color semi-transparent green.

#### MAGENTA = (0x0C, 0xFFFF00FF, 0xFF770077)

This sets the CEA 608 closed captions text or background color magenta.

#### MAGENTA\_SEMITRANS = (0x0D, 0xFFFF00FF, 0x77FF00FF)

This sets the CEA 608 closed captions text or background color semi-transparent magenta.

#### RED = (0x08, 0xFFFF0000, 0xFF770000)

This sets the CEA 608 closed captions text or background color red.

#### RED\_SEMITRANS = (0x09, 0xFFFF0000, 0x77FF0000)

This sets the CEA 608 closed captions text or background color semi-transparent red.

#### TRANSPARENT = (0xFF, 0x00000000, 0x00000000)

This sets the CEA 608 closed captions text or background color transparent (no color).

#### WHITE = (0x00, 0xFFFFFFFF, 0xFFEEEEEE)

This sets the CEA 608 closed captions text or background color white.

#### WHITE\_SEMITRANS = (0x01, 0xFFFFFFFF, 0x77FFFFFF)

This sets the CEA 608 closed captions text or background color semi-transparent white.

#### YELLOW = (0x0A, 0xFFFFFF00, 0xFF777700)

This sets the CEA 608 closed captions text or background color yellow.

#### YELLOW\_SEMITRANS = (0x0B, 0xFFFFFF00, 0x77FFFF00)

This sets the CEA 608 closed captions text or background color semi-transparent yellow.

### NexClosedCaption.CaptionMode Enum Reference

This enumeration sets how CEA 608 closed captions will be displayed (in FULL mode only).

#### staticCaptionModefromValue ( intvalue) [static]

This gets the mode that captions should be displayed based on the integer value of the enumeration.

**Returns**

The CaptionMode to be used to display CEA 608 closed captions. Please see the enumeration for details on the different modes.

#### int getValue ()

This gets the integer value of the CaptionMode enumeration for CEA 608 closed captions.

**Returns**

The integer value of the CaptionMode to be used. See the CaptionMode enumeration for more details.

#### None = (0)

No captions.

#### PaintOn = (3)

Each character in the caption will be displayed at a time, as it becomes available.

#### PopOn = (2)

The entire row of the caption will be displayed ("pop on") the screen at once.

#### RollUp = (1)

The rows of captions will be displayed and "roll up" the screen.

This may include 2, 3, or 4 rows displayed and "rolling" at once.

#### Text = (4)

Only text will be displayed. This mode is used for example in emergency broadcast situations.

### NexVideoView.Settings.CEARenderMode Enum Reference

This enumeration defines the possible modes for CEA rendering.

**Public Member Functions**

- **CEARenderMode** (int value)
- int **getInteger** ()

**Public Attributes**

- **CEA\_608** = (0)
- **CEA\_708** = (1)
- int **mValue**

### NexClosedCaption.Charset Enum Reference

This enumerator defines the encoding character set to be used for CEA 608 closed captions (in FULL mode only).

#### static Charset fromValue (int value) [static]

This gets the character set to be used for encoding based on the integer value.

**Returns**

The character set to be used for encoding. See the **Charset** enumeration for the possible character encoding sets.

#### int getValue ()

This gets the integer value code for the Charset enumeration.

**Returns**

The integer value of the **Charset** enumeration. See the enumeration for possible values.

#### GB\_2312\_80 = (4)

Chinese characters encoding.

#### KSC\_5601\_1987 = (3)

Korean characters encoding.

#### PRIVATE\_1 = (1)

Not currently used but reserved for future use. Can be ignored.

#### PRIVATE\_2 = (2)

Not currently used but reserved for future use. Can be ignored.

#### UNICODE\_UCS2 = (0)

Unicode characters, include special characters for French and Spanish accents.

### NexLogStringQueue.CharUnit Class Reference

This class defines a character unit in CEA 708 closed captions.

**Public Attributes**

- byte mPenSize
- byte mFontStyle
- byte mTextTag
- byte mOffset
- byte mItalics
- byte mUnderline
- byte mEdgeType
- byte mFGOpacity
- byte mBGOpacity
- byte mFGColor
- byte mBGColor
- byte mEdgeColor
- int mCChar

#### int GetARGBBGColor ( )

This method gets the background color of EIA 708 closed captions as an ARGB color.

**Returns**

0 if the background is transparent, or the background ARGB color as an integer.

#### int GetARGBEdgeColor ()

This method gets the edge color of CEA 708 closed captions as an ARGB color.

**Returns**

0 if the edge is transparent, or the edge ARGB color as an integer.

#### int GetARGBTextColor ( )

This method gets the text color of CEA 708 closed captions as an ARGB color.

**Returns**

0 if the text is transparent, or the text ARGB color as an integer.

### DashDRMManager Class Reference

**Static Public Member Functions**

- static native int initDRMManager (String strEngineLibName)
- static native int initDRMManagerMulti (Object nexPlayerHandle, String strEngineLibName)

### DeceUVDRMManager Class Reference

> **Deprecated** For internal use only. Please do not use.

#### static native int initDRMManager (String strEngineLibName) [static]

Initializes and registers the **DeceUVDRMManager**.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initDRMManagerMulti (Object nexPlayerHandle, String strEngineLibName) [static]

Internal use only. Please do not use.

### DRMManager Class Reference

> **Deprecated** For internal use only. Please do not use.

#### static native int initDRMManager (String strEngineLibName) [static]

Initializes and registers DRMManager.

**Parameters**
 
| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initDRMManagerMulti (Object nexPlayerHandle, String strEngineLibName) [static]

Internal use only. Please do not use.

### NexCaptionSetting.EdgeStyle Enum Reference

This enumeration defines the caption edge style.

These are available caption edge styles :

- **NONE** : None.
- **DEFAULT** : Apply a effect by a content.
- **DROP\_SHADOW** : Apply a drop shadow effect to caption text.
- **RAISED** : Apply a raised effect to caption text.
- **DEPRESSED** : Apply a depressed effect to caption text.
- **UNIFORM** : Apply a uniform effect to caption text.

### NexCaptionAttribute.EdgeStyle Enum Reference

This enumeration defines the caption edge style.

These are available caption edge styles :

- **NONE** : Default.
- **DROP\_SHADOW** : Adds a drop shadow effect to caption text.
- **RAISED** : Adds a raised effect to caption text.
- **DEPRESSED** : Adds a depressed effect to caption text.
- **UNIFORM** : Adds a uniform effect to caption text.

### NexTextureView.EGLManager Class Reference

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

### NexEIA708Struct.EIA708Service Class Reference

This class defines a CEA 708 service.

**Public Member Functions**

- void **SetCurrentWindow** (int WinID)

### NexEIA708Struct.EIA708Window Class Reference

This class describes the window where CEA 708 closed captions will be displayed.

#### void ApendChar (int cc)

This method appends a character to the end of a CEA 708 closed caption.

#### void ClearUpdate ()

This method resets the mUpdate paramater that indicates whether CEA 708 closed caption data has been updated
or not.

#### void ClearWindow ()

This method clears the CEA 708 closed caption window.

#### void DeleteWindow ()

This method deletes the CEA 708 closed caption window.

#### int GetARGBColorBorderColor ()

This method gets the border color of CEA 708 closed captions as an ARGB color.

#### int GetARGBColorWindows ()

This method gets the ARGB color windows for CEA 708 closed captions.

#### int GetHeight ()

This method gets the height of the window for CEA 708 closed captions.

#### int GetTextLine (NexLogStringQueue.CharUnit[ ] cData, int index)

This method gets a line of text in CEA 708 closed captions.

**Parameters**
 
| Name  | Description  | 
|---|---|
| cData | The caption data for the received line of text, as anarray of characters.|
| index | The index of the line of text, as an integer.|
  

#### int GetTextLineCount ( )

This method gets the number of the current line of text in CEA 708 closed captions.

#### int GetWidth ( )

This method gets the width of the window for CEA 708 closed captions.

#### void HideWindow ( )

This method hides the CEA 708 closed caption window when called.

#### boolean IsUpdate ( )

This method indicates if CEA 708 closed caption data has been updated.

**Returns**
 
`TRUE` if caption data has been updated, otherwise `FALSE`.
 
#### void SetEndofText ( )

This method sets the end of text in CEA 708 closed captions.

#### void SetPenAttr (byte PenSize, byte FontStyle, byte TextTag, byte Offset, byte Italics, byte Underline, byte EdgeType)

This method sets the CEA 708 closed caption pen attributes.

#### void SetPenColor (byte FGColor, byte FGOpacity, byte BGColor, byte BGOpacity, byte EdgeColor)

This method sets the CEA 708 closed caption pen color.

#### void SetPenLocation (int Row, int Col)

This method sets the CEA 708 closed caption pen position.

**Parameters**
 
| Name  | Description  | 
|---|---|
| Row | The row position.|
| Col | The column position.|
 
#### final void SetPerdefinedPenStyle (byte PenStyle)

This method sets the pen attributes and color based on the pen style in CEA 708 closed captions.

#### final void SetPerdefinedWinStyle (byte WinStyle)

This method sets the window attributes and color based on the window style in CEA 708 closed captions.

#### void SetWinAttr (byte Justify, byte PrintDirection, byte ScrollDirection, byte Wordwrap, byte DisplayEffect, byte EffectDirection, byte EffectSpeed, byte FillColor, byte FillOpacity, byte BorderType, byte BorderColor)

This method sets the CEA 708 closed caption window attributes.

#### void ShowWindow ( )

This method makes the CEA 708 closed caption window visible when called.

#### void ToggleWindow ( )

This method toggles the CEA 708 closed caption window when called.

### NexMediaDrmSessionManager.EventListener Interface Reference

**Public Member Functions**

- void **onDrmKeysLoaded** (byte[ ] keySetId, byte[ ] sessionId)
- void **onDrmSessionManagerError** (Exception e)
- void **onDrmKeyStatusChanged** (List<NexMediaDrm.KeyStatus>KeyStatusInfo, byte[ ] sessionId)
- void **onDrmKeyExpired** (Exception e)
- void **onDrmKeysRestored** ()
- void **onDrmKeysRemoved** ()

### NexStatisticsMonitor.FileType Enum Reference

An enumeration of the possible types of files being handled by NexPlayer™ during HLS, DASH or SS playback.

These are possible values for the HTTP statistics parameter key, *FILE\_TYPE*.

#### FileType (intcode)

Sets the ***FileType***.

#### int getCode()

Gets the ***FileType*** code as an integer.

**Returns**

The requested ***FileType*** code as an integer.
 
#### static FileType toFileType (int code) [static]

This method gets the ***FileType*** from the integer code of the ***FileType***.

**Returns**

The ***FileType*** corresponding to the given integer code. This will be one of:
 
- `UNKNOWN` for an unknown filetype,
- `MANIFEST` for a manifest file,
- `SEGMENT` for a segment file,
- `INITIAL_SEGMENT` for an initial segment file, or
- `KEY` for a key file.
 
### NexStatisticsMonitor.GeneralStatisticsMetric Enum Reference

This is an enumeration of the possible general statistics that can be requested during playback of HLS, DASH or SS content in NexPlayer™.

The statistics defined here are for general playback of HLS, DASH or SS content. If statistics about the initialization of content are required, please review ***InitialStatisticsMetric*** instead.

**See Also**
 
- InitialStatisticsMetric
- IStatistics
- setDuration

#### GeneralStatisticsMetric (int code)

Sets the general statistic metric.

#### int getCode ()

Gets the general statistic code, as an integer.

**Returns**
 
The general statistics code requested.
 
Implements **NexStatisticsMonitor.IStatistics**.

#### BYTES\_RECEIVED = ( 0x00000200 )

The bytes received, as a long.

This is the same as NexRTStreamInformation.mNumOfBytesRecv.

#### CUR\_NETWORK\_BW\_BPS = ( 0x00000300 )

The current bandwidth of the network, in bps, as an integer.

This is the same as NexRTStreamInformation.mCurNetworkBw.

#### CUR\_TRACK\_BW\_BPS = ( 0x00000400 )

The current track bandwidth, in bps, as an integer.

This is the same as NexRTStreamInformation.mCurTrackBw.

#### NUM\_HTTP\_REQUESTS = ( 0x00001000 )

This current number of HTTP requests that have been made, as an integer.

This is the same as the running count of onHttpRequest (NexPlayer mp, String msg) calls.

#### NUM\_REQUEST\_ERRORS = ( 0x00000A00 )

The current number of segments that the player failed to receive, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegFailToReceive.

#### NUM\_REQUEST\_TIMEOUT = ( 0x00000B00 )

The current number of segment reads that resulted in a timeout, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegTimeout.

#### NUM\_SEG\_DOWN\_RATE = ( 0x00000700 )

The number of segments that have an actual read bitrate below the bitrate specified in the profile, where the read
bitrate is the speed at which the segments are read from the network.

This is the same as NexRTStreamInformation.mNumOfSegDownRate.

#### NUM\_SEG\_FAIL\_TO\_PARSE = ( 0x00000800 )

The number of segment reads that were failed to be read and parsed, for example due to HTTP errors, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegFailToParse.

#### NUM\_SEG\_IN\_BUFFER = ( 0x00000900 )

The current number of segments in the buffer, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegInBuffer.

#### NUM\_SEG\_RECEIVED = ( 0x00000600 )

The current number of segments received, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegReceived.

#### NUM\_SEG\_REQUESTS = ( 0x00000500 )

The current number of segment requests, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegRequest.

#### NUM\_TRACK\_SWITCH\_DOWN = ( 0x00000D00 )

The number of times the content profile has been changed to a profile with a lower bitrate, as an integer.

This is the same as NexRTStreamInformation.mNumOfTrackSwitchDown.

#### NUM\_TRACK\_SWITCH\_UP = ( 0x00000C00 )

The number of times the content profile has been changed to a profile with a higher bitrate, as an integer.

This is the same as NexRTStreamInformation.mNumOfTrackSwitchUp.

#### NUM\_VIDEO\_FRAME\_DECODED = ( 0x00000F00 )

The current number of frames that have been decoded, as an integer.

This is the same as getContentInfoInt (NexPlayer.CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_DECODIN-
G\_TOTAL\_COUNT).

#### NUM\_VIDEO\_FRAME\_RENDERED = ( 0x00000E00 )

The current number of frames that have been successfully rendered, as an integer.

This is the same as getContentInfoInt (NexPlayer.CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_TOTAL\_COUNT).

#### PLAY\_TIME\_SEC = ( 0x00000100 )

The current play time in seconds, as along.

This is the same as the count of NEXPLAYER\_EVENT\_TIME.

### GetHttpAuthInfoManager Class Reference

**Deprecated** For internal use only. Please do not use.



#### static native int initManager (String strEngineLibName) [static]

Initializes and registers the GetHttpAuthInfoManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initManagerMulti (Object nexPlayerHandle, String strEngineLibName) [static]

Internal use only. Please do not use.

### GetKeyExtManager Class Reference

> **Deprecated** For internal use only. Please do not use.



#### static native int initManager (String strEngineLibName) [static]

Initializes and registers the GetKeyExtManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initManagerMulti ( Object nexPlayerHandle, String strEngineLibName) [static]

Internal use only. Please do not use.

### GetPDBlockManager Class Reference

> **Deprecated** For internal use only. Please do not use.



#### static native int initManager (String strEngineLibName) [static]

Initializes and registers the GetPDBlockManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initManagerMulti (Object nexPlayerHandle, String strEngineLibName) [static]

Internal use only. Please do not use.

### GetPlaylistInfoManager Class Reference

> **Deprecated** For internal use only. Please do not use.


#### static native int initManager (String strEngineLibName) [static]

Initializes and registers the GetPlaylistInfoManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initManagerMulti (Object nexPlayerHandle, String strEngineLibName) [static]

Internal use only. Please do not use.

### GLRenderer Class Reference

This is the view for displaying NexPlayer™ video output when using the OpenGL renderer.

For details see the OpenGL Renderer section of the general NexPlayer™ Engine documentation.

#### GLRenderer (Contextcontext, NexPlayernp, IListenerlistener, intcolorDepth)

The sole constructor.

**Parameters**

| Name  | Description  | 
|---|---|
| context | Android context object (if the caller is an activity, passing this is normal).| 
|np| The NexPlayer™ object that will provide the video frames to display in this view.|
|listener| An object that implements GLRenderer.IListener, for receiving notifications about changes to the size of the surface.|
|colorDepth| Video output image color depth (this must be the same value passed when initializing NexPlayer™).<br>**1** : RGBA\_8888<br>**4** : RGB\_565|



#### void release ()

This method releases resources that are used by the instances of GLRenderer.
 
#### void setListener (IListener listener)

This method sets the IListener.

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

> **Warning** When onVideoRenderPrepared is invoked, this should be set to true if the GLRenderer already has been created once.
 
The typical method of reinitializing the video renderer is to set this to true and then request a rendering pass, as follows:

```java
glRenderer.mReInitRenderer = true;
glRenderer.requestRender();
```
 
### HLSAES128DescrambleManager Class Reference

> **Deprecated** For internal use only. Please do not use.



#### static native int initManager (String strEngineLibName) [static]

Initializes and registers the HLSAES128DescrambleManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.| 
 
#### static native int initManagerMulti (Object nexPlayerHandle, String strEngineLibName) [static]

Internal use only. Please do not use.

### HLSTsDRMManager Class Reference

This class allows NexPlayer™ to handle and descramble HLS TS encrypted content.



#### static native int initDRMManager (String strEngineLibName) [static]

Initializes and registers the `HLSTsDRMManager`.

**Parameters**

| Name  | Description                                                                |
|-------|----------------|
| strEngineLibName | The relevant engine library name as a string. |
 
#### static native int initDRMManagerMulti (Object nexPlayerHandle,String strEngineLibName) [static]

Internal use only. Please do not use.

### HTTPRetrieveDataManager Class Reference

This class allows NexPlayer™ to support and handle offline HLS and Smooth Streaming content.
 
#### static native int initManager (String strEngineLibName, String cachFolder) [static]

Initializes and registers the `HTTPRetrieveDataManager`.

**Parameters**

| Name  | Description                                                                |
|-------|----------------|
| strEngineLibName | The relevant engine library name as a string. |
| cachFolder | The folder to be used for the cache, as a string. |
 
#### static native int initManagerMulti (Object nexPlayerHandle, String strEngineLibName, String cachFolder) [static]

Internal use only. Please do not use.

### NexStatisticsMonitor.HttpStatisticsMetric Enum Reference

This enumeration defines the possible HTTP statistics that can be requested during HLS, DASH or SS playback by NexPlayer™.

For general playback statistics or system statistics during playback, please monitor `GeneralStatisticsMetric` or `SystemStatisticsMetric` instead.

**Public Attributes**

- **DOWN\_START** = ( 0x00000000 )
- **CONNECT** = ( 0x00000001 )
- **CONNECTED** = ( 0x00000003 )
- **HEADER\_RECEIVED** = ( 0x00000004 )
- **DATA\_RECEIVED** = ( 0x00000005 )
- **DOWN\_END** = ( 0x00000006 )
- **ERROR** = ( 0x00000007 )

**See Also**
 
- GeneralStatisticsMetric
- SystemStatisticsMetric
- HttpStatisticsParamKey
 
#### HttpStatisticsMetric( int code )

Sets the HTTP statistics metric.

#### int getCode ( )

Gets an HTTP statistic metric as an integer.

**Returns**

The requested HTTP statistic metric, as an integer.
 
Implements `NexStatisticsMonitor.IStatistics`.

### NexStatisticsMonitor.HttpStatisticsParamKey Enum Reference

This enumeration defines the parameter key, for parameters related to HTTP statistics monitored during HLS, DASH or SS playback.

**Public Attributes**

- **RESOURCE\_URL** = ( 0x00000000 )
    The resource URL, as a *String*.
- **FILE\_TYPE** = ( 0x00000001 )
	 The file type being received, as a *`FileType`*.
- **SEG\_NO** = ( 0x00000002 )
    The current segment number, as an integer.
- **SEG\_DURATION** = ( 0x00000003 )
    The duration of the current segment, as an integer.
- **TRACK\_BW** = ( 0x00000004 )
    The bandwidth of the current track, as an integer.
- **MEDIA\_COMPOSITION** = ( 0x00000005 )
    The media composition of the current content, as an integer.
- **BYTE\_RECEIVED** = ( 0x00000006 )
    The current number of bytes received, as a *long*.
- **CONTENT\_LENGTH** = ( 0x00000007 )
    The current length of the HLS, DASH or SS content received so far, as a *long*.
- **ERROR\_CODE** = ( 0x00000008 )
    The error code.

**See Also**
 
HttpStatisticsMetric
 
#### HttpStatisticsParamKey (int code)

Sets the HTTP statistics parameter key.



#### final int getCode ()

Gets the HTTP statistics parameter key as an integer code.

**Returns**
 
The HTTP statistics parameter key requested, as an integer.
 
#### BYTE\_RECEIVED = ( 0x00000006 )

The current number of bytes received, as a *long*.

A parameter for the HTTP statistics, *DATA\_RECEIVED* and *DOWN\_END*.

#### CONTENT\_LENGTH = ( 0x00000007 )

The current length of the HLS, DASH or SS content received so far, as a *long*.

A parameter for the HTTP statistic,DATA\_RECEIVED.

#### ERROR\_CODE = ( 0x00000008 )

The error code.

A parameter for the HTTP statistic, *ERROR*.

#### FILE\_TYPE = ( 0x00000001 )

The file type being received, as a *`FileType`*.

A parameter for the HTTP statistic, *DOWN\_START*.

#### MEDIA\_COMPOSITION = ( 0x00000005 )

The media composition of the current content, as an integer.

A parameter for the HTTP statistic, *DOWN\_START*.

#### RESOURCE\_URL = ( 0x00000000 )

The resource URL, as a *String*.

A possible parameter for the HTTP statistics, *DOWN\_START*, *CONNECT*, *CONNECTED*, *HEADER\_RECEIVED*,
 *DATA\_RECEIVED*, *DOWN\_END*, and *ERROR*.

#### SEG\_DURATION = ( 0x00000003 )

The duration of the current segment, as an integer.

A parameter for the HTTP statistic, *DOWN\_START*.

#### SEG\_NO = ( 0x00000002 )

The current segment number, as an integer.

A parameter for the HTTP statistic, *DOWN\_START*.

#### TRACK\_BW = ( 0x00000004 )

The bandwidth of the current track, as an integer.

A parameter for the HTTP statistic, *DOWN\_START*.

### HTTPStoreDataManager Class Reference
 


#### static native int initManager (String strEngineLibName, String cachFolder) [static]

Initializes and registers the HTTPStoreDataManager.

**Parameters**

| Name  | Description                                                                |
|-------|----------------|
| cData | The caption data for the received line of text, as an array of characters. |
| cachFolder     | The folder to be used for the cache, as a string.|
 
#### static native int initManagerMulti (Object nexPlayerHandle, String strEngineLibName, String cachFolder) [static]

Internal use only. Please do not use.

### NexABRController.IABREventListener Interface Reference

This interface must be implemented in order for the application to receiveABRControlevents from NexABRController.

NexABRController will call the methods provided in this interface automatically during playback to notify the application when various ABRControl events have occurred.

In most cases, the handling of these events is optional; NexPlayer™ will continue to play content back normally without the application doing anything special in response to the events received.
 


#### abstract void onMinMaxBandWidthChanged (NexErrorCode result, int minBwBps,  int maxBwBps) [abstract]

This method will be called by the NexABRController when either the minimum or maximum bandwith allowed
for streaming content is changed.

**Parameters**

| Name  | Description  | 
|---|---|
| result | NexErrorCode object for the specified error code.|
| minBwBps | Minimum bandwidth in bps (bits per second)|
| maxBwBps | Maximum bandwidth in bps (bits per second)|
  
**See Also**
 
- changeMinMaxBandWidth()
- changeMaxBandWidth()
- changeMinBandWidth()
 
#### abstract void onTargetBandWidthChanged (NexErrorCode result, int reqBwBps, int selBwBps) [abstract]

This method will be called by the NexABRController when the target bandwidth for streaming content is
changed.

For example, if content has three tracks at bandwidths of 500k, 900k, and 1200k and the applications calls set TargetBandwidth to set a target of 700k with the target option `BELOW`, `reqBwBps` will be 700,000 and `selBwBps` will be 500,000.

**Parameters**

| Name  | Description  | 
|---|---|
| result | NexErrorCode object for the specified error code.|
| reqBwBps | The requested target bandwidth to select a track, in bps (bits per second)|
| selBwBps | The actual bandwidth of the track selected, in bps (bits per second)|
 
**See Also**
 
- setTargetBandWidth


### NexHLSAES128DRMManager.IAESCallbackListener Interface Reference

An interface for GetKeyExternal and IsSupportKey Callbacks.

This must be implemented by the UI.



#### byte [ ] getKeyFromExternal (String strKeyUrl)

Callback function to retrieve an encryption key from an HLS playlist over HTTPS for descrambling.

This function is called each time a new playlist is received and an encryption key is available in the playlist.


**Parameters**

| Name  | Description  | 
|---|---|
| strKeyUrl | A pointer to the URL of the encryption key.|
 
**Returns**
 
A byte array where the encryption key information will be stored.
 
#### boolean isSupportKeyAttr (String strKeyAttr, String strURL)

Callback function that verifies whether or not a key attribute is supported by the DRM module.

This callback is called when NexPlayer meets `#EXT-X-KEY` tags while NexPlayer is parsing playlists. If the callback returns a non-zero value, NexPlayer will not call DRM functions even if that function is registered.

**Parameters**

| Name  | Description  | 
|---|---|
| strURL | The URL of the playlist.|
| strKeyAttr | Key information of the segment that has been received.|
 
**Returns**

If the DRM supports that key attribute, then it should return TRUE. Then, NexPlayer will call DRM callbacks
depending on the encryption method. If the DRM does not support the key, then it should return FALSE.
In this case, NexPlayer will not call the "getKeyFromExternal" callbacks and it will decrypt using its internal decryption function.
 
### NexALFactory.ICodecDownListener Interface Reference

> **Warning** These methods are for internal usage only. Please do not use.
 
#### void onCodecDownloaderEventBegin (int param1, long param2)

For internal use only. Please do not use.

#### void onCodecDownloaderEventComplete (int param1, int result )

For internal use only. Please do not use.

#### void onCodecDownloaderEventError (NexALFactoryErrorCode errorcode )

For internal use only. Please do not use.
 
#### void onCodecDownloaderProgress (int param1, int param2, long param3, long param4)

For internal use only. Please do not use.
 
### NexPlayer.IDynamicThumbnailListener Interface Reference

This interface must be implemented in order for the application to receive Dynamic Thumbnail events from NexPlayer™.

NexPlayer™ will call the methods provided in this interface automatically during playback to notify the application when various Dynamic Thumbnail events have occurred.

In most cases, the handling of these events is optional; NexPlayer™ will continue play content back normally
without the application doing anything special in response to the events received.
 


#### void onDynamicThumbnailData (NexPlayer mp, int width, int height, int cts, Object bitmap)

This method will be called by the NexPlayer™ engine when thumbnail data is created.

If the `enableDynamicThumbnail()` method is called before Smooth Streaming content is in the open state,
then this method will be called and gets the thumbnail information associated with the content.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|
| width | The width of the thumbnail image.|
| height | The height of the thumbnail image.|
| cts | The current timestamp of the thumbnail image.|
| bitmap | RGB buffer pointer(RGB565) of the thumbnail image.| 
 
> Implemented in NexEventReceiver.

#### void onDynamicThumbnailRecvEnd (NexPlayer mp)

This callback method informs the Dynamic Thumbnail listener when the end of thumbnail data is received.

**Parameters**
 
| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|
 
> Implemented in NexEventReceiver.

### NexPlayer.IHTTPABRTrackChangeListener Interface Reference

This interface must be implemented in order for the application to receive an ABR Track switch event from NexPlayer™.

NexPlayer™ will call the methods provided in this interface automatically during playback to notify the application when an ABR Track switch event has occurred.

In most cases, the handling of this event is optional; NexPlayer™ will continue to play content normally without the application doing anything special in response to the event received.

> **Note** To use the method defined by this interface, NexProperty.ENABLE\_HTTPABRTRACKCHANGE\_CALLBACK
should be enabled before calling open.
 


#### int onHTTPABRTrackChange (NexPlayer mp, int param1, int param2, int param3)

This method will be called by the NexPlayer™ engine when the ABR track is switched.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|
| param1 | The current network bandwidth.|
| param2 | The current track bandwidth.|
| param3 | The target track bandwidth.|
 
**Returns**

The exact track bandwidth that the user wants to set to forcibly.
 
> Implemented in NexEventReceiver.

### NexPlayer.IListener Interface Reference

The application must implement this interface in order to receive events from NexPlayer™.

> **CAUTION:** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from with in IListener callbacks. The safest way to update the UI is to use `android.os.Handler` to post an event back to the main application thread.

NexPlayer™ will call the methods provided in this interface automatically during playback to notify the application when various events have occurred.

In most cases, the handling of these events is optional; NexPlayer™ will continue playback normally without the application doing anything special. There are a few exceptions to this which are listed below.

There are two categories of notifications. First of all, for any asynchronous command issued to NexPlayer™ (via the appropriate method call), a callback will occur when that command has completed to notify the application of the success or failure of the operation.

The other category of notifications are notifications that occur during playback to notify the application of changes in the state of NexPlayer™. For example, if NexPlayer™ begins buffering data during streaming playback, an event occurs to allow the application to display an appropriate message, if necessary.

For asynchronous commands, the application will generally want to take action in the following cases (some applications may need to handle these differently depending on their requirements; these are correct for most cases):

- When any command fails, display an error to the user.
- When an open command succeeds, issue a start command to begin actual playback.
- When a stop command succeeds, issue a close command to close the file.

This is because commands such as open and stop take some time to execute, and follow-up commands such as
start and close can not be called immediately, but must wait until the first command has completed.

> **Warning** However, do not call close in these event handlers as this may give rise to a deadlock. A safe way to call `close` is to use the Android UI main thread’s message handler.

> See each individual `IListener` method for a recommendation on how to implement that method in your application.

**Public Attributes**

- `int eNEXPLAYER_STATUS_NONE = 0x00000000`

	Possible value for msg parameter of onStatusReport.

- `int eNEXPLAYER_AUDIO_GET_CODEC_FAILED = 0x00000001`

	Possible value for msg parameter of onStatusReport.

- `int eNEXPLAYER_VIDEO_GET_CODEC_FAILED = 0x00000002`

	Possible value for msg parameter of onStatusReport.

- `int eNEXPLAYER_AUDIO_INIT_FAILED = 0x00000003`
 
	Possible value for msg parameter of onStatusReport.
 
- `int eNEXPLAYER_VIDEO_INIT_FAILED = 0x00000004`

	Possible value for msg parameter of onStatusReport.

- `int eNEXPLAYER_TRACK_CHANGED = 0x00000005`
    
	Possible value for msg parameter of onStatusReport.

- `int eNEXPLAYER_STREAM_CHANGED = 0x00000006`

	Possible value for msg parameter of onStatusReport.

- `int eNEXPLAYER_DSI_CHANGED = 0x00000007`

	Possible value for msg parameter of onStatusReport.

- `int eNEXPLAYER_OBJECT_CHANGED = 0x00000008`

	Possible value for msg parameter of onStatusReport.

- `int eNEXPLAYER_CONTENT_INFO_UPDATED = 0x00000009`

	Possible value for msg parameter of onStatusReport.

- `int NEXPLAYER_STATUS_MAX = 0xFFFFFFFF`

	Possible value for msg parameter of onStatusReport.



#### void onAsyncCmdComplete (NexPlayer mp, int command, int result, int param1, int param2)

When an asynchronous method of NexPlayer™ has completed successfully or failed, this event occurs.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|
| command | The command which completed. This may be any of the following values:|
| result | Zero if the command was successful, otherwise an error code.|

```
NEXPLAYER_ASYNC_CMD_OPEN_LOCAL (0x00000001)
NEXPLAYER_ASYNC_CMD_OPEN_STREAMING (0x00000002)
NEXPLAYER_ASYNC_CMD_OPEN_TV (0x00000003)
NEXPLAYER_ASYNC_CMD_START_LOCAL (0x00000005)
NEXPLAYER_ASYNC_CMD_START_STREAMING (0x00000006)
NEXPLAYER_ASYNC_CMD_START_TV (0x00000007)
NEXPLAYER_ASYNC_CMD_STOP (0x00000008)
NEXPLAYER_ASYNC_CMD_PAUSE (0x00000009)
NEXPLAYER_ASYNC_CMD_RESUME (0x0000000A)
NEXPLAYER_ASYNC_CMD_SEEK (0x0000000B)
NEXPLAYER_ASYNC_CMD_STEP_SEEK (0x0000000E)
NEXPLAYER_ASYNC_CMD_REINITVIDEO (0x00000013)
NEXPLAYER_ASYNC_CMD_FASTPLAY_START (0x00000027)
NEXPLAYER_ASYNC_CMD_FASTPLAY_STOP (0x00000028)
NEXPLAYER_ASYNC_CMD_SET_MEDIA_STREAM (0x00000031)
```
 
Below are the possible error codes for `async_command_value`.

* NEXPLAYER\_ASYNC\_CMD\_OPEN\_LOCAL 
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- SOURCE\_OPEN\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- UNKNOWN
 
* NEXPLAYER\_ASYNC\_CMD\_OPEN\_STREAMING
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- SOURCE\_OPEN\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- UNKNOWN
 
* NEXPLAYER\_ASYNC\_CMD\_START\_LOCAL
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- DATA\_INACTIVITY\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- CODEC\_DECODING\_ERROR
	- NOT\_SUPPORT\_VIDEO\_RESOLUTION
	- UNKNOWN

 
* NEXPLAYER\_ASYNC\_CMD\_START\_STREAMING
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- DATA\_INACTIVITY\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- CODEC\_DECODING\_ERROR
	- NOT\_SUPPORT\_VIDEO\_RESOLUTION
	- UNKNOWN

 
* NEXPLAYER\_ASYNC\_CMD\_STOP
	- NOT\_SUPPORT\_MEDIA
	- ERROR\_NETWORK\_PROTOCOL
	- UNKNOWN

* NEXPLAYER\_ASYNC\_CMD\_PAUSE
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- ERROR\_NETWORK\_PROTOCOL
	- UNKNOWN

* NEXPLAYER\_ASYNC\_CMD\_RESUME
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- UNKNOWN
 
* NEXPLAYER\_ASYNC\_CMD\_SEEK
	- INVALID\_STATE
	- NOT\_SUPPORT\_TO\_SEEK
	- DATA\_INACTIVITY\_TIMEOUT
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- CODEC\_DECODING\_ERROR
	- UNKNOWN

* NEXPLAYER\_ASYNC\_CMD\_SETEXTSUBTITLE 
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- UNKNOWN
 
* NEXPLAYER\_ASYNC\_CMD\_REINITVIDEO
	- INVALID\_STATE
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- CODEC\_DECODING\_ERROR
	- NOT\_SUPPORT\_TO\_SEEK
	- DATA\_INACTIVITY\_TIMEOUT
	- UNKNOWN
 
* NEXPLAYER\_ASYNC\_CMD\_FASTPLAY\_START
	- INVALID\_STATE
	- UNKNOWN

* NEXPLAYER\_ASYNC\_CMD\_FASTPLAY\_STOP
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- CODEC\_DECODING\_ERROR
 
* NEXPLAYER\_ASYNC\_CMD\_SET\_MEDIA\_STREAM
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- UNKNOWN

* NEXPLAYER\_ASYNC\_CMD\_OPEN\_STORE\_STREAM
	- INVALID\_PARAMETER
	- SOURCE\_OPEN\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- ERROR\_NETWORK\_PROTOCOL
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- UNKNOWN
 
* NEXPLAYER\_ASYNC\_CMD\_START\_STORE\_STREAM
	- INVALID\_STATE
	- INVALID\_PARAMETER
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- ERROR\_NETWORK\_PROTOCOL
	- FILE\_INVALID\_SYNTAX
	- UNKNOWN

**Parameters**
 
| Name  | Description  | 
|---|---|
| param1 | A value specific to the command that has completed. The following commands use this value (for all other commands, the value is undefined and reserved for future use, and must be ignored): <br>**NEXPLAYER\_ASYNC\_CMD\_SEEK:** The actual position at which the seek command completed. Depending on the media format, this may be different than the position that was requested for the seek operation.| 
| param2 | A value specific to the command that has completed. Currently there are no commands that pass this parameter, and it is reserved for future use. Applications should ignore this value.| 
 
> Implemented in NexEventReceiver.

#### void onAudioRenderCreate (NexPlayer mp, int samplingRate, int channelNum)

Notification that the audio rendering thread has been created.

Under previous versions of the SDK, it was necessary to create and manage the audio renderer. However, under
the current version this is done automatically, and the on AudioRenderCreate method should be empty or
contain only diagnostic code.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| samplingRate | The sample rate (in Hz) of the content to be played back.| 
| channelNum | The number of channels in the content (1=mono, 2=stereo).| 
 
> Implemented in NexEventReceiver.

#### void onAudioRenderDelete(NexPlayer mp)

Notification that the audio rendering thread has been destroyed.

Under previous versions of the SDK, it was necessary to destroy the audio renderer. However, under the current version this is done automatically, and the on AudioRenderDelete method should be empty or contain only
diagnostic code.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
  
> Implemented in NexEventReceiver.

#### void onAudioRenderPrepared (NexPlayer mp)

This method is called when NexPlayer™ recognizes which audio render will be used.

Because NexPlayer™ supports only a SW audio render, this method will not be used.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
  
> Implemented in NexEventReceiver.

#### void onBuffering (NexPlayer mp, int progress\_in\_percent)

This reports the current buffering status.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| progress\_in\_percent | The current buffering percentage.| 
   
> Implemented in NexEventReceiver.

#### void onBufferingBegin (NexPlayer mp)

Reports the start of buffering.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
 
> Implemented in NexEventReceiver.

#### void onBufferingEnd (NexPlayer mp)

This reports the end of buffering.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
 
> Implemented in NexEventReceiver.

#### void onDataInactivityTimeOut (NexPlayer mp)

Reports Data Inactivity Timeout.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
 
> Implemented in NexEventReceiver.

#### void onDateRangeData (NexPlayer mp, NexDateRangeData[] data)

This method reports the data Range value that is contained in the EXT-X-DATERANGE tag.

**Parameters**

 
| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| data | The array of NexDateRangeData object that includes data Range and data contained in the EXT-X-DATERANGE tag.| 
 
> Implemented in NexEventReceiver.
 
#### void onDownloaderAsyncCmdComplete (NexPlayer mp, int msg, int param1, int param2)

This function is called when an asynchronous command in the Downloader module is complete.

This method will be called whenever DownloaderOpen(), DownloaderClose(), DownloaderStart() or DownloaderStop() finish asynchronously.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| data | The asynchronous command completed. This will be one of:<br>- NEXDOWNLOADER\_ASYNC\_CMD\_OPEN = 0x00200001<br>- NEXDOWNLOADER\_ASYNC\_CMD\_CLOSE = 0x00200002<br>- NEXDOWNLOADER\_ASYNC\_CMD\_START = 0x00200003<br>- NEXDOWNLOADER\_ASYNC\_CMD\_STOP = 0x00200004|
| param1 | This integer indicates the result of the command. It will be 0 in the event of success, or will be an error code in the event of failure.| 
| param2 | Additional information, if available, concerning the result reported in param1. For example if the error is invalid response, param2 gives the HTTP status code.|  
 
> Implemented in NexEventReceiver.

#### void onDownloaderError (NexPlayer mp, int msg, int param1)

This function is called when an error is generated by the Downloader module.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| msg | An integer indicating the error generated by the Downloader module.| 
| param1 | This parameter is currently undefined but reserved for future use and should not be used.| 
  
> Implemented in NexEventReceiver.

#### void onDownloaderEventBegin (NexPlayer mp, int param1, int param2)

This method reports when a Downloader event has started.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| param1 | This parameter is currently undefined and is not used but is reserved for future use.| 
| param2 | The total size of the content file to be downloaded.| 
 
> Implemented in NexEventReceiver.

#### void onDownloaderEventComplete (NexPlayer mp, int param1)

This function is called when a Downloader event has completed.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| param1 | This parameter is currently undefined and is not used but is reserved for future use.| 

> Implemented in NexEventReceiver.

#### void onDownloaderEventProgress (NexPlayer mp,int param1,int param2,long param3,long param4)

This function is called to pass the downloading progress of a Downloader event.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| param1 | This parameter is currently undefined and is not used but is reserved for future use.| 
| param2 | The time remaining until the downloading file has saved completely, inmsec(milliseconds).| 
| param3 | The size of the portion of the downloading file already received. in bytes (B).| 
| param4 | The total size of the content file being downloaded, in bytes (B).| 
 
> Implemented in NexEventReceiver.

#### void onDownloaderEventState (NexPlayer mp,int param1,int param2)

This method reports the current state of a Downloader event.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
| param1 | This parameter is currently undefined and is not used but is reserved for future use.| 
| param2 | This is an integer that indicates the current state of the Downloader event. This will be one of:<br>- **NEXDOWNLOADER\_STATE\_NONE = 0**<br>- **NEXDOWNLOADER\_STATE\_CLOSED = 2**<br>- **NEXDOWNLOADER\_STATE\_STOP = 3**<br>- **NEXDOWNLOADER\_STATE\_DOWNLOAD = 4**|

> Implemented in NexEventReceiver.

#### void onEndOfContent (NexPlayer mp)

This method indicates when playback has completed successfully up to the end of the content.

This event occurs when the player reaches the end of the file or stream. In most cases, applications should respond to this by calling NexPlayer.stop and then updating the user interface.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.| 
 
> Implemented in NexEventReceiver.

#### void onError (NexPlayer mp, NexErrorCode errorcode)

An error has occurred during playback.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|  
| errorcode | The error code for the generated error.|  

> Implemented in NexEventReceiver.

#### void onHTTPRequest (NexPlayer mp, String strRequest)

This method allows NexPlayer™ to pass HTTP request messages to an application.

While NexPlayer™ normally handles HTTP requests and responses internally, in cases where additional information is required from the server (for example user cookies), this method can be used in conjunction with `onHTTPResponse` to allow an application to handle that information directly.

> **Note** This should be called before a request is sent to an HTTP server. To modify an HTTP request, see `onModifyHttpRequest`. To handle the response received, call `onHTTPResponse`.
 
**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|  
| strRequest | The HTTP request to be sent to the server, as a string.|   
 
 The HTTP request to be sent to the server, as a string.
 
**See Also**
 
- NexPlayer.onHTTPResponse
- NexPlayer.onModifyHttpResponse
 
> Implemented in NexEventReceiver.


#### void onHTTPResponse (NexPlayer mp, String strResponse)

This method allows responses from an HTTP server to be received and handled in a more customized way.

While NexPlayer™ normally handles HTTP requests and responses internally, in cases where additional information is required from the server (for example user cookies), this method can be used in conjunction with onHTTPRequest to handle that information directly.

> **Note** This should be called after a response has been received from the server. To change the requests being made, onModifyHttpRequest should be called.
 
**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|  
| strResponse | The response from the HTTP server, as a string.|   
 
**See Also**

- NexPlayer.onHTTPRequest
- NexPlayer.onModifyHttpRequest
 
Implemented in NexEventReceiver.

#### String onModifyHttpRequest (NexPlayer mp, int param1, Object input\_obj)

This method provides the HTTP Request that will be used by NexPlayer™ when an HTTP request is modified.

**Parameters**
 
| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|  
| param1 | The length of the current HTTP Request data.|  
| input\_obj | The modified HTTP Request data.|   
 
**Returns**
 
A String with the modified HTTP request. This value will be used by NexPlayer™ instead of the previous HTTP
request.
 
**See Also**

Enabling Modified HTTP Requests for more information.
 
> Implemented in NexEventReceiver.

#### void onPauseSupervisionTimeOut (NexPlayer mp)

Reports Pause Supervision Timeout.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|  

> Implemented in NexEventReceiver.

#### void onPictureTimingInfo (NexPlayer mp, NexPictureTimingInfo[] arrPictureTimingInfo)

This method provides SEI picture timing information about video frames of H.264 content when available.

This method is called when `ENABLE_H264_SEI` is enabled and the H.264 content contains supplemental en-
hancement information (SEI). While SEI may include a variety of attributes, this method specifically receives SEI picture timing information when available.

NexPlayer™ delivers the timing information through this method by passing an instance of NexPictureTimingInfo whenever SEI picture timing information is received.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|  
|arrPictureTimingInfo|The NexPictureTimingInfo object that includes the SEI picture timing information for the content.|
 
> Implemented in NexEventReceiver.

#### void onProgramTime (NexPlayer mp,String strTag,long offset)

This retrieves the program time and date information from HLS content when the #EXT-X-PROGRAM-DATE-TIME
tag is present.

This event happens approximately once every second when a .ts file is decoding (approximately every 30 frames). The `str` Tagvalue will remain the same until a new #EXT-X-PROGRAM-DATE-TIME tag is received in a subsequent segment, whereas the value of the timeoffsetparameter will continuously rise in subsequent frames until a new #EXT-X-PROGRAM-DATE-TIME tag is received.

The values fromstrTagandoffsetparameters can be added to determine the current frame’s timestamp. The
time can then be used to help sync content and text streams or to determine when content should play.

> **Note** If the program time is required at a more specific moment in time, the same information can be retrieved by calling the method, getProgramTime.
 
**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|
|strTag | The most recent #EXT-X-PROGRAM-DATE-TIME tag in the HLS content, as a string.|
|offset|The time offset of the currently decoding frame’s timestamp with respect to the #EXT-X-PROGRAM-DATE-TIME tag time, in milliseconds.|
 
**See Also**
 
getProgramTime

> Implemented in NexEventReceiver.

#### void onRecording (NexPlayer mp,int recDuration,int recSize)

This reports NexPlayer™’s recording status.


**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|  
| recDuration | An integer indicating the duration of the recording so far.|  
| recSize | An integer indicating the size of the recording so far.|   
 
> **Deprecated** Not available in current version; do not use.

> Implemented in NexEventReceiver.

#### void onRecordingEnd (NexPlayer mp,int success)

This indicates when NexPlayer™ recording has ended.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|  
| success | |  

 
> **Deprecated** Not available in current version; do not use.

> Implemented in NexEventReceiver.

#### void onRecordingErr (NexPlayer mp, int err)

This indicates when there has been a NexPlayer™ recording error.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|  
| err | An error while recording. |  
 
> **Deprecated** Not available in current version; do not use.

> Implemented in NexEventReceiver.

#### void onRTSPCommandTimeOut (NexPlayer mp)

Reports RTSP command Timeout.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|  

> Implemented in NexEventReceiver.

#### void onSessionData (NexPlayer mp, NexSessionData[] data)

This method reports the arbitrary session data of the HLS master playlist.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|  
| data | The array of NexSessionData object that includes the arbitrary session data of the HLS master playlist.|  
 
> Implemented in NexEventReceiver.

#### void onSignalStatusChanged (NexPlayer mp, int pre, int now)

NexPlayer™’s signal status has been changed.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|  
| pre | The previous signal status.| 
| now | The current signal status.| 
 
> Implemented in NexEventReceiver.

#### void onStartAudioTask ( NexPlayer mp )

The NexPlayer™ audio task has started.

> **Deprecated** This method is only included for compatibility with older code and should not be used. This is provided for compatibility with older code, and new applications may safely ignore this event.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|  
 
> Implemented in NexEventReceiver.

#### void onStartVideoTask ( NexPlayer mp )

The NexPlayer™ video task has started.

> **Deprecated** This method is only included for compatibility with older code and should not be used.

This is provided for compatibility with older code, and new applications may safely ignore this event.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|  
 
> Implemented in NexEventReceiver.

#### void onStateChanged ( NexPlayer mp, int pre, int now )

NexPlayer™’s state has been changed.

This method is called when NexPlayer™’s state has been changed but it does not mean that the changing operation
has completed. Therefore, the next operation can be carried out only after the event onAsyncCmdComplete is
received, not when this event, onStateChanged, is called.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|
| pre | The previous play status.| 
| mp | The current play status.|
 
> Implemented in NexEventReceiver.

#### void onStatusReport ( NexPlayer mp, int msg, int param1 )

This function is called when there is a change in the available content information.

This can happen, for example, if the track changes during HLS playback, resulting in changes to the bitrate, resolution, or even the codec in use.

The msg parameter contains information about the condition that has changed.

Since multiple calls to this function can be issued for the same event, unknown values for msg should generally be ignored. To handle general status changes that affect content information without processing duplicate
messages, the best approach is just to handle NEXPLAYER\_STATUS\_REPORT\_CONTENT\_INFO\_UPDATED.

To determine the new content information when this event occurs, call getContentInfo or getContentInfoInt.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
| param1 | Additional information. The meaning of this depends on the value of msg. If the description above doesn’t refer to param1, then this parameter is undefined for that value of msg and should not be used.|
| msg | The type of notification. This is one of the following values:| 

- `NEXPLAYER_STATUS_REPORT_NONE (0x00000000)` 
No status change (thisvalue is not normally passed to onStatusReport, and should generally be ignored).

- `NEXPLAYER_STATUS_REPORT_AUDIO_GET_CODEC_FAILED (0x00000001)` 
Failed to determine the audio codec. This notification can happen at the beginningof playback, or during playback if there is an audio codec change. This can happenbecause of a switch to a new codec that NexPlayer™ does not support, or due to anerror in the format of the content or corrupted data in the content.

- `NEXPLAYER_STATUS_REPORT_VIDEO_GET_CODEC_FAILED (0x00000002)` 
Failed to determine the video codec. This notification can happen at the beginningof playback, or during playback if there is a video codec change. This can happenbecause of a switch to a new codec that NexPlayer™ does not support, or due to anerror in the format of the content or corrupted data in the content.

- `NEXPLAYER_STATUS_REPORT_AUDIO_INIT_FAILED (0x00000003)` 
 The audiocodec failed to initialize. This can happen for several reasons. The container mayindicate the wrong audio codec, or the audio stream may be incorrect or corrupted,or the audio stream may use a codec version or features that NexPlayer™ doesn’tsupport.

- `NEXPLAYER_STATUS_REPORT_VIDEO_INIT_FAILED (0x00000004)` 
 The videocodec failed to initialize. This can happen for several reasons. The container mayindicate the wrong video codec, or the video stream may be incorrect or corrupted,or the video stream may use a codec version or features that NexPlayer™ doesn’tsupport.

- `NEXPLAYER_STATUS_REPORT_TRACK_CHANGED (0x00000005)` 
 The track haschanged. This happens for protocols such as HLS that provide the content in multipleformats or at multiple resolutions or bitrates. The ID of the new track can be found in mCurrTrackID, and also in param1. When this event occurs, NexPlayer™ also generates a NEXPLAYER_CONTENT_INFO_UPDATED event.

- `NEXPLAYER_STATUS_REPORT_STREAM_CHANGED (0x00000006)` 
 The streambeing played back has changed (between the states AudioOnly, VideoOnly and Audio+Video). The new stream type is in mMediaType, and also in param1.

- `NEXPLAYER_STATUS_REPORT_DSI_CHANGED (0x00000007)` 
 An attribute relating to the video or audio format (such as the resolution, bitrate, etc.)` 
 has changed.This is considered Decoder Specific Information (DSI).

- `NEXPLAYER_STATUS_REPORT_OBJECT_CHANGED (0x00000008)` 
 One of thecodec objects in use has changed (that is, the audio or video codec in use haschanged). See mAudioCodec and mVideoCodec to get the ID of the new codec.

- `NEXPLAYER_STATUS_REPORT_CONTENT_INFO_UPDATED (0x00000009)` 
 The content information has changed. When onStatusReport is called with any other non Failure value for msg, it will also be called with this as well. This is a good place to monitor insignificant changes to the content information.

- `NEXPLAYER_STATUS_REPORT_DOWNLOAD_PROGRESS (0x00000080)` 
 Reports the progress made storing content for offline play. This message will be calledwhen content is opened with NEXPLAYER_SOURCE_TYPE_STORE_STREAM type.For this notification, the parameterparam1returns the percentage of downloadingcomplete (0
-100).

- `NEXPLAYER_STATUS_REPORT_AVMODE_CHANGED (0x0000000A)` 
 Thestream being played back has changed and the new stream has a different mediatype. This event happens whenever the state changes between video-only, audio-only and audio-video. param1 contains the new media type: 1 for audio, 2 for video, 3 for both.

- `NEXPLAYER_STATUS_REPORT_HTTP_INVALID_RESPONSE (0x0000000B)` 
 An HTTP error response was received from the server.param1 contains the error code(this is a normal HTTP response code, such as 404, 500, etc.)

- `NEXPLAYER_STATUS_REPORT_DISCONTINUITY_EXIST (0x00000012)` 
 There is a discontinuity tag found in the HLS content playlist.

- `NEXPLAYER_STATUS_REPORT_EXTERNAL_DOWNLOAD_CANCELED(0x00000020)` 
 The player canceled External PD Mode and played content onNormal PD Mode. (e.g. The engine attempted to play regular content instead of piffcontent on External PD Mode).

- `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED(0x00000021)` 
 Either the Minimum bandwidth or Maximum bandwidth has beenchanged.

- `NEXPLAYER_STATUS_REPORT_STREAM_RECV_PAUSE (0x00000060)` 
 Whenthe prefetch buffer exceeds the maximum value, the player pauses the buffer control.The user can adjust the maximum value of the prefetch buffer by using setProperty ofthe properties MAX_BUFFER_RATE or MAX_BUFFER_DURATION.

- `NEXPLAYER_STATUS_REPORT_STREAM_RECV_RESUME (0x00000061)` 
 Whenthe prefetch buffer is below the minimum value, the player resumes the buffer control. The user can adjust the mimimum value of the prefetch buffer by using setProperty ofthe properties MIN_BUFFER_RATE or MIN_BUFFER_DURATION.

- `NEXPLAYER_STATUS_REPORT_DOWNLOAD_PROGRESS (0x00000080)` 
 Reports the progress made storing content for offline play. This message will be calledwhen content is opened with NEXPLAYER_SOURCE_TYPE_STORE_STREAM type.For this notification, the parameter param1 returns the percentage of downloadingcomplete (0-100).

- `NEXPLAYER_STATUS_REPORT_MAX (0xFFFFFFFF)` 
 This value is reserved; do not use it.

> Implemented in NexEventReceiver. 
 
#### void onTextRenderInit ( NexPlayer mp, int numTracks )
 
Called when initially beginning playback of media content with associated subtitles.
 
**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
| numTracks | The number of subtitle tracks available for this media. Note that this may be 0 if there are no subtitles, or this function may not be called at all.|
 
> Implemented in NexEventReceiver.
 
#### void onTextRenderRender ( NexPlayer mp, int trackIndex, NexClosedCaption textInfo )
 
This function is called when new subtitle data is ready for display. This is called whenever playback reaches a point in time where subtitles on any track need to be displayed or cleared. The text to display is provided in a NexClosedCaption object as a byte array; it is the responsibility of the application to convert this to text with the appropriate encoding. Where possible, the encoding information will be provided in the NexClosedCaption.mEncodingType, but many subtitle file formats do not explicitly specify an encoding, so it may be necessary for the application to guess the encoding or allow the user to select it. 

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
| trackIndex | This is always zero and should always be ignored.|
| textInfo | The text to be displayed (cast this to a NexClosedCaption object).|
 
> Implemented in NexEventReceiver.

#### void onTime ( NexPlayer mp, int millisec )

This method indicates that playback has progressed to the specified position.

This event occurs once per second. If the application is displaying the current play position, it should update it to reflect this new value.

Applications that wish to update the play time more often that once per second or with a greater accuracy may ignore this event and create their own timer, in which case they can use the current play time reported in NexContentInformation.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|
| millisec | Current play position in milliseconds.|
 
> Implemented in NexEventReceiver.

#### void onTimedMetaRenderRender ( NexPlayer mp, NexID3TagInformation TimedMeta )

This method is called when new timed metadata is ready to be displayed in HLS.

Timed metadata includes additional information about the playing content that may be displayed to the user and this information may change at different times throughout the content. Each time new metadata is available for display, this method is called.

**See Also**

NexID3TagInformation for more details on the available metadata information. 

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
| TimedMeta | An NexID3TagInformation object that contains the timed metadata associated with the content to be displayed.|
 
> Implemented in NexEventReceiver.

#### void onTimeshift ( NexPlayer mp, int currTime, int TotalTime )

This is a deprecated method that formerly reported NexPlayer™’s Time shift status.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object generating the event.|
| currTime | The current time.|
| TotalTime | The total time.| 
 
> **Deprecated** Not available in current version; do not use.

> Implemented in NexEventReceiver.

#### void onTimeshiftErr ( NexPlayer mp, int err )

This is a deprecated method that formerly reported any NexPlayer™ Time shift error.

> **Deprecated** Not available in current version; do not use.

> Implemented in NexEventReceiver.

#### void onVideoRenderCapture ( NexPlayer mp, int width, int height, int pixelbyte, Object bitmap )

Called when a frame of video has been captured.

> **Deprecated** Not available in current version; use IVideoRendererListener instead.

After calling captureVideo to set up video capture, this function will be called whenever a frame is captured, and can process the captured frame as necessary.

```java
Bitmap bitmap = Bitmap.createBitmap(width, height, pixelbyte==2?Config.RGB_565:Config.ARGB_8888 );
ByteBuffer RGBBuffer = (ByteBuffer)rgbBuffer;
RGBBuffer.asIntBuffer();
bitmap.copyPixelsFromBuffer(RGBBuffer);
```

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
| width | The width of the captured frame.|
| height | The height of the captured frame.| 
| pixelbyte | The number of bytes per pixel (2 for RGB565; 4 for RGBA).| 
| bitmap | The object where the captured video frame data is stored.| 
 
> Implemented in NexEventReceiver.

#### void onVideoRenderCreate ( NexPlayer mp, int width, int height, Object rgbBuffer )

This method is called when NexPlayer™ needs the application to create a surface on which to render the video.

> **Deprecated** Not available in current version; use IVideoRendererListener instead.

The application must respond to this by calling setDisplay.

Generally speaking, the application will actually create the surface earlier, during GUI layout, and will simply use the existing handle in response to this call. There are, however, some threading considerations. See setDisplay for details.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
| width | The width of the source video.|
| height | The height of the source video.|
| rgbBuffer | Direct RGB Buffer(RGB565 format). This RGB buffer is shared with NexPlayer™ Engine native code.|
 
> Implemented in NexEventReceiver.

#### void onVideoRenderDelete ( NexPlayer mp )

This method is called when NexPlayer™ no longer needs the render surface.

> **Deprecated** Not available in current version; use IVideoRendererListener instead.

If a surface was created in onVideoRenderCreate, this is the place to destroy it. However, if (as in most cases) an existing surface was used, then this function need not take any special action, other than updating whatever state the application needs to track.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
 
> Implemented in NexEventReceiver.

#### void onVideoRenderPrepared ( NexPlayer mp )

This method is called when NexPlayer™ recognizes which video render type will be used.

> **Deprecated** Not available in current version; use IVideoRendererListener instead.

At first, NexPlayer™ does not know which renderer will be used. When this method is called, the application can determine the video renderer mode by calling GetRenderMode and prepare for the specified video renderer, as in the following example code:

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
					FrameLayout view = (FrameLayout)findViewById(R.id.gl_container);
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
				if(mNexPlayer.GetRenderMode() == NexPlayer.NEX_USE_RENDER_AND)
				{
					mSurfaceHolder.setType(SurfaceHolder.SURFACE_TYPE_NORMAL);//For Gingerbread Android Renderer
				}
				else
				{
					mSurfaceHolder.setType(SurfaceHolder.SURFACE_TYPE_PUSH_BUFFERS);//For HWRenderer
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
 
| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
 
> Implemented in NexEventReceiver.

#### void onVideoRenderRender ( NexPlayer mp )

This requests to display Video frame data at JAVA application.

> **Deprecated** Not available in current version; use IVideoRendererListener instead.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer™ object to which this event applies.|
 
> Implemented in NexEventReceiver.

#### int eNEXPLAYER\_AUDIO\_GET\_CODEC\_FAILED = 0x00000001

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_AUDIO\_GET\_CODEC\_FAILED instead.

#### int eNEXPLAYER\_AUDIO\_INIT\_FAILED = 0x00000003

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_AUDIO\_INIT\_FAILED instead.

#### int eNEXPLAYER\_CONTENT\_INFO\_UPDATED = 0x00000009

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_CONTENT\_INFO\_UPDATED instead.

#### int eNEXPLAYER\_DSI\_CHANGED = 0x00000007

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_DSI\_CHANGED instead.

#### int eNEXPLAYER\_OBJECT\_CHANGED = 0x00000008

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_OBJECT\_CHANGED instead.

#### int eNEXPLAYER\_STATUS\_NONE = 0x00000000

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_NONE instead.

#### int eNEXPLAYER\_STREAM\_CHANGED = 0x00000006

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_STREAM\_CHANGED instead.

#### int eNEXPLAYER\_TRACK\_CHANGED = 0x00000005

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_TRACK\_CHANGED instead.

#### int eNEXPLAYER\_VIDEO\_GET\_CODEC\_FAILED = 0x00000002

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_VIDEO\_GET\_CODEC\_FAILED in-
stead.

#### int eNEXPLAYER\_VIDEO\_INIT\_FAILED = 0x00000004

Possible value for msg parameter of onStatusReport.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_VIDEO\_INIT\_FAILED instead.

#### int NEXPLAYER\_STATUS\_MAX = 0xFFFFFFFF

Possible value for msg parameter of onStatusReport.

This value is deprecated and has been renamed. Use NEXPLAYER\_STATUS\_REPORT\_MAX instead.

> **Deprecated** Renamed; use NexPlayer#NEXPLAYER\_STATUS\_REPORT\_MAX instead.

### GLRenderer.IListener Interface Reference

The application must implement this interface in order to receive notification when the size of the OpenGL surface (the video rendering surface) changes.

This is specfified in the constructor for `GLRenderer`.

Do not confuse this with `NexPlayer.IListener`, a separate interface.



#### void onGLChangeSurfaceSize ( int width, int height )

This method is called when the size of the OpenGL surface has changed.

Whenever the width or height in `GLRenderer`changes, the changed values are passed through the `IListener`.

**Parameters**
 
| Name   | Description                    |
|--------|------------|
| width  | New surface width, in pixels.  |
| height | New surface height, in pixels. |
 
### NexVideoRenderer.IListener Interface Reference

The application must implement this interface in order to receive events from `NexVideoRenderer`.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within *IListener* callbacks. The safest way to update the UI is to use *android.os.Handler* to post an event back to the main application thread.
 
`NexVideoRenderer` will call the methods provided in this interface automatically during playback to notify the application when various events have occurred.

In most cases, the handling of these events is optional; `NexPlayer`™ will continue playback normally without the application doing anything special. For best results, handling all events is recommended.

See each individual *IListener* method for a recommendation on how to handle the event in the application.
 


#### void onDisplayedRectChanged ( )

This callback indicates that the displayed rectangle’s position or size has changed.

This event occurs when `NexVideoRenderer.setOutputPos` is called.

This would be a good time for the application to handle any related layout changes that need to be performed, such as changing the layout of subtitles or the player UI controls.


#### void onFirstVideoRenderCreate ( )

This callback indicates that the `NexPlayer`™ instance has performed its first of possibly many `onVideoRenderCreate` callbacks.

This event occurs when `NexVideoRenderer` first receives the `onVideoRenderCreate` callback from the associated NexPlayer™ instance.

On receiving this callback, the application should call `NexVideoRenderer.setOutputPos` to display the video at the desired resolution and aspect ratio.
 
#### void onSizeChanged ( )

This callback indicates that the size of the `NexVideoRenderer FrameLayout` has changed.

This event could occur when the device is rotated or the application requests the view to change size.

On receiving this callback, the application should call `NexVideoRenderer.setOutputPos` to display the video at the
desired resolution and aspect ratio.
 
#### void onVideoSizeChanged ( )

This callback indicates that the size of the media content has changed.

This event will occur at least once when first starting playback.

On receiving this callback, the application should call `NexVideoRenderer.setOutputPos` to display the video at the
desired resolution and aspect ratio.
 
### INexDRMLicenseListener Interface Reference

The application must implement this interface in order to receive events from `NexPlayer`.

#### byte [ ] onLicenseRequest ( byte[ ]requestData)**

This method provides the license request data that will be used by DRM Client.

**Parameters**
 
| Name        | Description                              |
|-------------|----------------------|
| requestData | requestData is the license request data. |
 
**Returns**

 
A *Object* with license response data. DRM Client will use this *string* without any modification. If modification is not needed, then the UI should return null.
 
### NexStatisticsMonitor.InitialStatisticsMetric Enum Reference

This is an enumeration of the possible initial statistics that can be requested when initializing playback of HLS, DASH or SS content in `NexPlayer`™.

Since this statistics metric is only for monitoring the statistics related to the initialization of content, for more general playback statistics, monitor *GeneralStatisticsMetric* instead.

**See Also**
 
`GeneralStatisticsMetric`
 

#### int getCode ()

Gets the initial statistic code, as an integer.

**Returns**

The initial statistics code, as an integer.
 
> Implements `NexStatisticsMonitor.IStatistics`.

#### CONTENT\_DURATION = ( 0x00000090 )

The total duration of the current content, as an integer.

This is the same as `NexContentInformation.mMediaDuration`.

#### INITIAL\_PLAYLIST = ( 0x00000060 )

The full content of the initial manifest playlist, as a *String*.

This is the same as *NexRTStreamInformation.mInitialMpd*.

#### INITIAL\_PLAYLIST\_URL = ( 0x00000070 )

The actual URL (after all redirects) of the initial request for the manifest playlist, as a *String*.

This is the same as *NexRTStreamInformation.mInitialMpdUrl*.

#### MASTER\_PLAYLIST = ( 0x00000040 )

The full content of the master manifest playlist, as a *String*.

This is the same as *NexRTStreamInformation.mMasterMpd*.

#### MASTER\_PLAYLIST\_URL = ( 0x00000050 )

The URL of the master manifest playlist, as a *String*.

This is the same as *NexRTStreamInformation.mMasterMpdUrl*.

#### NUM\_PREBUFFERED\_SEGMENTS = ( 0x00000020 )

The total number of segments loaded in the buffer, as an integer.

This is the same as *NexRTStreamInformation.mNumOfSegInBuffer*.

#### NUM\_REDIRECTS = ( 0x00000030 )

The total number of redirects, as an integer.

This is the same as *NexRTStreamInformation.mNumOfRedirect*.

#### NUM\_TRACK = ( 0x00000010 )

The total number of tracks in the current content, as an integer.

#### START\_SEGMENT\_URL = ( 0x00000080 )

The description of the initially selected profile, as a *String*.

This is the same as *NexRTStreamInformation.mStartSegUrl*.

### NexPlayer.IOfflineKeyListener Interface Reference


#### void onOfflineKeyExpiredListener (NexPlayer mp)

This method will be called by the `NexPlayer`™ engine when the keyId of media DRM should be expired.

**Parameters**

| Name | Description                                 |
|------|-------------------------|
| mp   | The NexPlayer™ object generating the event. |
 
**Returns**

 
the key ID of media drm stored with onOfflineKeyStoreListener.
 
 
Implemented in `NexEventReceiver`.

#### byte [ ] onOfflineKeyRetrieveListener (NexPlayer mp)

This method will be called by the `NexPlayer`™ engine when the keyId of media DRM should be retrieved.

**Parameters**

 
| Name | Description                                 |
|------|-------------------------|
| mp   | The NexPlayer™ object generating the event. |

 
**Returns**

 
the key ID of media drm stored with onOfflineKeyStoreListener.
 
 
Implemented in `NexEventReceiver`.

#### void onOfflineKeyStoreListener (NexPlayer mp, byte[ ]keyId)

This method will be called by the `NexPlayer`™ engine when the keyId of media DRM should be stored.

**Parameters**

 
| Name  | Description                                     |
|-------|---------|
| mp    | The `NexPlayer`™ object generating the event. |
| keyId | The Key ID of Media drm for offline playback.   |
 
**Returns**

 
void.
 
 
Implemented in `NexEventReceiver`.

### NexOfflineStoreController.IOfflineStoreListener Interface Reference

This interface allows the application to get events about the Offline Store from `NexOfflineStoreController`.

When stroing data to `NexOfflineStoreController`, the user must call `setListener(IOfflineStoreListener i)` to get events
before startOfflineStore. When the user wants to call an API that edits UI-related APIs or the state of OfflineStore
such as `stopOfflineStore()` from `IOfflineStoreListener` callback, they must use a Handler in order for the API to be
able to run on the main application thread.




#### void onDownloadEnd ( boolean completed)

This event is called when the download is complete.

**Parameters**

 
| Name      | Description                                                                                                               |
|-----------|-------------------|
| completed | Set to *TRUE* for when the content is completely downloaded. Call stopOfflineStore after onDownloadEnd(true) is received. |
 
#### void onDownloading ( int percentage)

This event reports the end of download.

**Parameters**

 
| Name      | Description                                                                                                               |
|-----------|-------------------|
| percentage |  |
 
#### void onError ( NexPlayer.NexErrorCode errorCode)

This event is called when there is an error.

**Parameters**

| Name      | Description                                                                                                               |
|-----------|-------------------|
| errorCode | The error code for the generated error. |

 
### NexPlayer.IReleaseListener Interface Reference

This interface can be implemented in an application in order to receive `NexPlayer`™ release events from `NexPlayer`™.

In most cases, the handling of these events is optional; `NexPlayer`™ will continue playback normally without the
application doing anything special in response to the events received.

**See Also**

- `NexPlayer.addReleaseListener`

- `NexPlayer.removeReleaseListener`
 
 
### NexStatisticsMonitor.IStatistics Interface Reference


This interface defines a set of statistics to be received from `NexPlayer`™ *about* HLS, DASH or SS playback.

Every set of statistics (general, initial, HTTP, and system statistics) implements this interface.

**See Also**

 
- GeneralStatistics

- InitialStatistics

- HTTPStatistics

- SystemStatistics
 
 


#### int getCode ( )

This method gets a statistics code.

Implemented in `NexStatisticsMonitor.SystemStatisticsMetric`, `NexStatisticsMonitor.HttpStatisticsMetric`, `Nex-
StatisticsMonitor.InitialStatisticsMetric`, and `NexStatisticsMonitor.GeneralStatisticsMetric`.


### NexStatisticsMonitor.IStatisticsListener Interface Reference

This interface defines the listener that will be used to receive statistics related to playback.

Any listener created to receive statistics from `NexPlayer`™ must implement this interface.

Once an instance of *NexStatisticsMonitor* is created, a statistics listener implementing this interface can
be set with *setListener(IStatisticsListener listener)*.

**See Also**

 
- `setListener`

 


#### void onUpdated (int statisticsType, HashMap < IStatistics, Object > map)

This method is called whenever statistics are updated and sent by `NexPlayer`™.

The time interval at which general and system statistics are updated in *NexStatisticsMonitor* can be
changed by calling the *setDuration()* method.

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="5">statistics Type</th>
</tr>
  <tr><td><b>STATISTICS_GENERAL</b>= 0, for general playback statistics</td></tr>
  <tr><td><b>STATISTICS_INITIAL</b>= 1, for initial statistics when playback starts</td></tr>
  <tr><td><b>STATISTICS_HTTP</b>= 2, for HTTP statistics during playback</td></tr>
  <tr><td><b>STATISTICS_SYSTEM</b>= 3, for system statistics during HLS, DASH or SS playback</td></tr>
</table>
 
| Name | Description                                   |
|------|---------------------------|
| map  | The updated statistics object as a *HashMap*. |
 
**See Also**

 
- `setDuration`
  
### NexPlayer.IVideoRendererListener Interface Reference

The application must implement this interface in order to receive video renderer-specific events from NexPlayer™.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may
not be safe to call UI-related functions from within *IListener* callbacks. The safest way to update the UI is
to use *android.os.Handler* to post an event back to the main application thread.
 

> **Note** This interface replaces the deprecated methods in `IListener` that received video renderer-specific events from
`NexPlayer`™. Note that in existing older applications, the video renderer related methods of `IListener` (now
deprecated) can be reused.
 
`NexPlayer`™ will call the methods provided in this interface automatically during playback to notify the application
when various video renderer-specific events have occurred.

In most cases, the handling of these events is optional; `NexPlayer`™ will continue playback normally without the
application doing anything special. There are a few exceptions to this which are listed below.

See each individual *IVideoRendererListenermethod* for a recommendation on how to implement that
method in your application.

**See Also**

 
- `NexPlayer.setVideoRendererListener`

- `NexVideoRenderer`
 
 


#### void onVideoRenderCapture (NexPlayer mp, int width, int height, int pixelbyte, Object bitmap)

Called when a frame of video has been captured.

After calling `captureVideo` to set up video capture, this function will be called whenever a frame is captured, and can
process the captured frame as necessary.

```java
	Bitmap bitmap = Bitmap.createBitmap(width, height, pixelbyte==2?Config.RGB\_565:Config.ARGB\_8888 );
	ByteBuffer RGBBuffer = (ByteBuffer)rgbBuffer;
	RGBBuffer.asIntBuffer();
	bitmap.copyPixelsFromBuffer(RGBBuffer);
```

**Parameters**

 
| Name      | Description                                               |
|-----------|-------------------|
| mp        | The `NexPlayer`™ object to which this event applies.    |
| widht     | The width of the captured frame.                          |
| height    | The height of the captured frame.                         |
| pixelbyte | The number of bytes per pixel (2 for RGB565; 4 for RGBA). |
| bitmap    | The object where the captured video frame data is stored. |
 
Implemented in `NexEventReceiver`.

#### void onVideoRenderCreate (NexPlayer mp,int width,int height,Object rgbBuffer)

This method is called when `NexPlayer`™ needs the application to create a surface on which to render the video.

The application must respond to this by calling `setDisplay`.

Generally speaking, the application will actually create the surface earlier, during GUI layout, and will simply use
the existing handle in response to this call. There are, however, some threading considerations. See `setDisplay` for
details.

**Parameters**

 
| Name      | Description                                                                                         |
|-----------|---------------------|
| mp        | The `NexPlayer`™ object to which this event applies.                                              |
| widht     | The width of the source video.                                                                      |
| height    | The height of the source video.                                                                     |
| pixelbyte | Direct RGB Buffer(RGB565 format). This RGB buffer is shared with `NexPlayer`™ Engine native code. | 
Implemented in `NexEventReceiver`.

#### void onVideoRenderDelete (NexPlayer mp)

This method is called when `NexPlayer`™ no longer needs the render surface.

If a surface was created in *onVideoRenderCreate*, this is the place to destroy it. However, if (as in most cases)
an existing surface was used, then this function need not take any special action, other than updating whatever state
the application needs to track.


**Parameters**

 
| Name | Description                                            |
|------|----------------|
| mp   | The `NexPlayer`™ object to which this event applies. | 
Implemented in `NexEventReceiver`.

#### void onVideoRenderPrepared (NexPlayer mp)

This method is called when `NexPlayer`™ recognizes which type of video renderer will be used.

At first, `NexPlayer`™ does not know which renderer will be used. When this method is called, the application can
determine the video renderer mode by calling `GetRenderMode` and prepare for the specified video renderer, as in
the following example code:

```java
	public void onVideoRenderPrepared(NexPlayer mp) {
		if(mNexPlayer.GetRenderMode() == NexPlayer.NEX\_USE\_RENDER\_OPENGL) {
			UseOpenGL = true;
			mHandler.post(new Runnable() {
				public void run() {
					mVideoSurfaceView.setVisibility(View.INVISIBLE);
					int colorDepth = 4;
					if(glRenderer == null)
					{
						glRenderer = new GLRenderer(mContext, mNexPlayer, this, colorDepth);
						FrameLayout view = 	(FrameLayout)findViewById(R.id.gl\_container);
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
				if(mNexPlayer.GetRenderMode() == NexPlayer.NEX\_USE\_RENDER\_AND){
						mSurfaceHolder.setType(SurfaceHolder.SURFACE\_TYPE\_NORMAL);//For Gingerbread Android Renderer
				}
				else
				{
					mSurfaceHolder.setType(SurfaceHolder.SURFACE\_TYPE\_PUSH\_BUFFERS);//For HW Renderer
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
| mp   | The `NexPlayer`™ object to which this event applies. |
 
Implemented in `NexEventReceiver`.

#### void onVideoRenderRender (NexPlayer mp)

This requests to display Video frame data at JAVA application.

**Parameters**

 
| Name | Description                                            |
|------|----------------|
| mp   | The `NexPlayer`™ object to which this event applies. |
 
Implemented in `NexEventReceiver`.

### NexWVDRMSession.IWVDRMSessionListener Interface Reference

**Public Member Functions**

- `void processResonsde (byte[ ] arrResponse, long cach)`

### NexStatisticsMonitor.MediaType Enum Reference

An enumeration defining the possible types of HLS, DASH or SS media can be played by `NexPlayer`™.

These media types include:

- `NONE= 0` : No media file found.
- `AUDIO = 1` : Audio content.
- `BASEVIDEO = 2` : Base video content.
- `TEXT = 4` : Text content or subtitles.
- `ENHANCEDVIDEO = 8` : Enhanced video content.

**See Also**

 
- GeneralStatistics

- `isMediaExist( MediaType mediaType, int mediaComposition )`
 
 


#### int getCode ( )

Gets the integer code for the `MediaType`.

**Returns**

The integer code for the specified `MediaType`.
 
 
#### static boolean isMediaExist (MediaType mediaType,int mediaComposition) *[static]*

This method indicates whether or not the requested media exists in the current content.

This method can be used to check if the current content contains the specific media (*AUDIO,BASEVIDEO,TEXT,ENHANCEDVIDEO*) based on the *mediaComposition* value received.

**Parameters**

 
| Name              | Description                                                                                                                                                                                                                     |
|-------------------|-----------------|
| mediaType         | The type of media to check. This will be one of: •*AUDIO* (0x00000001): for audio media. •*BASEVIDEO* (0x00000002): for base video. •*TEXT* (0x00000004): for text or subtitles. •*ENHANCEDVIDEO* (0x00000008): for enhanced video. |
| media-Composition | The composition of the specified media, as an integer.                                                                                                                                                                          |
 
**Returns**

 
*TRUE* if the media indicated exists, or *FALSE* if it does not exist in the current content.
  
### MPDDescrambleManager Class Reference

This class allows `NexPlayer`™ to support and handle encrypted SmoothStreaming manifests or HLS playlists.

`NexPlayer`™ implements this when it receives the manifest or top level of a playlist so that it may be decrypted if
required.

As illustrated in the sample code, this registers the MPDDescramble callback function to handle any necessary
decryption of encrypted manifests or playlists.

```java
	MPDDescrambleManager drmManager = new MPDDescrambleManager();
	String strEnginePath;
	strEnginePath = "/data/data/com.nexstreaming.nexplayersample/lib/libnexplayerengine.so";
	drmManager.initManager(strEnginePath);
```
 
> **Deprecated** For internal use only. Please do not use.



#### static native int initManager (String strEngineLibName) *[static]*

Initializes and registers the `MPDDescrambleManager`.

**Parameters**
 
| Name             | Description                                   |
|------------------|---------------------------|
| strEngineLibName | The relevant engine library name as a string. |
 
#### static native int initManagerMulti (Object nexPlayerHandle,String strEngineLibName) *[static]*

> Internal use only. Please do not use.

### NexNetAddrTable.NetAddrTableInfo Class Reference

This class defines the information possible for an entry made with the method *8addEntry*, including the hostname and its corresponding IP address when a customized IP address is desired.
 
### Nex3DAudioSolution01 Class Reference

This class allows `NexPlayer`™ to handle audio and convert to 3D audio.

#### int setEuler ( float pitch,float yaw,float roll)

This method sets the pitch, yaw and roll euler angles.

**Parameters**

| Name  | Description                                       |
|-------|-----------|
| pitch | The pitch is pitch degrees around the x axis.     |
| yaw   | The yaw value is yaw degrees around the y axis.   |
| roll  | The roll value is roll degrees around the z axis. |
 
#### int setPositionAngle (float x, float y, float z, float angle)

This method sets the Position Vector and Angle.

**Parameters**

| Name  | Description                                                   |
|-------|-----------------------|
| x     | The x position that represents a vector or point in 3D space. |
| y     | The y position that represents a vector or point in 3D space. |
| z     | The z position that represents a vector or point in 3D space. |
| angle | The angle rotating degrees about axis(x or y or z).           |
 
#### int setQuaternion (float w, float x, float y, float z)

This method sets the quaternion value.

**Parameters**

| Name | Description                                                       |
|------|---------------------------|
| w    | The w of quaternion that used to represent a rotation in 3D space |
| x    | The x of quaternion that used to represent a rotation in 3D space |
| y    | The y of quaternion that used to represent a rotation in 3D space |
| z    | The z of quaternion that used to represent a rotation in 3D space |

### NexABRController Class Reference

This class allows applications to control and use ABR-related methods within the `NexPlayer`™ SDK.

An instance of *NexABRController* can be called once `NexPlayer`™ has been created and initialized.


**Classes**

- `interface IABREventListener`
    
    This interface must be implemented in order for the application to receiveABRControlevents from *NexABRController*.
- `enum SegmentOption`
    
    This enum defines the options possible for how `NexPlayer`™ should handle existing buffered content as a track
    changes (due to a set target bandwidth).
- `enum TargetOption`
    
    This enumeration defines the possible options for how an application should use a target bandwidth set.

 
#### NexABRController(NexPlayer mp)

Sole constructor for *NexABRController*.

The application must create an instance of the *NexABRController* class to control ABR-related methods which
for example change the minimum/maximum allowed bandwidths or the target bandwidth for streaming content with
multiple tracks.
 


#### NexErrorCode changeMaxBandWidth(int maxBwBps)

This method sets the maximum bandwidth for streaming playback dynamically during playback.

This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of
HLS). The player will not consider any track over the maximum bandwidth when determining whether a track change
is appropriate, even if it detects more bandwidth available.

**Parameters**

| Name     | Description                                 |
|----------|-------------------------|
| maxBwBps | Maximum bandwidth in bps (bits per second). |
 
**Returns**

 
NexErrorCode
 
#### NexErrorCode changeMinBandWidth(int minBwBps)

This method sets the minimum bandwidth for streaming playback dynamically during playback.

This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of H-
LS). The player will not consider any track under the minimum bandwidth when determining whether a track change
is appropriate, even if it detects less bandwidth available.

**Parameters**

| Name     | Description                                 |
|----------|-------------------------|
| minBwBps | Minimum bandwidth in bps (bits per second). |
 
**Returns**

 
NexErrorCode
 
 
#### NexErrorCode changeMinMaxBandWidth(int minBwBps, int maxBwBps)

This method sets the minimum and maximum bandwidth for streaming playback dynamically during playback.

This applies in cases where there are multiple tracks at different bandwidths (such as in the case of HLS). The
player will not consider any track under the minimum, and over the maximum bandwidth when determining whether
a track change is appropriate, even if it detects less, and more bandwidth available.

**Parameters**

 
| Name     | Description                                 |
|----------|-------------------------|
| minBwBps | Minimum bandwidth in bps (bits per second). |
| maxBwBps | Maximum bandwidth in bps (bits per second). |
 
**Returns**

 
NexErrorCode
  
#### NexErrorCode setABREnabled(boolean enabled)

This method sets whether ABR methods should be used or not.

In general, `NexPlayer`™ plays streaming content, including content with multiple tracks at different bandwidths such
as HLS, by choosing the optimal track according to network conditions and device performance. This is the default
behavior of `NexPlayer`™ and this occurs when ABR is enabled (or calling *setABREnabled* with the parameter
enabledset to *TRUE*).

However, there may be instances when an application may want to set limits on which tracks should be selected
and played by `NexPlayer`™ in order to provide a specific user experience, and to force `NexPlayer`™to stay on a
particular bandwidth track, regardless of network conditions. In cases like this, in order to keep playing a track at
a target bandwidth (set with *setTargetBandWidth*) this method must be called to disable `NexPlayer`™’s ABR
behavior (with the parameter *enabled* set to *FALSE*).

> **Warning** This method must be called with *enabled* set to *FALSE* `before` calling *setTargetBandWidth* if the
application should continue playing the target bandwidth regardless of network conditions.
 
**Parameters**

| Name    | Description                                                                                                                                                                                                      |
|---------|--------------------------|
| enabled | - `TRUE` : ABR enabled. `NexPlayer`™ will handle track changes automatically. - `FALSE` : ABR disabled. `NexPlayer`™ will continue playing the target bandwidth track     set, regardless of network conditions. |

**Returns**

 
NexErrorCode
 
**See Also**

 
- `setTargetBandWidth`
  

#### void setIABREventListener(IABREventListener listener)

This method sets and registers an *IABREventListener* listener for the application playing content with `NexPlayer`™.


**Parameters**

 
| Name     | Description           |
|----------|-----------------------|
| listener | `IABREventListener` |
 
**See Also**

 
- `NexABRController.IABREventListener`
  
#### NexErrorCode setTargetBandWidth(int targetBwBps, SegmentOption segOption, TargetOption targetOption)

This method sets the target bandwidth for streaming playback dynamically during playback.

This method should be called after `NexPlayer.open()`. This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the target bandwidth and over the target bandwidth when determining whether a track change is appropriate, even if it detects less and more bandwidth available.

**Parameters**

 
| Name         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|--------------|----------------|
| targetBwBps  | Target bandwidth in bps (bits per second).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
| segOption    | One of the following SegmentOption values, indicating how to handle buffered content when the track changes:  **DEFAULT** : Default (NexPlayer will decide between QUICKMIX (changing tracks     quickly) and LATEMIX (playing buffered content and changing tracks more slowly)). **QUICKMIX** : NexPlayer will clear the buffer as much as possible and will start to download new track so user can see a new track faster. **LATEMIX** : NexPlayer will preserve and play the content segments already buffered and will download a new track. |
| targetOption | How to use the target bandwidth value set. One of the following TargetOption options: **DEFAULT** : Default target option (BELOW) **BELOW** : Select a track with a bandwidth below the target bandwidth. **ABOVE** : Select a track with a bandwidth above the target bandwidth. **MATCH** : Select the track that has a bandwidth that matches the target set; otherwise send an error and no new target bandwidth is selected.                                                                                                                          |

**Returns**
 
NexErrorCode
 
**See Also**
 
- TargetOption
- SegmentOption
- setABREnabled
 
 
### NexALFactory Class Reference

The primary interface to the `NexALFactory`.

`NexALFactory` handles codecs and renderer selection for the `NexPlayer`™ SDK starting from `NexPlayer`™ SDK version 6.0. To use the `NexPlayer`™ SDK, the application must create an instance of the `NexALFactory` class (supplied as part of the `NexPlayer`™ SDK).

In addition, an application must also do the following:

1. Create an instance of `NexPlayer` ™ and an instance of `NexALFactory` and set the codec usage policy.

 	```java
		mNexPlayer = new NexPlayer();
		mNexALFactory = new NexALFactory();
	```
 
2. Call the `NexALFactory.init` method, passing the model name of the current device.

 	```java
		mNexALFactory.init(this, android.os.Build.MODEL, android.os.Build.MODEL, nLogLevel, colorDepth);
		mNexPlayer.setNexALFactory(mNexALFactory);
		mNexPlayer.init(this, 1);
	```
 
3. After playback by `NexPlayer`™, `NexALFactory.release` should be called when instances of `NexPlayer`™ and
    `NexALFactory` are no longer needed.

 	```java
		mNexPlayer.release();
		mNexALFactory.release();
	```
 
**Classes**

- `interface ICodecDownListener`
- `enum NexALFactoryErrorCode`
   
    Possible error codes that can be returned by `NexPlayer`™’s *NexALFactory*.

**Protected Member Functions**

- `native void setExternalSurfaceMode (int mode)`
- `void finalize ()`
    
    Releases native resources.

**Static Protected Attributes**

- `static final int NEX\_EXTERNAL\_VIEW\_SURFACETEXTURE = 1`


#### NexALFactory( )

Sole constructor for `NexALFactory`;.

After constructing a `NexALFactory` object, you must call `NexALFactory.init` before you can call any other methods.



#### native int cancelDownloadCodec ( )

This method cancels a codec download.

**Returns**

 
Zero if successful or a non-zero error code.

 
#### static native int canUseNativeDecoder (String strDeviceModel, int sdkInfo) *[static]*

Checks whether the current device can use native decoders or not.

**Parameters**
 
| Name           | Description                                                                                                                                                                                                                                                                                                                                                     |
|----------------|---------------------|
| strDeviceModel | Device model name. Under normal (production) use, you should pass the MODEL as available via the Android API *inandroid.os.Build.MODEL*.                                                                                                                                                                                                                      |
| sdkInfo        | The Android SDK version number. Refer to NexSystemInfo.getPlatformInfo()   - 0x15 : SDK version 1.5 CUPCAKE - 0x16 : SDK version 1.6 DONUT - 0x21 : SDK version 2.1 ECLAIR - 0x22 : SDK version 2.2 FROYO - 0x30 : SDK version 2.3 GINGERBREAD - 0x31 : SDK version 3.0 HONEYCOMB - 0x40 : SDK version 4.0 ICECREAM SANDWICH - 0x41 : SDK version 4.1 JELLYBEAN |

**Returns**

 
An integer greater than 0 if native decoder can be used; and 0 or less than 0 if the native decoder cannot be
used.
 
- 0 : A device where the native decoder cannot be used.
- 1 : Devices that are expected to support hardware codecs.
- 2 : specific devices that are verified to support hardware codecs.

#### int downloadCodec (NexCodecInformation codecInfo)

This method downloads a codec.

> **Warning** This must be called after `NexALFactory.getDownloadableCodecs` has been called.
 
After a codec is downloaded by calling this method, the application should also call *`NexALFactory.rescanCodecs` to
inform `NexPlayer`™ of the newly available codecs.

**Parameters**
 
| Name      | Description                                                     |
|-----------|-------------------------|
| codecInfo | A `NexCodecInformation` object of the codec to be downloaded. |
 
**Returns**

 
Zero if successful or a non-zero error code.
 
**See Also**

 
- `rescanCodecs`
  
#### NexCodecInformation[ ] getAvailableCodecs ( )

This method retrieves the codec list that can be used.

This must be called `after` `NexALFactory.init` has been called.

**Returns**

 
An array of the available codecs as `NexCodecInformation` objects.
 
**See Also**

 
- `NexCodecInformation`
 
#### NexCodecInformation[ ] getDownloadableCodecs ( )

This method retrieves a list of the codecs that can be downloaded.

This must be called `after` `NexALFactory.init` has been called.

**Returns**

 
An array of the codecs available to be downloaded from the server.
 

 
#### long getNexALFactoryContext ( )

Returns the NexALFactoryContext.

This method is called by the `NexPlayer`™ Engine. This is just for native methods. Don’t use this method for other
purposes.

#### boolean init (Context context, String strModel, String strRenderMode, int logLevel, int colorDepth)

Initializes `NexALFactory`.

`NexPlayer`™ automatically detects the devices where HW codecs and H.264 Main/High profiles can be supported
so there is no need to indicate any specific device model to the player.

> **Warning** Although it is possible to change the device model parameter, *strModel*, it is not recommended because
changing the model name may result in the H/W decoder not working properly. Please do NOT change
the device model name in the sample code. Similarly, although it is possible to change the render mode
parameter, *strRenderMode*, `NexPlayer`™ is only guaranteed to work properly with *strRenderMode*
set to *NEX\_DEVICE\_USE\_AUTO*. Please do NOT change the render mode in the sample code.

**Parameters**

 
| Name          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|---------------|------------------------|
| context       | The current context; from *Activity* subclasses, you can just pass *this*.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| srtModel      | Device model name. `NexPlayer`™ includes multiple renderer modules, and past versions of the player selected the module most suitable to the device based on this value. The renderer is now set by the parameter *strRenderMode*. Under normal use, you should pass the MODEL as available via the Android API in *android.os.Build.MODEL*. For example:  	*nexALFactory.init(this, android.os.Build.MODEL, 	NEX\_DEVICE\_USE\_AUTO, 0, 1);*     `NexPlayer`™ uses this to select the most appropriate renderer if no renderer is selected (*NULL* is passed) with the parameter *strRenderMode* below. For OS versions up to Gingerbread, this is always the Android Renderer (although from Froyo, other renderers are supported as well) if the SW codec is in use. For Honeycomb and Ice Cream Sandwich (ICS), this is always the OpenGL renderer when the SW codec is in use.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| srtRenderMode | The Renderer to use, as a string. The recommended render mode to use is *NEX\_DEVICE\_USE\_AUTO*, which will choose the most appropriate render mode automatically. For devices that support the hardware codec, this will be:   - `NEX\_USE\_RENDER\_IOMX.` For devices that don’t support the hardware codec, this     will be one of the software renderers. While most devices should work properly with     OpenGL, occasionally another rendering module may be beneficial, for example if a device supports 3D rendering, if an application doesn’t implement support for the OpenGL renderer, or for devices running older versions of the Android OS. In some other     cases, such as the Kindle Fire running on Gingerbread, while the default renderer is     Android, the OpenGL renderer is recommended because of improved performance.     The available software renderers are:        `- NEX\_DEVICE\_USE\_AUTO ("Auto")` Added in `NexPlayer` SDK version 6.1.2, this           chooses which renderer to use automatically.        `- NEX\_DEVICE\_USE\_ONLY\_ANDROID ("Android")` Use only standard Android           API bitmaps to display frames. This is usually slower, but is more portable.        `- NEX\_DEVICE\_USE\_JAVA ("JAVA")` Use the Java renderer.        `- NEX\_DEVICE\_USE\_OPENGL ("OPENGL")` Use the OpenGL renderer.        `- NEX\_DEVICE\_USE\_ANDROID\_3D ("Android 3D")` Use the 3D video renderer           with standard Android API bitmaps. |
| logLevel      | `NexPlayer`™ SDK logging level. This affects the messages that the SDK writes to the Android log.   - **-1** : Do not output any log messages. (If you do not want to output any log messages     in NexPlayerSample App, you should set the loglevel to 0xF0000000.) - **0** : Output basic log messages only (recommended). - **1** ∼ **4** : Output detailed log messages; higher numbers result in more verbose log entries, but may cause performance issues in some cases and are not recommended for general release code.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| colorDepth    | colorDepth Video output image color depth.   - **1** : RGBA\_8888 - **4** : RGB\_565                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

**Returns**

 
*TRUE* if initialization succeeded; *FALSE* in the case of a failure (in the case of failure, check the log for details).
 
**See Also**

 
- NexPlayer.getRenderMode for more details.
 
#### void release ( )

This method releases resources used by the `NexALFactory` instance.

This should be called when the instance is no longer needed. After calling this method, the instance can no longer
be used.

#### native int rescanCodecs ( )

This method rescans the codec files in the application files directory(*/data/data/<package\_name>/files*) to update the codecs available in `NexPlayer`™.

> **Warning** This must be called after `NexALFactory.init` has been called.
 
Any time an application downloads an additional codec by calling `NexALFactory.downloadCodec`, this method
should be called to inform `NexPlayer`™ of the newly available codecs.

**Returns**

 
Zero if successful, or a non-zero error code.


#### int setAppUniqueCode (String strAppUCode)

This method sets the unique App code provided.

This must be called `after` `NexALFactory.init` has been called.

**Parameters**

| Name        | Description                   |
|-------------|-----------|
| strAppUCode | The provided unique App code. |
 
**Returns**

Zero if successful, or a non-zero error code.
  
#### void setCodecDownloadListener (ICodecDownListener listener)

>**Warning** This method is for internal NexStreaming usage only. Please do not use.

 
### NexALFactory.NexALFactoryErrorCode Enum Reference

Possible error codes that can be returned by `NexPlayer`™’s *NexALFactory*.

This is a Java *enum* so each error constant is an object, but it can be converted to or from a numerical code using
the instance and class methods.

To get the error constant of a given code, call: `fromIntegerValue(int)`.

To get the error description given an error constant, call: `getDesc()`.

To get the error code given an error constant, call: `getIntegerCode()`.

Because this is a Java *enum*, it is very easy to include the name of the error constant in error messages instead of
just the number values. For example, the following code logs the errors that are received from `NexALFactory`:

```java
	void onCodecDownloaderEventError(NexALFactoryErrorCode errorCode) {
	{
		NexLog.d( "onError",
			"Received the error: "
				+ errorCode.getDesc()
				+ " ("
				+ errorCode.getIntegerCode()
				+ ")."
		);
	}
```

**Public Attributes**

- `ERROR_SW_CODEC_DOWNLOAD_INTERNAL_ERROR` = (-1, "Internal error or invalid socket handle.")
- `ERROR_SW_CODEC_DOWNLOAD_RECV_TIME_OUT` = (-2, "Receive time out.")
- `ERROR_SW_CODEC_DOWNLOAD_DNS_FAIL` = (-9, "DNS lookup failure.")
- `ERROR_SW_CODEC_DOWNLOAD_CONNECTION_FAIL` = (-11, "Connection failure.")


#### static NexALFactoryErrorCode fromIntegerValue (int code) *[static]*

This method gets the error code of a given *NexALFactoryError*, from a given integer value.

#### String getDesc ( )

This method gets the description of a given *NexALFactoryError*, given an error constant.

#### int getIntegerCode ( )

This method gets the integer code for a given *NexALFactoryError*.

### NexCaptionAttribute Class Reference

This class manages the properties of captions.

**Classes**

- `enum EdgeStyle`
    
    This enumeration defines the caption edge style.

**Protected Member Functions**

- `boolean withinRangeOfOpacity (int value)`
- `boolean withinRangeOfScaleFactor (float value)`

**Protected Attributes**

- `float mScaleFactor` = 1.0f
- `float mStrokeWidth` = 1.0f
- `EdgeStyle mEdgeStyle` = EdgeStyle.NONE
- `int mFontOpacity` = 255
- `int mEdgeOpacity` = 255
- `int mBackgroundOpacity` = 255
- `int mWindowOpacity` = 255
- `CaptionColor mFontColor` = CaptionColor.WHITE
- `CaptionColor mEdgeColor` = CaptionColor.BLACK
- `CaptionColor mBackGroundColor` = CaptionColor.BLACK
- `CaptionColor mWindowColor` = CaptionColor.BLACK


#### NexCaptionAttribute(NexCaptionAttribute settings)

Constructor of `NexCaptionAttribute`.

The attributes will be generated by initializing settings object values.

**Parameters**

| Name     | Description                       |
|----------|---------------|
| settings | A `NexCaptionAttribute` object. |
 


#### Object getValue (int attr)

This method gets the value of an individual `NexCaptionAttribute` attribute.

**Parameters**


| Name     | Description                       |
|----------|---------------|
| attr | The attibute to get |
 
**Returns**

 
The value of the attribute.
 
 
#### boolean setValue (int attr,CaptionColorv alue)

This method sets the value of an individual *NexCaptionAttribute* attribute.

**Parameters**

| Name  | Description                      |
|-------|--------------|
| attr  | The attribute to set.            |
| value | The new value for the attribute. |
 
**Returns**

 
Zero for success, or a non-zero `NexPlayer`™ error code in the event of a failure.
 
 
#### boolean setValue (int attr,EdgeStyle value)

This method sets the value of an individual *NexCaptionAttribute* attribute.

**Parameters**


| Name  | Description                      |
|-------|--------------|
| attr  | The attribute to set.            |
| value | The new value for the attribute. |
 
**Returns**

 
Zero for success, or a non-zero `NexPlayer`™ error code in the event of a failure.
  
#### boolean setValue (int attr,int value)

This method sets the value of an individual *NexCaptionAttribute* attribute.

**Parameters**


| Name  | Description                      |
|-------|--------------|
| attr  | The attribute to set.            |
| value | The new value for the attribute. |.
 
**Returns**

 
Zero for success, or a non-zero `NexPlayer`™ error code in the event of a failure.
  
#### boolean setValue (int attr,float value)

This method sets the value of an individual *NexCaptionAttribute* attribute.

**Parameters**

| Name  | Description                      |
|-------|--------------|
| attr  | The attribute to set.            |
| value | The new value for the attribute. |
 
**Returns**

 
Zero for success, or a non-zero `NexPlayer`™ error code in the event of a failure.
 
#### final int COLOR\_BACKGROUND = 0x00000102 *[static]*

Possible key value for *key* parameter of `setValue(int, CaptionColor)`.

This key indicates the caption text background color.

**See Also**

 
- `NexClosedCaption.CaptionColor` for available background colors.
 
#### final int COLOR\_EDGE = 0x00000101 *[static]*

Possible key value for *key* parameter of `setValue(int, CaptionColor)**.

This key indicates the caption text edge color.

**See Also**

 
- `NexClosedCaption.CaptionColorAvaliable` for available font edge colors.
 
#### final int COLOR\_FONT = 0x00000100 *[static]*

Possible key value for *key* parameter of `setValue(int, CaptionColor)`.

This key indicates the caption text color.

**See Also**

 
- `NexClosedCaption.CaptionColor` for available caption font colors.
 
#### final int COLOR\_WINDOW = 0x00000103 [static]

Possible key value for *key* parameter of `setValue(int, CaptionColor)`.

This key indicates the caption window color.

**See Also**

 
- `NexClosedCaption.CaptionColor` for available caption window colors.


#### final int EDGE\_STYLE = 0x00000010 *[static]*

Possible key value for *key* parameter of `setValue(int, EdgeStyle)`.

This key indicates the caption text edge style.

Available Edge Styles :

- NexCaptionAttribute.EdgeStyle.NONE
- NexCaptionAttribute.EdgeStyle.DROP\_SHADOW
- NexCaptionAttribute.EdgeStyle.RAISED
- NexCaptionAttribute.EdgeStyle.DEPRESSED
- NexCaptionAttribute.EdgeStyle.UNIFORM

#### final int FLOAT\_SCALE\_FACTOR = 0x00000000 *[static]*

Possible key value for *key* parameter of `setValue(int, float)`.

This key indicates the value to scale the caption text.

Possible Value : **0.5** ∼ **2.0**

#### final int FLOAT\_STROKE\_WIDTH = 0x00000001 *[static]*

Possible key value for *key* parameter of `setValue(int, float)`.

This key indicates the uniform width of caption text.

#### final int OPACITY\_BACKGROUND = 0x00000202 *[static]*

Possible key value for *key* parameter of `setValue(int, int)`.

This key indicates the caption text background opacity.

Possible Value : **0** ∼ **255** , where 0 is completely transparent and 255 is completely opaque.

#### final int OPACITY\_EDGE = 0x00000201 *[static]*

Possible key value for *key* parameter of `setValue(int, int)`.

This key indicates the caption text edge opacity.

Possible Value : **0** ∼ **255** , where 0 is completely transparent and 255 is completely opaque.

#### final int OPACITY\_FONT = 0x00000200 *[static]*

Possible key value for *key* parameter of `setValue(int, int)`.

This key indicates the caption text opacity.

Possible Value : **0** ∼ **255** , where 0 is completely transparent and 255 is completely opaque.

#### final int OPACITY\_WINDOW = 0x00000203 *[static]*

Possible key value for *key* parameter of `setValue(int, int)`.

This key indicates the caption window opacity.

Possible Value : **0** ∼ **255** , where 0 is completely transparent and 255 is completely opaque.

### NexCaptionPainter Class Reference


This class defines the caption renderer view and displays the information to the user.

In order to support all of the text attributes and display options of the CEA 608 / CEA 708 / WebVTT / TTML / SMI /
SRT / SUB specifications, it is necessary to create a Caption Renderer view with the `NexCaptionPainter` class.

The `NexCaptionPainter` view is overlaid on the application’s video output, and as a result, whenever the video display
changes, the `NexCaptionPainter` must also be updated in order for captions to be accurately displayed.

In particular, the `NexCaptionPainter` in an application requires the following information:

- `Rendering Area Information:` Whenever the video output in an application UI changes its size or the orientation changes, the new size information should also be passed to the `NexCaptionPainter`class by calling the
    `NexCaptionPainter.setRenderingArea` method.
- `New Caption Data:` Whenever new caption data is received, it should be passed to the `NexCaptionPainter`
    by calling the `NexCaptionPainter.setDataSource` method.

When it is necessary to clear captions from the screen, for example when seeking in or stopping content, calling the
`NexCaptionPainter.clear` method will remove the captions existing on the screen.

When you want to set attributes to the captions, the `NexCaptionSetting` should be passed to `NexCaptionPainter` by
calling the `NexCaptionPainter.setUserCaptionSettings` method.


**Public Attributes**

- `SparseIntArray cachedMappedFontColors`

**Protected Member Functions**

- `void onLayout (boolean changed, int l, int t, int r, int b)`

#### NexCaptionPainter(Context context,int captionType)

This is an alternative constructor for the `NexCaptionPainter`.

**Parameters**

| Name        | Description                          |
|-------------|------------------|
| context     | The handle for the player.           |
| captionType | The type of caption to be displayed. |
 
#### NexCaptionPainter(Context context,AttributeSet attrs)

This is an alternative constructor for the `NexCaptionPainter`.

> **Warning** If the caption view has to be used in Android xml, this constructor must be called. CEA-608 caption type will
be selected as a default.
 
**Parameters**

| Name    | Description                                     |
|---------|---------|
| context | The handle for the player.                      |
| attrs   | The set of attributes associated with the view. |
 


#### int getCaptionType ()

This is a method to get the type of caption to be displayed.

**Returns**

 
the type of the caption to be displayed.
 
**See Also**

 
- caption types in `NexContentInformation` class
 
#### NexCaptionSetting getUserCaptionSettings ( )

This method gets the attributes of the captions.

**Returns**

 
The attributes of the captions. If the user has not set this before, it will returned the default properties.
 
#### void setCaptionType (int captionType)

This is a method to set the type of caption to be displayed.

**Parameters**
 
| Name        | Description                          |
|-------------|------------------|
| captionType | the type of caption to be displayed. |
 
**See Also**

 
- caption types in `NexContentInformation`
 
#### void setDataSource (final NexClosedCaption data)

This method sets the caption data to be rendered.

**Parameters**

| Name    | Description                                                                                |
|---------|--------------------------------|
| caption | The NexClosedCaption object containing the closed captions and attributes to be displayed. |
 
#### void setRenderingArea (Rect renderingArea, float scale)

This method sets the caption rendering area, compared to the video rendering area.

This method can be used to reposition where captions will appear relative to the playing content.

**Parameters**

| Name          | Description                                                              |
|---------------|--------------|
| renderingArea | The area of caption.                                                     |
| scale         | The scale should be used to scale the text renderer accordingly as well. |
 
#### void setUserCaptionSettings (NexCaptionSetting captionSettings)

This method sets the attributes of the captions.

**Parameters**

 
| Name            | Description                    |
|-----------------|------------|
| captionSettings | An object of NexCaptionSetting |
 
**See Also**

 
- `NexCaptionSetting`
 
### NexCaptionPreview Class Reference


This class defines the look of a caption preview renderer so that a preview of captions may be displayed to the user.

This class can be used as a preview of user selections, to show how captions will be rendered on screen during playback when different attributes such as caption window, background, text color, and edge effect have been set by the user.

This preview can be used for any format of captions.

**Static Public Attributes**

- `static final int PTEXT_ALIGN_HORIZONTAL_LEFT` = 0
- `static final int PTEXT_ALIGN_HORIZONTAL_CENTER` = 1
- `static final int PTEXT_ALIGN_HORIZONTAL_RIGHT` = 2
- `static final int PTEXT_ALIGN_VERTICAL_TOP` = 0
- `static final int PTEXT_ALIGN_VERTICAL_MIDDLE` = 1
- `static final int PTEXT_ALIGN_VERTICAL_BOTTOM` = 2

**Protected Member Functions**

- `void onMeasure (int widthMeasureSpec, int heightMeasureSpec)`
- `void onDraw (Canvas canvas)`

 
#### NexCaptionPreview (Context context)

This method constructs the caption preview renderer.

**Parameters**

 
| Name    | Description                |
|---------|--------|
| context | The handle for the player. |

 
#### NexCaptionPreview (Context context, AttributeSet attr)

This method is an alternative constructor for the caption preview renderer.

**Parameters**

 
| Name    | Description                                     |
|---------|---------|
| context | The handle for the player.                      |
| attr    | The set of attributes associated with the view. |

 
> **Warning** If the caption view is to be used in Android xml, this constructor must be used.

 


#### void changeFontSize (int sizeRate)

This method changes the font size of text in the caption preview.

To double the font size, the parameter *sizeRate* should be set to 200. In contrast, to halve the font size, *sizeRate* should be set to 50.

**Parameters**
 
| Name     | Description                                                           |
|----------|-------------------------------|
| sizeRate | The change in size of the caption preview text font, as a percentage. |

 
#### void resetEdgeStyle ( )

This method resets the edge effects on caption preview text.

Possible edge effects include *setShadow*, *setCaptionStroke*, *setRaise*, and *setDepressed*.

 
#### void setBGCaptionColor (CaptionColor bgColor, int opacity)

This method sets the background color of text in the caption preview.

**Parameters**

 
| Name    | Description                                                                                                                             |
|---------|-------------|
| bgColor | The color to be used for the background of text (the window color where caption text will appear).                                      |
| opacity | The opacity of the preview caption window as an integer, from 0 to 255, where 0 is completely transparent and 255 is completely opaque. |

 
#### void setCaptionStroke (CaptionColor strokeColor, int strokeOpacity, float strokeWidth)

This method sets the stroke color and width of caption preview text.

For a full list of colors, please refer to `NexClosedCaption.CaptionColor`. The stroke line width is in pixels. Antialiasing is supported, so fractions of a pixel are allowed.


**Parameters**

| Name          | Description                                                                                                      |
|---------------|----------|
| strokeColor   | The stroke color, or null to use the color from the original caption data.                                       |
| strokeOpacity | The stroke opacity as an integer, from 0 to 255, where 0 is completely transparent and 255 is completely opaque. |
| strokeWidth   | The width of the stroke line as a float, in pixels.                                                              |

 
#### void setCaptionWindowColor (CaptionColor windowColor, int windowOpacity)

This method sets the color of the caption window when previewed.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.

**Parameters**

 
| Name          | Description                                                                                                            |
|---------------|----------------|
| windowColor   | The window color, or null to use the color from the original caption data.                                             |
| windowOpacity | The window color opacity as an integer, from 0 to 255, where 0 is completely transparent and 255 is completely opaque. |
 

 
#### void setDepressed (boolean isDepressed)

This method adds a depressed filter to caption preview text.

**Parameters**

| Name        | Description                                                                           |
|-------------|---------------------------|
| isDepressed | TRUE if the text should be displayed as if depressed into the screen; otherwise FALSE |

 
#### void setDepressedWithColor (boolean isDepressed, CaptionColor depColor, int depOpacity)

This method indicates whether or not CEA 608 closed captions should be displayed as if "depressed" (in a set font
color).

If CEA 608 closed captions are "depressed", they should be displayed as if they are pressed into the video display
slightly, and the color of the depressed portion of the caption text ("sunken" into the display) can be set by the user.

**Parameters**

 
| Name        | Description                                                                                              |
|-------------|--------------------------|
| isDepressed | TRUE if the text should be displayed as if depressed into the screen; otherwise FALSE                    |
| depColor    | The color of the depressed part of the text set by the user, or null to use the default color.           |
| depOpacity  | The opacity of the depressed part of the text as an integer, from 0 (transparent) to 255 (fully opaque). |

 
#### void setEmbossBlurRadius ( float radius)

This method sets the radius of blur for the Emboss Mask filter when a user sets the caption preview to be displayed
’Raised’ or ’Depressed’ in the UI.

**Parameters**

 
| Name   | Description                                         |
|--------|-------------|
| radius | The radius of blur when Emboss Mask filter is used. |
 
 
#### void setEmbossSpecular (float specular)

This method sets the specular level of the Emboss Mask filter used when a user sets the caption preview to be
displayed ’Raised’ or ’Depressed’ in the UI.

**Parameters**

 
| Name     | Description                                   |
|----------|---------------------------|
| specular | The specular level of the Emboss Mask filter. |
 
#### void setFGCaptionColor (CaptionColor fontColor, int opacity)

This method sets the foreground color of caption preview text.

**Parameters**

 
| Name      | Description                                                                                                                   |
|-----------|-----------------------|
| fontColor | The color to be used for caption preview text.                                                                                |
| opacity   | The opacity of the preview text as an integer, from 0 to 255, where 0 is completely transparent and 255 is completely opaque. |
 
#### void setFonts (Typeface normType, Typeface boldType, Typeface italicType, Typeface boldItalicType)

This method sets the fonts to be used for caption preview text.

Four typefaces may be specified for different combinations of **bold** anditalics. The preview caption renderer will
select the appropriate typeface from among these based on the preview caption selections being displayed.

For best results, specify all four typefaces. Any typeface can be set to null, in which case the system default
typeface will be used.



**Parameters**

 
| Name           | Description                                                                 |
|----------------|-----------------|
| normType       | Typeface to be used for preview captions that are neither bold nor italic.  |
| boldType       | Typeface to be used for bold preview captions.                              |
| italicType     | Typeface to be used for preview captions in italics.                        |
| boldItalicType | Typeface to be used for preview captions that are both bold and in italics. |
 
#### void setPreviewTextAlign (int horizontal, int vertical)

This method sets the alignment of text inside the caption window preview.

**Parameters**

 
| Name       | Description                                                                                                                                                                                           |
|------------|-----------------------------------|
| horizontal | Horizontal alignment value. This will be one of:   - PTEXT\_ALIGN\_HORIZONTAL\_LEFT: left aligned - PTEXT\_ALIGN\_HORIZONTAL\_CENTER: center aligned - PTEXT\_ALIGN\_HORIZONTAL\_RIGHT: right aligned |
| vertical   | Vertical alignment value. This will be one of:   - PTEXT\_ALIGN\_VERTICAL\_TOP: top aligned - PTEXT\_ALIGN\_VERTICAL\_MIDDLE: middle aligned - PTEXT\_ALIGN\_VERTICAL\_BOTTOM: bottom aligned         |
 
#### void setRaise (boolean isRaised)

This method adds a raised filter to caption preview text.

**Parameters**

| Name      | Description                                                         |
|-----------|-----------------------------|
| isRaisedv | TRUE if the text should be displayed as if raised; otherwise FALSE. |
 
#### void setRaisedWithColor (boolean isRaised, CaptionColor raisedColor, int raisedOpacity)

This method indicates whether or not CEA 608 closed captions should be displayed as if "raised" (in a set font
color).

If CEA 608 closed captions are "raised", they should be displayed as if they rise from the video display slightly, and
the color of the raised portion of the caption text can be set by the user.

**Parameters**

 
| Name          | Description                                                                                           |
|---------------|-----------------------|
| isRaise       | TRUE if closed captions are raised, FALSE if not.                                                     |
| raisedColor   | The color of the raised part of the text set by the user, or null to use the default color.           |
| raisedOpacity | The opacity of the raised part of the text as an integer, from 0 (transparent) to 255 (fully opaque). |
 
#### void setShadow (boolean isShadow, CaptionColor shadowColor, int shadowOpacity)

This method adds a drop shadow effect to caption preview text.

**Parameters**

 
| Name          | Description                                                                                                      |
|---------------|----------|
| isShadow      | Set this to TRUE to force text to be displayed with a shadow, or FALSE for no shadow.                            |
| shadowColor   | The shadow color, or null to use the color from the original caption data.                                       |
| shadowOpacity | The shadow opacity as an integer, from 0 to 255, where 0 is completely transparent and 255 is completely opaque. |
 
#### void setUniform (boolean isUniform)

This method adds a uniform filter to caption preview text.

**Parameters**

| Name      | Description                                                                         |
|-----------|-------------------------|
| isUniform | TRUE if the text should be displayed with a uniform black outline; otherwise FALSE. |
 
### NexCaptionRenderer Class Reference

This class defines the CEA 608 Closed Caption renderer view and displays the information to the user.

In order to support all of the text attributes and display options of the CEA 608 specifications, it is necessary to create a separate Caption Renderer view with the `NexCaptionRenderer` class.

The` NexCaptionRenderer` view is overlaid on the application’s video output, and as a result, whenever the video display changes, the `NexCaptionRenderer` must also be updated in order for captions to be accurately displayed.

In particular, the `NexCaptionRenderer` in an application requires the following information:


- `Video Size Information:` Whenever the video output in an application’s UI changes size or orientation changes, the new size information should also be passed to `NexCaptionRenderer` by calling the `NexCaptionRenderer.setRenderArea` method.
- `New CEA 608 closed caption Data:` Whenever new CEA 608 closed caption data is received, it should be passed to the `NexCaptionRenderer` by calling the `NexCaptionRenderer.SetData` method.

When it is necessary to clear CEA 608 closed captions from the screen, for example when seeking in or stopping content, calling the `NexCaptionRenderer.makeBlankData` method will erase captions existing on the screen.

This class should only be used when displaying CEA 608 closed captions, not other kinds of subtitles.

To display CFF and 3GPP timed text, please use `NexCaptionRendererForTimedText.`


**Static Public Attributes**

- `static final int RENDER\_MODE\_BASIC = 0`
- `static final int RENDER\_MODE\_CUSTOM = 1`

**Protected Member Functions**

- `void onMeasure (int widthMeasureSpec, int heightMeasureSpec)`
- `void onDraw (Canvas canvas)`

#### NexCaptionRenderer (Context context, int borderX, int borderY)

This sets the CEA 608 closed caption renderer in FULL mode.

In order for captions to be legible when they are displayed, the closed caption rendering area defined here is
a rectangle set within the larger video rendering area. This ensures that when characters are displayed on the
screen, they are not difficult to see because they are flush with the edge of the video.

The parameters `borderX` and `borderY` set a kind of border around the caption rendering area and within the
video rendering area where no captions will appear.

**Parameters**

| Name    | Description                                                                                    |
|---------|----------------|
| context | The handle for the player.                                                                     |
| borderX | The horizontal indent from the edge of the video rendering area to the caption rendering area. |
| borderY | The vertical indent from the edge of the video rendering area to the caption rendering area.   |
 
#### NexCaptionRenderer (Context context, AttributeSet attrs)

This is an alternative constructor for the `NexCaptionRenderer`.

> **Warning** If the caption view is to be used in Android xml, this constructor must be used.

**Parameters**

 
| Name    | Description                                     |
|---------|---------|
| context | The handle for the player.                      |
| attrs   | The set of attributes associated with the view. |
 


#### void changeTextSize (int sizeRate)

This method changes the font size of CEA 608 closed captions when displayed in content.

It allows the font size of CEA 608 closed captions to be selected by users in the UI.

**Parameters**

 
| Name     | Description                                                                                        |
|----------|--------------------|
| sizeRate | The change in font size as a percentage, from 50 to 200 percent of the original caption text size. |
 
#### int getM\_border\_X ( )

This method gets the horizontal position of the CEA 608 caption rendering area, compared to the video rendering
area.

This method can be used along with `setM\_border\_X` to reposition where CEA 608 closed captions will appear
relative content.

**Returns**

The horizontal indent of the captions, as an integer.
 
**See Also**

 
- `NexCaptionRenderer.setM\_border\_X`
 

#### int getM\_border\_Y ( )

This method gets the horizontal position of the CEA 608 caption rendering area, compared to the video rendering
area.

This method can be used along with `setM\_border\_Y` to reposition where CEA 608 closed captions will appear
relative to the playing content.

**Returns**

 
The vertical indent of the captions, as an integer.
 
**See Also**

 
- `NexCaptionRenderer.setM\_border\_Y`
 
 
#### void init CaptionStyle ( )

This method initializes the style attributes of CEA 608 closed captions that may be set by a user, including the colors
of the text, background, and caption window as well as the edge style and the font size.

This API does not effect the default caption style attributes of specific streaming content.

 
#### void makeBlankData ( )

This clears the currently displayed captions in CEA 608 closed captions.

Use this method if it is necessary to erase captions that are left on the screen.

#### void resetEdgeEffect ( )

This method resets the edge effects on CEA 608 closed captions.

Possible edge effects includes setShadow, setCaptionStroke, setRaise, and setDepressed.

 
#### void setBGCaptionColor (CaptionColor background,int bgOpacity)

This sets the background color of CEA 608 closed captions.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.


**Parameters**

 
| Name       | Description                                                                    |
|------------|--------------------|
| background | The background color, or null to use the color from the original caption data. |
| bgOpacity  | The background opacity, from 0 (transparent) to 255 (fully opaque). |

#### void setBold (boolean isBold)

Controls whether captions are displayed in bold text.

Caption data includes attributes such as bold and italic.

Normally, the caption renderer displays each character in normal, bold or italic based on the attributes included in
the caption data.

However in some cases (such as for users with visual impairment) it may be desirable to force the use of bold text.

By enabling this option, the bold attributes in the caption data are ignored and a bold font is used for all characters.

**Parameters**

 
| Name   | Description                                                                                       |
|--------|-------------------|
| isBold | Set this to TRUE to force bold text, or FALSE to use the bold attribute in the original captions. |
 
#### void setCaptionStroke (CaptionColor strokeColor, float strokeWidth)

This sets the CEA 608 caption renderer stroke color and width.

For a full list of colors, please refer to `NexClosedCaption.CaptionColor`. The stroke line width is in pixels. Antialiasing is supported, so fractions of a pixel are allowed.

**Parameters**

 
| Name        | Description                                                                |
|-------------|----------------|
| strokeColor | The stroke color, or null to use the color from the original caption data. |
| strokeWidth | The stroke width in pixels.                                                |
 
#### void SetData (NexClosedCaption caption)

This method sets the caption data to be rendered and displayed with CEA 608 closed captions.


**Parameters**

 
| Name    | Description                                                                                  |
|---------|----------------------------------|
| caption | The `NexClosedCaption` object containing the closed captions and attributes to be displayed. |
 
#### void setDefaultTextSize (float dTextSize)

This method sets the default font size for CEA 608 closed captions.

When the `setMode` API is not in use or the parameter `mode` is set to 0, only the text size of the CEA 608 closed
captions will change while the render area of each letter will be fixed (as defined by the CEA 608 specifications).
The caption text will then be cut off when the font size is increased to sizes larger than this fixed rendering area. To
avoid this potential issue and to ensure that caption text can be easily read, the parameter`mode` in the `setMode`
API should be set to 1 so that both caption text size and the caption rendering area will be resized together.

The parameter `dTextSize` can be set to a percentage of the default caption render area (as defined in the CEA
608 specifications). The default value is 70 which means that text will fill 70 percent of the caption rendering area.

> **Warning** Note that clear text render is not guaranteed when the default font size is set to be too big or too small and
may result in caption text being cut off or overlapping.
 
**Parameters**

| Name      | Description                                                                           |
|-----------|---------------------------|
| dTextSize | The default text size to set, as a percentage of the caption render area (as afloat). |
 
**See Also**

 
- `NexCaptionRender.setMode`
 
 
#### void setDepressed (boolean isDepressed)

This method indicates whether or not CEA 608 closed captions are "depressed".

If CEA 608 closed captions are "depressed", they should be displayed as if pressed into the video display slightly.

If depressed closed captions are to be displayed in a user-defined color, see the method `setDepressedWithColor` instead.


**Parameters**

| Name        | Description                                                  |
|-------------|----------------------|
| isDepressed | TRUE if closed captions are depressed, FALSE if they are not. |
 
**See Also**

 
- `NexCaptionRenderer.setDepressedWithColor`
 
#### void setDepressedWithColor (boolean isDepressed, CaptionColor depressedColor, int depressedOpacity)

This method indicates whether or not CEA 608 closed captions should be displayed as if "depressed" (in a set font
color).

If CEA 608 closed captions are "depressed", they should be displayed as if they are pressed into the video display
slightly, and the color of the depressed portion of the caption text ("sunken" into the display) can be set by the user.

**Parameters**

 
| Name             | Description                                                                                              |
|------------------|--------------------------|
| isDepressed      | TRUE if closed captions are depressed,FALSE if they are not.                                             |
| depressedColor   | The color of the depressed part of the text set by the user, or null to use the default color.           |
| depressedOpacity | The opacity of the depressed part of the text as an integer, from 0 (transparent) to 255 (fully opaque). |
 
#### void setDisableFlashing (boolean disableFlashing)

This method turns off flashing in CEA 608 closed captions.

CEA 608 closed captions can include a "flashing" attribute to indicate that the captions should be displayed flashing
in order to fully meet the specifications. However, it may at times be is desireable to turn off this "flashing" display,
and this method makes this possible.


**Parameters**

 
| Name            | Description                                                                                                                                                                                                                                                       |
|-----------------|-----------|
| disableFlashing | If set to TRUE, the renderer will ignore flashing attributes even in content with closed captions that have flashing attributes. If set to FALSE, the renderer will display flashing captions if the content’s caption information includes a flashing attribute. |
 
#### void setDisableUnderline (boolean disableUnderline)

This method turns off underlining in CEA 608 closed captions.

CEA 608 closed captions can include an underline attribute to indicate that the captions should be underlined in
order to fully meet the specification. However, it may at times be desireable to turn off this underlining, and this
method makes this possible.

**Parameters**

 
| Name             | Description                                                                                                                                                                                                                                                    |
|------------------|--------|
| disableUnderline | If set to TRUE, the renderer will ignore underline attributes even in content with closed captions that have underline attributes. If set to FALSE, the renderer will underline captions if the content’s caption information includes an underline attribute. |
 
#### void setEmbossBlurRadius (float radius)

This method sets the blur radius of the Emboss Mask filter used when a user sets CEA 608 captions to be ’Raised’
or ’Depressed’ in the UI.

**Parameters**

 
| Name   | Description                                |
|--------|------------------------|
| radius | The blur radius of the Emboss Mask filter. |
 
@deprecated This API is deprecated.

#### void setEmbossSpecular (float specular)

This method sets the specular level of the Emboss Mask filter used when a user sets CEA 608 captions to be
’Raised’ or ’Depressed’ in the UI.

**Parameters**

 
| Name     | Description                                   |
|----------|---------------------------|
| specular | The specular level of the Emboss Mask filter. |
 
@deprecated This API is deprecated.

#### void setFGCaptionColor (CaptionColor foreground, int fgOpacity)

This sets the CEA 608 closed captions foreground (text) color.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.

**Parameters**
 
| Name       | Description                                                                    |
|------------|--------------------|
| foreground | The foreground color, or null to use the color from the original caption data. |
| fgOpacity  | The foreground opacity, from 0 (transparent) to 255 (fully opaque).            | 

#### void setFonts (Typeface normType, Typeface boldType, Typeface italicType, Typeface boldItalicType)

This sets the font used for the captions.

Four typefaces may be specified for different combinations of bold and italic. The caption renderer will select the
appropriate typeface from among these based on the CEA-608 captions being displayed.

For best results, specify all four typefaces. Any typeface can be set to null, in which case the system default
typeface will be used.


**Parameters**

 
| Name           | Description                                                        |
|----------------|----------------------------|
| normType       | Typeface to be used for captions that are neither bold nor italic. |
| boldType       | Typeface to be used for bold CEA-608 captions.                     |
| italicType     | Typeface to be used for italic CEA-608 captions.                   |
| boldItalicType | Typeface to be used for CEA-608 captions that are both and italic. |
 
#### void setLineSpacingRate (float spaceRate)

This method sets the spacing between lines of CEA 608 closed captions.

This method will only work when the parameter `mode` in `setMode` is set to 1, so that CEA 608 closed captions
can be rendered with additional font settings. The parameter `spaceRate` can be set to a percentage of the default
space size between caption lines in CEA 608 closed captions. Also note that a maximum of 15 lines of CEA 608
closed caption text can appear on the screen at one time, which may become relevant when caption font size is
increased.

>**Warning** Note that clear text render is not guaranteed when the value ofspaceRateis set to be too big or too small
and may result in text being cut off or overlapping.
 
**Parameters**

| Name      | Description                                                                                                                                                    |
|-----------|----------------|
| spaceRate | The amount of space to leave between lines of text in CEA 608 closed captions, as a percentage of the default size of space between caption lines (as afloat). |
 
**See Also**

 
- `NexCaptionRenderer.setMode`
- `NexCaptionRenderer.setDefaultTextSize`
 
 
#### void setM\_border\_X (int m\_border\_X)

This method sets the horizontal position of the CEA 608 caption rendering area, compared to the video rendering
area.

This method can be used to reposition where CEA 608 closed captions will appear relative to the playing content.


**Parameters**

| Name         | Description                                                                                                  |
|--------------|------|
| m\_border\_X | The horizontal indent of the caption window, as an integer, where 0 is the left of the video rendering area. |
 
#### void setM\_border\_Y (int m\_border\_Y)

This method sets the vertical position of the CEA 608 caption rendering area, compared to the video rendering
area.

This method can be used to reposition where CEA 608 closed captions will appear relative to the playing content.

**Parameters**

 
| Name         | Description                                                                                               |
|--------------|---------------------------|
| m\_border\_Y | The vertical indent of the caption window, as an integer, where 0 is the top of the video rendering area. |
 
#### void setMode (int mode)

This method allows the rendering mode of CEA 608 closed captions to be chosen.

The two available rendering modes are basic CEA 608 rendering, which meets the specifications of the CEA 608
standard, and an enhanced rendering mode that makes it possible for CEA 608 closed captions to be rendered
with additional display settings. This second mode makes it possible for CEA 608 closed captions to satisfy FCC
regulations regarding captioning options (including the changing of foreground and background color, font size, font
type).

**Parameters**

| Name | Description                                                                                                                                                                                                                  |
|------|--------------|
| mode | Zero when CEA 608 closed captions will be rendered and displayed according to the CEA 608 specifications; or 1 when CEA 608 closed captions should be rendered with additional rendering options to satisfy FCC regulations. |
 
#### void setRaise (boolean isRaise)

This method indicates whether or not CEA 608 closed captions are "raised".

If CEA 608 closed captions are "raised", they should be displayed as if rising above the video display slightly, for
example as if they were embossed.

To have the raised closed captions be displayed in a user-defined color, see the *setRaiseWithColor* method
instead.

**Parameters**

| Name    | Description                                               |
|---------|-------------------|
| isRaise | TRUE if closed captions are raised, FALSE if they are not. |
 
**See Also**

 
- `NexCaptionRenderer.setRaiseWithColor`
 
#### void setRaiseWithColor (boolean isRaise, CaptionColor raisedColor, int raisedOpacity)

This method indicates whether or not CEA 608 closed captions should be displayed as if "raised" (in a set font
color).

If CEA 608 closed captions are "raised", they should be displayed as if they rise from the video display slightly, and
the color of the raised portion of the caption text can be set by the user.

**Parameters**

 
| Name          | Description                                                                                           |
|---------------|-----------------------|
| isRaise       | TRUE if closed captions are raised,FALSE if not.                                                      |
| raisedColor   | The color of the raised part of the text set by the user, or null to use the default color.           |
| raisedOpacity | The opacity of the raised part of the text as an integer, from 0 (transparent) to 255 (fully opaque). |
 
#### void setRenderArea (int x, int y, int width, int height)

This sets the CEA 608 closed caption rendering area within the displayed video area.

CEA 608 closed captions will be displayed in this caption rendering area on the screen within the border defined by
`NexCaptionRenderer`.

**Parameters**

 
| Name   | Description                                                                                |
|--------|--------------------------------|
| x      | The horizontal position of the top left corner of the video rendering area, as an integer. |
| y      | The vertical position of the top left corner of the video rendering area, as an integer.   |
| width  | The width of the caption rendering area, as an integer.                                    |
| height | The height of the caption rendering area, as an integer.                                   |
 
#### void setShadow (boolean isShadow)

This sets whether the CEA-608 captions have a shadow.

**Parameters**

| Name     | Description                                                    |
|----------|------------------------|
| isShadow | Set this to TRUE to force shadow text, or FALSE for no shadow. |
 
#### void setShadowWithColor (boolean isShadow, CaptionColor shadowColor, int shadowOpacity)

This method sets whether CEA 608 closed captions should be displayed with a colored shadow.

It can be used to allow users to select the color they want to use for shadows added to CEA 608 closed captions.

**Parameters**

 
| Name          | Description                                                                           |
|---------------|---------------------------|
| isShadow      | Set this to TRUE to force text to be displayed with a shadow, or FALSE for no shadow. |
| shadowColor   | The shadow color, or null to use the color from the original caption data.            |
| shadowOpacity | The shadow opacity as an integer, from 0 (transparent) to 255 (fully opaque).         |
 
#### void setTextScaleFactor (float scale, float textSize)

This method lets users control the CEA 608 closed caption font size in `NexPlayer`™ from the application UI.

>**Warning** This method should only be used when a *customFont* has been set by calling the method `NexCaptionRenderer.setFonts` AND the captions exceed the size of the caption character cell.
 
**Parameters**

| Name     | Description                                                      |
|----------|--------------------------|
| scale    | The value to scale the caption text when resizing it, as afloat. |
| textSize | The size of the desired caption text, in points.                 |
 
**See Also**

 
- `NexCaptionRenderer.setFonts`
 
#### void setUniform (boolean isUniform)

This method indicates whether or not CEA 608 closed captions should be displayed with a uniform effect.

If CEA 608 closed captions are displayed with the uniform effect, they should be displayed with a uniform black
outline.

**Parameters**

 
| Name      | Description                                                                          |
|-----------|--------------------------|
| isUniform | TRUE if all caption characters should have a uniform black outline; otherwise FALSE. |
 
#### void setWindowColor (CaptionColor windowColor, int windowOpacity)

This method sets the window color of CEA 608 closed captions.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.

**Parameters**

 
| Name          | Description                                                                |
|---------------|----------------|
| windowColor   | The window color, or null to use the color from the original caption data. |
| windowOpacity | The window color opacity, from 0 (transparent) to 255 (fully opaque).      |
 
### NexCaptionRendererForTimedText Class Reference

This class defines the renderer view for CFF and 3GPP timed text subtitles in content and displays them.

In order for `NexPlayer`™ to display CFF or 3GPP timed text, a separate Caption Renderer view must be created with the `NexCaptionRendererForTimedText` class.

In particular, in order to use `NexCaptionRendererForTimedText`, care must be taken to do the following:

1. **Pass Video Size Information** : Since the `NexCaptionRendererForTimedText` view is overlaid on the video display in an application, information about the video display must be passed to the caption renderer for timed text to be properly displayed. This means that when the video output size in the application UI is set
    or changes (including the when the video surface is first created), `NexCaptionRendererForTimedText` should
    also be notified. To do so, the following two methods should be called:
       - `setScaleRatio(float scale)`: When the video is scaled up (for example to fit-screen or full-screen), pass
          the scale ratio to `NexCaptionRendererForTimedText` with this method.
	- `setVideoSizeInformation(int videoWidth, int videoHeight, int surfaceWidth, int surfaceHeight, int left, int
    top)`: To fit the text render area within the video, `NexCaptionRendererForTimedText` also needs to know
    the video size and position information provided by calling this method.
2. **Pass Timed Text Data to the Renderer** : Whenever timed text is updated, the new timed text data must be
passed to `NexCaptionRendererForTimedText`. To do this:
	- (a) When calling `onTextRenderRender`, the text type must be checked by calling `NexClosedCaption.getTextType`.
	- (b) If that method returns TEXT\_TYPE\_TTML\_TIMEDTEXT for CFF timed text or TEXT\_TYPE\_3GPP\_-
TIMEDTEXT for 3GPP timed text, pass a `NexClosedCaption` object with the new timed text data to
`NexCaptionRendererForTimedText` with the s`etData(NexClosedCaption data)` method.
	- (c) Finally, call the NexCaptionRendererForTimedText.invalidate method when updating the captions.
 
3. **Clear Timed Text on the Screen** : Whenever timed text must be cleared from the screen (for example when
    seeking or stopping content), calling clear and invalidate will `clear` any existing text from the device screen.

This class replaces the NexCaptionRendererFor3GPPTT in earlier versions of the `NexPlayer`™ SDK.

To display CEA 608 closed captions however, please use `NexCaptionRenderer`.

#### NexCaptionRendererForTimedText (Context context)

This is the constructor for the 3GPP and TTML timed text caption renderer.

**Parameters**
 
| Name    | Description                |
|---------|--------|
| context | The handle for the player. |
 
#### NexCaptionRendererForTimedText (Context context, AttributeSet attrs)

This is an alternative constructor for the Timed Text caption renderer.

> **Warning** If the caption view is to be used in Android xml, this constructor must be used.


**Parameters**

 
| Name    | Description                                     |
|---------|---------|
| context | The handle for the player.                      |
| attrs   | The set of attributes associated with the view. |
 


#### float getScaleRatio ( )

This method gets the scale ratio of the displayed video.

The scale ratio should be used to scale the timed text renderer whenever the video display changes size.

**Returns**

 
The video’s scale ratio as a float.

 
#### void init CaptionStyle ( )

This method initializes the style attributes of timed text captions that may be set by a user, including the colors of
the text, background, and caption window as well as the edge style and the font size.

This API does not effect the default caption style attributes of specific streaming content.
 
#### void resetEdgeEffect ( )

This method resets the edge effects on timed text captions.

Possible edge effects includes setShadow, setCaptionStroke, setRaise, and setDepressed.
 
#### void setBGCaptionColor (CaptionColor background, int bgOpacity)

This sets the background color of 3GPP/TTML captions.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.


**Parameters**

 
| Name       | Description                                                                    |
|------------|--------------------|
| background | The background color, or null to use the color from the original caption data. |
| bgOpacity  | The background opacity, from 0 (transparent) to 255 (fully opaque).            |
 
#### void setBold (boolean isBold)

This method controls whether timed text captions are displayed in bold text.

Caption data includes attributes such as **bold** anditalics.

Normally, the caption renderer displays each character in normal, **bold** or *italics* based on the attributes included in
the caption data.

However in some cases (such as for users with visual impairment) it may be desirable to force the use of **bold** text.

By enabling this option, the bold attributes in the caption data are ignored and a bold font is used for all characters.

**Parameters**

| Name   | Description                                                                                       |
|--------|-------------------|
| isBold | Set this to TRUE to force bold text, or FALSE to use the bold attribute in the original captions. |
 
#### void setCaptionStroke (CaptionColor strokeColor, int strokeOpacity, float strokeWidth)

This sets the 3GPP/TTML caption renderer stroke color and width.

For a full list of colors, please refer to `NexClosedCaption.CaptionColor`. The stroke line width is in pixels. Antialiasing is supported, so fractions of a pixel are allowed.

**Parameters**

 
| Name          | Description                                                                |
|---------------|----------------|
| strokeColor   | The stroke color, or null to use the color from the original caption data. |
| strokeOpacity | The stroke opacity, from 0 (transparent) to 255 (fully opaque).            |
| strokeWidth   | The stroke width in pixels.                                                |
 
#### void setCaptionWindowColor (CaptionColor windowColor, int windowOpacity)

This method sets the window color of 3GPP/TTML captions.

This is similar to setting a background color behind the caption text.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.

**Parameters**

| Name          | Description                                                                |
|---------------|----------------|
| windowColor   | The window color, or null to use the color from the original caption data. |
| windowOpacity | The window color opacity, from 0 (transparent) to 255 (fully opaque).      |
 
#### void setData (NexClosedCaption data)

This property specifies the 3GPP or CFF timed text data to the renderer.

**Parameters**

| Name | Description                                         |
|------|-------------|
| data | The timed text data as a `NexClosedCaption` object. |
 
#### void setDefaultTextSize (float size)

This method sets the default size of text for 3GPP/TTML timed text captions.

To change the font size for example based on a user selection, call the method *setFontSize* instead.

**Parameters**

| Name | Description                                                      |
|------|--------------------------|
| size | The default size of the caption text to set, in dip, as a float. |
 
**See Also**

 
- `setFontSize(float sizePercentage)`

#### void setDepressed (boolean isDepressed)

This method indicates whether or not 3GPP/TTML timed text captions should be displayed as if "depressed".

If 3GPP/TTML timed text captions are "depressed", they should be displayed as if pressed into the video display
slightly.

If depressed timed text is to be displayed in a user-defined color, see the method *setDepressedWithColor*
instead.

**Parameters**

 
| Name        | Description                                                                                     |
|-------------|-----------------|
| isDepressed | TRUE if the 3GPP/TTML timed text captions should be displayed as if depressed, otherwise FALSE. |
 
**See Also**

 
- `NexCaptionRendererForTimedText.setDepressedWithColor`
 
#### void setDepressedWithColor (boolean isDepressed, CaptionColor depColor, int depOpacity)

This method indicates whether or not 3GPP/TTML timed text should be displayed as if "depressed" (in a set font
color).

If 3GPP/TTML timed text is "depressed", it should be displayed as if the text is pressed into the video display slightly,
and the color of the depressed part of the text can be set by the user.

**Parameters**

| Name        | Description                                                                                 |
|-------------|---------------------------------|
| isDepressed | TRUE if the timed text is depressed,FALSE if not.                                           |
| depColor    | The color of the depressed part set by the user, or null to use the default color.          |
| depOpacity  | The opacity of the depressed part as an integer, from 0 (transparent) to 255 (fully opaque) |
 
 
#### void setEmbossBlurRadius (float radius)

This method sets the blur radius of the Emboss Mask filter used when a user sets 3GPP/TTML timed text to be
’Raised’ or ’Depressed’ in the UI.

**Parameters**

| Name   | Description                                |
|--------|------------------------|
| radius | The blur radius of the Emboss Mask filter. |
 
#### void setEmbossSpecular (float specular)

This method sets the specular level of the Emboss Mask filter used when a user sets 3GPP/TTML timed text to be
’Raised’ or ’Depressed’ in the UI.

**Parameters**

| Name     | Description                                   |
|----------|---------------------------|
| specular | The specular level of the Emboss Mask filter. |
 
#### void setFGCaptionColor (CaptionColor foreground, int fgOpacity)

This method sets the foreground (text) color of 3GPP/TTML timed text captions.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.

**Parameters**

 
| Name       | Description                                                                    |
|------------|--------------------|
| foreground | The foreground color, or null to use the color from the original caption data. |
| fgOpacity  | The foreground opacity, from 0 (transparent) to 255 (fully opaque).            |
 
#### void setFonts (Typeface normType, Typeface boldType, Typeface italicType, Typeface boldItalicType)

This method sets the fonts to be used for the 3GPP/TTML timed text captions.

Four typefaces may be specified for different combinations of bold and italic. The caption renderer will select the
appropriate typeface from among these based on the CEA-608 captions being displayed.

For best results, specify all four typefaces. Any typeface can be set to null, in which case the system default
typeface will be used.

**Parameters**

| Name           | Description                                                          |
|----------------|------------------------------|
| normType       | Typeface to be used for captions that are neither bold nor italic.   |
| boldType       | Typeface to be used for bold 3GPP/TTML captions.                     |
| italicType     | Typeface to be used for italic 3GPP/TTML captions.                   |
| boldItalicType | Typeface to be used for 3GPP/TTML captions that are both and italic. |
 
#### void setFontSize (float sizePercentage)

This method changes the font size of 3GPP/TTML timed text.

The size of text font can be changed from 50 to 200 percent of the original caption font size.

**Parameters**

| Name           | Description                                     |
|----------------|---------|
| sizePercentage | The percentage change in font size, as a float. |
 
#### void setRaise (boolean isRaise)

This method indicates whether or not 3GPP/TTML timed text captions should be displayed as if "raised".

If 3GPP/TTML timed text captions are "raised", they should be displayed as if rising above the video display slightly,
for example as if they were embossed.

To have the raised timed text be displayed in a user-defined color, see the *setRaiseWithColor* method instead.

**Parameters**

| Name    | Description                                                                 |
|---------|-----------------|
| isRaise | TRUE if the 3GPP/TTML timed text captions are raised,FALSE if they are not. |
 
**See Also**

 
- `NexCaptionRendererForTimedText.setRaiseWithColor`
 

#### void setRaiseWithColor (boolean isRaise, CaptionColor raisedColor, intr aisedOpacity)

This method indicates whether or not 3GPP/TTML timed text should be displayed as if "raised" (in a set font color).

If 3GPP/TTML timed text is "raised", it should be displayed as if the text rises from the video display slightly, and the
color of the raised part of the text can be set by the user.

**Parameters**

 
| Name          | Description                                                                               |
|---------------|-------------------------------|
| isRaise       | TRUE if the timed text is raised,FALSE if not.                                            |
| raisedColor   | The color of the raised part set by the user, or null to use the default color.           |
| raisedOpacity | The opacity of the raised part as an integer, from 0 (transparent) to 255 (fully opaque). |
 
#### void setScaleRatio (float scale)

This property describes the video’s scale ratio.

When a displayed video changes in size on the screen (as for example when a video is displayed full screen), this
ratio should be used to scale the text renderer accordingly as well.

**Parameters**

| Name  | Description              |
|-------|------|
| scale | The video’s scale ratio. |
 
#### void setShadow (boolean isShadow)

This method sets whether or not 3GPP/TTML timed text should be displayed with a shadow.

**Parameters**
 
| Name     | Description                                                                           |
|----------|---------------------------|
| isShadow | Set this to TRUE to force text to be displayed with a shadow, or FALSE for no shadow. |
 
#### void setShadowWithColor (boolean isShadow,CaptionColor shadowColor,int shadowOpacity)

This method sets whether or not timed text captions should be displayed with a colored shadow.

**Parameters**

| Name          | Description                                                                           |
|---------------|---------------------------|
| isShadow      | Set this to TRUE to force text to be displayed with a shadow, or FALSE for no shadow. |
| shadowColor   | The shadow color, or null to use the color from the original caption data             |
| shadowOpacity | The shadow opacity as an integer, from 0 (transparent) to 255 (fully opaque).         |
 
#### void setTextBoxOnLayout (Rect textBox)

This property overrides the text box and sets it to be able to be moved anywhere desired.

**Parameters**

| Name    | Description                   |
|---------|-----------|
| textBox | Override to anywhere desired. |
 
#### void setUniform (boolean isUniform)

This method indicates whether or not 3GPP/TTML timed text captions should be displayed "uniformly".

If 3GPP/TTML timed text captions are displayed "uniformly", they will have a uniform black outline around each
character.

**Parameters**

| Name        | Description                                                                                     |
|-------------|-----------------|
| isDepressed | TRUE if 3GPP/TTML timed text captions should be displayed "uniformly",FALSE if they should not. |


#### void setVideoSizeInformation (int videoWidth, int videoHeight, int surfaceWidth, int surfaceHeight, int left, int top)

This property specifies the size and position of the video surface on the device’s screen for timed text.

This information is used by the renderer when video is scaled to a different size so that the rendering area can also
be scaled proportionally.

**Parameters**

 
| Name          | Description                                                                          |
|---------------|--------------------------|
| videoWidth    | The width of the displayed video.                                                    |
| videoHeight   | The height of the displayed video.                                                   |
| surfaceWidth  | The width of the surface where video is displayed.                                   |
| surfaceHeight | The height of the surface where video is displayed.                                  |
| left          | The horizontal (X) position of the top left hand corner of the video rendering area. |
| top           | The vertical (Y) position of the top left hand corner of the video rendering area.   |
 
#### void setWindowMargin (int left, int top, int right, int bottom)

This method sets a margin around caption text to the edge of the caption window, for timed text.

**Parameters**

 
| Name   | Description                                                                         |
|--------|-------------------------|
| left   | Sets a margin from the left edge of the caption window to caption text, as an int.  |
| top    | Sets a margin from the top of the caption window to caption text, as an int.        |
| right  | Sets a margin from the right edge of the caption window to caption text, as an int. |
| bottom | Sets a margin from the bottom of the caption window to caption text, as an int.     |
 
### NexCaptionRendererForWebVTT Class Reference

This class defines the renderer view for Web Video Text Tracks (WebVTT) text tracks in HLS content and displays them.

In order for `NexPlayer`™ to display WebVTT, a separate Caption Renderer view must be created with the `NexCaptionRendererForWebVTT` class.

In particular, in order to use `NexCaptionRendererForWebVTT`, care must be taken to do the following:

1. **Pass Video Size Information** : Since the `NexCaptionRendererForWebVTT` view is overlaid on the video
    display in an application, information about the video display must be passed to the caption renderer for the
    WebVTT text to be properly displayed. This means that when the video output size in the application UI is set
    or changes (including the when the video surface is first created), `NexCaptionRendererForWebVTT` should
    also be notified. To do so, the following two methods should be called:
       - `setScaleRatio(float scale)`: When the video is scaled up (for example to fit-screen or full-screen), pass
          the scale ratio to `NexCaptionRendererForWebVTT` with this method.
       - `setVideoSizeInformation(int videoWidth, int videoHeight, int surfaceWidth, int surfaceHeight, int left, int
          top)`: To fit the text render area within the video, `NexCaptionRendererForWebVTT` also needs to know
          the video size and position information provided by calling this method.

2. **Pass Caption Data to the Renderer** : Whenever WebVTT text is updated, the new caption data must be passed to `NexCaptionRendererForWebVTT`. To do this:

 
	- (a) When calling `onTextRenderRender`, the text type must be checked by calling `NexClosedCaption.getTextType`.
	- (b) If that method returns TEXT\_TYPE\_WebVTT for WebVTT text, pass a NexClosedCaption object with the new WebVTT text data to NexCaptionRendererForWebVTT with the setData(`NexClosedCaption
data`) method.
	- (c) Finally, call the NexCaptionRendererForWebVTT.invalidate method when updating the captions.
 
3. **Clear the Text on the Screen** : Whenever WebVTT text must be cleared from the screen (for example when seeking or stopping content), calling clear and invalidate will `clear` any existing text from the device screen.

To display CEA 608 closed captions, CEA 708 closed captions, or timed text (CFF or 3GPP) however, please use the relevant caption renderers, namely one of `NexCaptionRenderer`, `NexEIA708CaptionView`, or `NexCaptionRendererForTimedText`.
 
#### NexCaptionRendererForWebVTT (Context context)

This is the constructor for the WebVTT caption renderer.

**Parameters**

| Name    | Description                |
|---------|--------|
| context | The handle for the player. |
 
#### NexCaptionRendererForWebVTT (Context context, AttributeSet attrs)

This is an alternative constructor for the WebVTT caption renderer.

> **Warning** If the caption view is to be used in Android xml, this constructor must be used.
 
**Parameters**

 
| Name    | Description                                     |
|---------|---------|
| context | The handle for the player.                      |
| attrs   | The set of attributes associated with the view. |
 


#### void clear ( )

This property clears the screen when using the WebVTT caption renderer.
 
#### String getWebVTTAsString (NexClosedCaption caption)

This method gets WebVTT text cue caption data as a String.

**Parameters**

 
| Name    | Description                                         |
|---------|-------------|
| caption | The WebVTT cue data as a `NexClosedCaption` object. |
 
**Returns**

 
The text cue data as a String.
 
 
#### void initCaptionStyle ( )

This method initializes the style attributes of WebVTT text cue captions that may be set by a user, including the
colors of the text, background, and caption window as well as the edge style and the font size.

This API does not effect the default caption style attributes of specific streaming content.


#### void resetEdgeEffect ( )

This method resets the edge effects on WebVTT text cue captions.

Possible edge effects include setShadow, setCaptionStroke, setRaise, and setDepressed.

 
#### void setBGCaptionColor (CaptionColor bgColor, int opacity)

This method sets the background color of WebVTT text cues.

**Parameters**

 
| Name    | Description                                                                                             |
|---------|-------------------------|
| bgColor | The color to be used for the background of text cues (the window color where caption text will appear). |
| opacity | The opacity of the caption window as an integer, from 0 (fully transparent) to 255 (fully opaque).      |
 
#### void setCaptionStroke (CaptionColor strokeColor, int strokeOpacity, float strokeWidth)**

This method sets the stroke color and width of WebVTT text cues.

For a full list of colors, please refer to `NexClosedCaption.CaptionColor`. The stroke line width is in pixels. Antialiasing is supported, so fractions of a pixel are allowed.

**Parameters**

| Name          | Description                                                                         |
|---------------|-------------------------|
| strokeColor   | The stroke color, or null to use the color from the original caption data.          |
| strokeOpacity | The stroke opacity as an integer, from 0 (fully transparent) to 255 (fully opaque). |
| strokeWidth   | The stroke line width as a float, in pixels.                                        |

#### void setCaptionWindowColor (CaptionColor windowColor, int windowOpacity)

This method sets the window color of WebVTT text cue captions.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.


**Parameters**

 
| Name          | Description                                                                         |
|---------------|-------------------------|
| windowColor   | The window color, or null to use the color from the original caption data.          |
| windowOpacity | The window color opacity as an integer, from 0 (transparent) to 255 (fully opaque). |
 
#### void setCenterAlignment ( )

This property sets the captions properties in order to be rendered aligned to the center.

**Deprecated** Use `NexCaptionPainter` class instead of this method.

#### void setData (NexClosedCaption data)

This method specifies the WebVTT text cue caption data to the renderer.

**Parameters**

| Name | Description                                          |
|------|--------------|
| data | The WebVTT caption data a `NexClosedCaption` object. |
 
**See Also**

 
- `NexClosedCaption`

 
#### void setDefaultTextSize (float size)

This method sets the default size of text for WebVTT text cues.


**Parameters**

| Name | Description                                |
|------|------------------------|
| size | The size of the default text in DIP units. |
 
#### void setDepressed (boolean isDepressed)

This method indicates whether or not WebVTT text cue captions should be displayed as if "depressed".

If depressed text cues are to be displayed in a user-defined color, see the method *setDepressedWithColor*
instead.

**Parameters**

 
| Name        | Description                                                                                 |
|-------------|---------------------------------|
| isDepressed | TRUE if the text cues should be displayed as if depressed into the screen; otherwise FALSE. |
 
**See Also**

 
- `NexCaptionRendererForWebVTT.setDepressedWithColor`
 
#### void setDepressedWithColor (boolean isDepressed, CaptionColor depColor, int depOpacity)

This method indicates whether or not WebVTT text cue captions should be displayed as if "depressed" (in a set font
color).

If WebVTT text cue captions are "depressed", they should be displayed as if they are pressed into the video display
slightly, and the color of the depressed part of the text can be set by the user.

**Parameters**

| Name        | Description                                                                                  |
|-------------|----------------------------------|
| isDepressed | TRUE if the text cues are depressed,FALSE if not.                                            |
| depColor    | The color of the depressed part set by the user, or null to use the default color.           |
| depOpacity  | The opacity of the depressed part as an integer, from 0 (transparent) to 255 (fully opaque). |
 
#### void setEmbossBlurRadius (float radius)

This method sets the blur radius of the Emboss Mask filter used when a user sets WebVTT text cues to be displayed
’Raised’ or ’Depressed’ in the UI.

**Parameters**

 
| Name   | Description                                |
|--------|------------------------|
| radius | The blur radius of the Emboss Mask filter. |
 
#### void setEmbossSpecular (float specular)

This method sets the specular level of the Emboss Mask filter used when a user sets WebVTT text cues to be
displayed ’Raised’ or ’Depressed’ in the UI.

**Parameters**

 
| Name     | Description                                   |
|----------|---------------------------|
| specular | The specular level of the Emboss Mask filter. |
 
#### void setFGCaptionColor (CaptionColor fontColor, int opacity)

This method sets the foreground (text) color of WebVTT text cues.


**Parameters**

 
| Name      | Description                                                                         |
|-----------|-------------------------|
| fontColor | The color to be used for caption text.                                              |
| opacity   | The opacity of the text as an integer, where 0 is invisible, and 1 is fully opaque. |
 
#### void setFonts (Typeface normType,Typeface boldType, Typeface italicType, Typeface boldItalicType)

This method sets the fonts to be used for WebVTT text cue captions.

Four typefaces may be specified for different combinations of **bold** anditalics. The caption renderer will select the
appropriate typeface from among these based on the WebVTT text cue captions being displayed.

For best results, specify all four typefaces. Any typeface can be set to *null*, in which case the system default
typeface will be used.

**Parameters**

 
| Name           | Description                                                                         |
|----------------|-------------------------|
| normType       | Typeface to be used for text cue captions that are neither bold nor italic.         |
| boldType       | Typeface to be used for bold WebVTT text cue captions.                              |
| italicType     | Typeface to be used for WebVTT text cue captions in italics.                        |
| boldItalicType | Typeface to be used for WebVTT text cue captions that are both bold and in italics. |
 
#### void setRaised (boolean isRaised)

This method indicates whether or not WebVTT text cue captions should be displayed as if "raised".

To have the raised text cues be displayed in a user-defined color, see the *setRaisedWithColor* method
instead.

**Parameters**

 
| Name     | Description                                                              |
|----------|--------------|
| isRaised | TRUE if the text cues should be displayed as if raised; otherwise FALSE. |
 
**See Also**

 
- `NexCaptionRendererForWebVTT.setRaisedWithColor`
 
#### void setRaisedWithColor (boolean isRaised, CaptionColor raisedColor, int raisedOpacity)

This method indicates whether or not WebVTT text cue captions should be displayed as if "raised" (in a set font
color).

If WebVTT text cue captions are "raised", they should be displayed as if they rise from the video display slightly, and
the color of the raised part of the text can be set by the user.

**Parameters**

 
| Name          | Description                                                                               |
|---------------|-------------------------------|
| isRaised      | TRUE if the text cues are raised,FALSE if not.                                            |
| raisedColor   | The color of the raised part set by the user, or null to use the default color.           |
| raisedOpacity | The opacity of the raised part as an integer, from 0 (transparent) to 255 (fully opaque). |
 
#### void setShadow (boolean isShadow)

This method adds a ’drop shadow’ effect to WebVTT text cue captions.

**Parameters**

| Name     | Description                                                                   |
|----------|-------------------|
| isShadow | TRUE if the captions should be displayed with a drop shadow; otherwise FALSE. |
 
#### void setShadowWithColor (boolean isShadow, CaptionColor shadowColor, int shadowOpacity)

This method sets whether or not WebVTT text cue captions should be displayed with a colored shadow.

**Parameters**

 
| Name          | Description                                                                           |
|---------------|---------------------------|
| isShadow      | Set this to TRUE to force text to be displayed with a shadow, or FALSE for no shadow. |
| shadowColor   | The shadow color, or null to use the color from the original caption data.            |
| shadowOpacity | The shadow opacity as an integer, from 0 (transparent) to 255 (fully opaque).         |
 
#### void setTextSize (int sizeRate)

This method changes the font size of WebVTT text cue captions.

To double the size of the font, the parameter *rate* should be set to 200. In contrast, to halve the size of the font, *rate* should be set to 50 (in other words, 50%).

**Parameters**

| Name     | Description                                                              |
|----------|--------------|
| sizeRate | The change in size of the WebVTT text cue caption font, as a percentage. |
 
#### void setUniform (boolean isUniform)

This method adds a "uniform" filter to WebVTT text cue captions.

**Parameters**

| Name      | Description                                                                              |
|-----------|------------------------------|
| isUniform | TRUE if the text cues should be displayed with a uniform black outline; otherwise FALSE. |
 
#### synchronized void setVideoSizeInformation (int videoWidth, int videoHeight, int surfaceWidth, int surfaceHeight, int left, int top)

This property specifies the size and position of the video surface on the device’s screen for WebVTT captions.

This information is used by the renderer when video is scaled to a different size so that the rendering area can also
be scaled proportionally.

**Parameters**

| Name          | Description                                                                          |
|---------------|--------------------------|
| videoWidth    | The width of the displayed video.                                                    |
| videoHeight   | The height of the displayed video.                                                   |
| surfaceWidth  | The width of the surface where video is displayed.                                   |
| surfaceHeight | The height of the surface where video is displayed.                                  |
| left          | The horizontal (X) position of the top left hand corner of the video rendering area. |
| top           | The vertical (Y) position of the top left hand corner of the video rendering area.   |


#### void setVideoTimeInfo (int currentTime)

This method checks the current time of the content and checks whether it is in the range of a WebVTT text cue (to
determine if it should be rendered and displayed).

> **Warning** This module needs to be added in order to remove captions that are not ’on time’. If the current time of the
playing content is not in the range of text cue’s time stamp, this method returns *false*. This method can be
used to ensure WebVTT text cues are displayed at the proper time while content is playing.
 
**Parameters**

| Name        | Description                                             |
|-------------|-----------------|
| currentTime | The current time of the playing content, as an integer. |
 
**Returns**

 
*FALSE* if the current time is NOT within the range of the WebVTT text cue’s duration range, otherwise *TRUE*.
 
#### void setWindowMargin (int left, int top, int right, int bottom)

This API sets a margin around caption text to the edge of the caption window, for WebVTT text tracks.

**Parameters**

| Name   | Description                                                           |
|--------|-------------------------------|
| left   | Sets margin from the left edge of window to caption text, as an int.  |
| top    | Sets margin from the top of window to caption text, as an int.        |
| right  | Sets margin from the right edge of window to caption text, as an int. |
| bottom | Sets margin from the bottom of window to caption text, as an int.     |

 
### NexCaptionWindowRect Class Reference

This class manages the position of captions for NexCaptionSetting.

**Classes**

- class RenderingArea

**Protected Member Functions**

- `void clearCaptionString ()`
- `void setRenderingArea (RenderingArea area)`
- `void renderClosedCaption (int captionType, final NexClosedCaption textInfo)`


#### NexCaptionRenderView (Context context)

Constructor for NexCaptionRenderView.

**Parameters**

| Name    | Description                                                                    |
|---------|--------------------|
| context | The Context instance associated with the activity that will contain this view. |


#### NexCaptionRenderView (Context *context*, AttributeSet *attrs*)

Constructor for NexCaptionRenderView.

**See Also**

- NexVideoRenderer.NexVideoRenderer(android.content.Context)

#### NexCaptionAttribute getCaptionAttribute ( )

This method gets the attribute information set to the current caption.

**Returns**


The NexCaptionAttribute object set to the current caption.


#### void setCaptionAttribute (NexCaptionAttribute attribute)

This method sets the attributes of captions used by the NexVideoView.

**Parameters**

| Name      | Description                   |
|-----------|-----------|
| attribute | A NexCaptionAttribute object. |

#### void setExternalSubtitleTextView (TextView *textview*, LayoutParams *param*, String *encodingPreset*)

This method sets the text view to display external subtitles.

**Parameters**

| Name        | Description                                                  |
|-------------|----------------------|
| textview    | A TextView instance.                                         |
| param       | The layout parameters associated with the textview           |
| charsetName | Converts the byte array to a string using the named charset. |


### NexCaptionSetting Class Reference

This class manages the attributes of the captions for `NexCaptionPainter`.

**Classes**

- enum EdgeStyle
   This enumeration defines the caption edge style.
- enum StringStyle
    This enumeration defines the behavior for caption string style.

**Public Attributes**

- `SparseIntArray mappedFontColors`


    This indicates the caption fonts as argb colors.
- `int mWindowColor`


    This indicates the caption window as an argb color.
- `int mEdgeColor`


	 This indicates the caption edge as an argb color.
- `float mEdgeWidth`


    This indicates the thickness of edge.
- `int mGravity`


    This indicates alignment of caption.
- `float mFontScale`


    This indicates scale of font size, as afloat.
- `int mPaddingLeft`


    This indicates margin from the left edge of the caption window to caption text, as anint.
- `int mPaddingTop`


    This indicates margin from the top edge of the caption window to caption text, as anint.
- `int mPaddingRight`


    This indicates margin from the right edge of the caption window to caption text, as anint.
- `int mPaddingBottom`


    This indicates margin from the bottom edge of the caption window to caption text, as anint.
- `Typeface mFontFamily`


    This indicates the fonts to be used captions as a Typeface.
- `EdgeStyle mEdgeStyle`


    This indicates edge style of caption.
- `int mBackgroundColor`


    This indicates the caption background as an argb color.
- `int mFontColor`


    This indicates the caption font as an argb color.
- `StringStyle mBold`


    This indicates the bold string style.
- `StringStyle mItalic`


    This indicates the italic string style.
- `StringStyle mUnderLine`


    This indicates the underline string style.
- `float mFontSize`


    This indicates the font size in px, as a float.
- `NexCaptionWindowRect mRelativeWindowRect`


    This indicates the position of caption.

**Static Public Attributes**

- `static final int DEFAULT = 0x00FFFFFE`

    This indicates that a property set by the contents will be applied.


#### NexCaptionSetting( )

Constructor of NexCaptionSetting.

The attributes will be initialized by NexCaptionSetting.DEFAULT


#### NexCaptionSetting (NexCaptionSetting ref)

Constructor of NexCaptionSetting.

The attributes will be generated by initializing settings object values.

**Parameters**

| Name | Description                 |
|------|---------|
| ref  | A NexCaptionSetting object. |



#### void copyAllSettings (NexCaptionSetting ref)

This method sets the values of the attributes by settings the object values including NexCaptionSetting.DEFAULT.

**Parameters**

| Name | Description                 |
|------|---------|
| ref  | A NexCaptionSetting object. |

#### void copyTouchedSettings (NexCaptionSetting ref) 

This method sets the values of the attributes by settings the object values excepting NexCaptionSetting.DEFAULT.

**Parameters**

| Name | Description                 |
|------|---------|
| ref  | A NexCaptionSetting object. |



#### SparseIntArray mappedFontColors

This indicates the caption fonts as argb colors.

It is used to replace with the colors provided by the content.

> **Note** This has a lower priority than NexCaptionSetting.mFontColor. Input key (argb color you want to change) and
value (desired argb color) using append() or put().

mNexCaptionSetting.mappedFontColors.append(Color.WHITE, Color.GRAY);
mNexCaptionSetting.mappedFontColors.put(Color.WHITE, Color.GRAY);


#### StringStyle mBold

This indicates the bold string style.

**See Also**


- NexCaptionSetting.StringStyle

#### EdgeStyle mEdgeStyle

This indicates edge style of caption.

**See Also**


- NexCaptionSetting.EdgeStyle

#### int mGravity

This indicates alignment of caption.

**See Also**

- android.view.Gravity

#### StringStyle mItalic

This indicates the italic string style.

**See Also**

- NexCaptionSetting.StringStyle

#### NexCaptionWindowRect mRelativeWindowRect

This indicates the position of caption.

It can be set to a percentage of the caption render area.

**See Also**

- NexCaptionWindowRect

#### StringStyle mUnderLine

This indicates the underline string style.

**See Also**


- NexCaptionSetting.StringStyle


### NexCaptionTextView Class Reference

This class is used internally to manage captions.

Please do not use. The other caption-related classes in NexPlayer™ should be used instead.


**Classes**

- `class SubStringDrawInfo`

**Public Member Functions**

- `NexCaptionTextView (Context context)`

**Protected Member Functions**

- `void setCaptionStroke (CaptionColor color, int opacity, float strokeWidth)`
- `void setCaptionStroke (int color, float strokeWidth)`
- `void setRaised (boolean isTrue)`
- `void setRaised (boolean isTrue, int raisedColor)`
- `void setDepressed (boolean isTrue)`
- `void setDepressed (boolean isTrue, int depColor)`
- `void setUniform (boolean isTrue)`
- `void setDropShadow (boolean isTrue)`
- `void setDropShadow (boolean isTrue, int color)`
- `void setDropShadow (boolean isTrue, float radius, float dx, float dy, int color)`
- `void initEdgeStyle ()`
- `int  getColorFromCapColor (CaptionColor cColor, int cOpacity)`
- `void setBaseTextColor (int color)`
- `void setBaseBackgroundColors (Spannable spannableString)`
- `void onDraw (Canvas canvas)`

**Protected Attributes**

- `float[ ] APPLY_SHADOW_PARAM = {0.0f, 0.0f, 0.0f}`


### NexCaptionView Class Reference


**Public Attributes**

- `final int CAPTION_EDGE_ATTR_NONE = 0`
- `final int CAPTION_EDGE_ATTR_DROP_SHADOW = 1`
- `final int CAPTION_EDGE_ATTR_RAISED = 2`
- `final int CAPTION_EDGE_ATTR_DEPRESSED = 3`
- `final int CAPTION_EDGE_ATTR_UNIFORM = 4`

**Static Public Attributes**

- `static final String LOG_TAG = "NexCaptionViewer"`

**Protected Member Functions**

- `void onDraw (Canvas canvas)`
- `void onLayout (boolean arg0, int arg1, int arg2, int arg3, int arg4)`

#### void changeFontSize ( float *sizePercentage* )

This method changes the font size of 3GPP/TTML captions.

The size of text font can be changed from 50 to 200 percent of the original caption font size.

**Parameters**

| Name           | Description                                    |
|----------------|--------|
| sizePercentage | The percentage change in font size, as a float |

#### void setBGCaptionColor (CaptionColor *background*, int *bgOpacity*)

This sets the background color of 3GPP/TTML captions.

For a full list of colors , please refer to NexClosedCaption.CaptionColor.

**Parameters**

| Name       | Description                                                                    |
|------------|--------------------|
| background | The background color, or null to use the color from the original caption data. |
| bgOpacity  | The background opacity, from 0 (transparent) to 255 (fully opaque).            |


#### void setBold (boolean *isBold*)

This method controls whether captions are displayed in bold text.

Caption data includes attributes such as **bold** and *italics*.

Normally, the caption renderer displays each character in normal, **bold** or *italics* based on the attributes included in the caption data.

However in some cases (such as for users with visual impairment) it may be desirable to force the use of **bold** text.

By enabling this option, the bold attributes in the caption data are ignored and a bold font is used for all characters.

**Parameters**

| Name   | Description                                                                                       |
|--------|-------------------|
| isBold | Set this to TRUE to force bold text, or FALSE to use the bold attribute in the original captions. |

#### void setCaptionRenderArea (int *videoWidth*, int *videoHeight*, int *surfaceWidth*, int *surfaceHeight*, int *left*, int *top*)

This property specifies the rendering area within the displayed video area.

This information is used by the renderer when video is scaled to a different size so that the rendering area can also
be scaled proportionally.

**Parameters**

| Name          | Description                                                                          |
|---------------|--------------------------|
| videoWidth    | The width of the displayed video.                                                    |
| videoHeight   | The height of the displayed video                                                    |
| surfaceWidth  | The width of the surface where video is displayed.                                   |
| surfaceHeight | The height of the surface where video is displayed                                   |
| left          | The horizontal (X) position of the top left hand corner of the video rendering area. |
| top           | The vertical (Y) position of the top left hand corner of the video rendering area    |

#### void setCaptionStroke ( CaptionColor *strokeColor*, int *strokeOpacity*, float *strokeWidth* )

This sets the 3GPP/TTML caption renderer stroke color and width.

For a full list of colors, please refer to NexClosedCaption.CaptionColor. The stroke line width is in pixels. Anti-aliasing is supported, so fractions of a pixel are allowed.



**Parameters**

| Name        | Description                                                                |
|-------------|----------------|
| strokeColor | The stroke color, or null to use the color from the original caption data. |
| strokeColor | The stroke opacity, from 0 (transparent) to 255 (fully opaque).            |
| strokeWidth | The stroke width in pixels.                                                |

#### void setCaptionWindowColor (CaptionColor *windowColor*, int *windowOpacity*)

This method sets the window color of 3GPP/TTML captions.

This is similar to setting a background color behind the caption text.

For a full list of colors , please refer to NexClosedCaption.CaptionColor.

**Parameters**

| Name          | Description                                                              |
|---------------|--------------|
| windowColor   | The window color, or null to use the color from the original caption data. |
| windowOpacity | The window color opacity, from 0 (transparent) to 255 (fully opaque).    |
#### void setDepressed ( boolean *isDepressed* )

This method indicates whether or not captions should be displayed as if "depressed".

If captions are "depressed", they should be displayed as if pressed into the video display slightly.

**Parameters**

| Name        | Description                                                                |
|-------------|----------------|
| isDepressed | TRUE if the captions should be displayed as if depressed, otherwise FALSE. |

#### void setEmbossBlurRadius ( float *radius* )**

This method sets the blur radius of the Emboss Mask filter used when a user sets caption to be ’Raised’ or ’De-pressed’ in the UI.


**Parameters**

| Name   | Description                                |
|--------|------------------------|
| radius | The blur radius of the Emboss Mask filter. |

#### void setEmbossSpecular ( float *specular* )

This method sets the specular level of the Emboss Mask filter used when a user sets caption to be ’Raised’ or ’Depressed’ in the UI.

**Parameters**

| Name     | Description                                  |
|----------|--------------------------|
| specular | The specular level of the Emboss Mask filter |

#### void setFGCaptionColor (CaptionColor *foreground*, int *fgOpacity*)

This property describes the video’s scale ratio.

When a displayed video changes in size on the screen (as for example when a video is displayed full screen), this ratio should be used to scale the text renderer accordingly as well.

**Parameters**

| Name  | Description                                                                      |
|-------|----------------------|
| scale | The video’s scale ratio.This method sets the foreground (text) color of captions |

For a full list of colors , please refer to NexClosedCaption.CaptionColor.

**Parameters**

| Name       | Description                                                                    |
|------------|--------------------|
| foreground | The foreground color, or null to use the color from the original caption data. |
| fgOpacity  | The foreground opacity, from 0 (transparent) to 255 (fully opaque).            |

#### void setFonts (Typeface *normType*, Typeface *boldType*, Typeface *italicType*, Typeface *boldItalicType*)

This method sets the fonts to be used for the captions.

Four typefaces may be specified for different combinations of bold and italic. The caption renderer will select the appropriate typeface from among these based on the captions being displayed.


For best results, specify all four typefaces. Any typeface can be set tonull, in which case the system default typeface will be used.

**Parameters**

| Name           | Description                                                        |
|----------------|----------------------------|
| normType       | Typeface to be used for captions that are neither bold nor italic. |
| boldType       | Typeface to be used for bold captions                              |
| italicType     | Typeface to be used for italic captions.                           |
| boldItalicType | Typeface to be used for captions that are both and italic          |

#### void setRaise (boolean *isRaise*)

This method indicates whether or not captions should be displayed as if "raised".

If captions are "raised", they should be displayed as if rising above the video display slightly, for example as if they were embossed.

**Parameters**

| Name    | Description                                             |
|---------|-----------------|
| isRaise | TRUE if the captions are raised, FALSE if they are not. |

#### void setShadow (boolean *isShadow*, CaptionColor *sColor*, int *sOpacity*)

This method sets whether or not captions should be displayed with a shadow.

**Parameters**

| Name     | Description                                                                          |
|----------|--------------------------|
| isShadow | Set this to TRUE to force text to be displayed with a shadow, or FALSE for no shadow |

#### void setUniform (boolean *isUniform*)

This method indicates whether or not captions should be displayed "uniformly".

If captions are displayed "uniformly", they will have a uniform black outline around each character.


**Parameters**

| Name        | Description                                                                 |
|-------------|-----------------|
| isDepressed | TRUE if captions should be displayed "uniformly", FALSE if they should not. |

### NexCaptionWindowRect Class Reference

This class manages the position of captions for NexCaptionSetting.


#### NexCaptionWindowRect( )

Constructor of NexCaptionWindowRect.

The values in NexCaptionWindowRect will be initialized with NexCaptionSetting.DEFAULT


#### NexCaptionWindowRect (NexCaptionWindowRect *ref*)

Constructor of NexCaptionWindowRect.

The values will be generated by initializing settings object values.

Parameters

| Name | Description                    |
|------|------------|
| ref  | A NexCaptionWindowRect object. |



#### void copyAllSettings (NexCaptionWindowRect *ref*)

This method sets the values by settings object values including NexCaptionSetting.DEFAULT.

Parameters

| Name | Description                    |
|------|------------|
| ref  | A NexCaptionWindowRect object. |

#### void copyTouchedSettings (NexCaptionWindowRect *ref*)

This method sets the values by settings object values excepting NexCaptionSetting.DEFAULT.

Parameters

| Name | Description                    |
|------|------------|
| ref  | A NexCaptionWindowRect object. |


#### boolean autoAdjustment

This indicates that the position is adjusted by NexPlayer.

It should be set to false if the position is set by the user.

Default: true Automatically adjusted by NexPlayer

#### int heightPercent

This indicates the height of the caption window.

It can be set to a percentage of the vertical caption render area.


#### boolean userDefined

This indicates ifthe position is set by user or not.

It should be set to true if the position set by the user should be applied instead of the position set by the content.

Default: false Set by content.

#### int widthPercent

This indicates the width of the caption window.

It can be set to a percentage of the horizontal caption render area.

#### int xPercent

This indicates the left position of the caption window.

It can be set to a percentage of the horizontal caption render area.

#### int yPercent

This indicates the top position of the caption window.

It can be set to a percentage of the vertical caption render area.

### NexClosedCaption Class Reference


This class handles the subtitles and closed captions data of content.

NexPlayer™ uses this class to handle SMI, SRT, SUB, and Smooth Streaming subtitles as well as CEA 608 and
CEA 708 closed captions included in HLS content, 3GPP and CFF timed text as well as WebVTT text tracks.

>Warning Certain methods though may only be called to handle specifically CEA 608 closed captions, CEA 708 closed
captions, timed text, or WebVTT text tracks, so care must be taken when implementing support for those
captions.

Text information from standard subtitle files (SMI, SRT, SUB, and Smooth Streaming subtitles) is handled by the getTextData method while the text of CEA 608 close captions, 3GPP timed text, and WebVTT captions must each be handled separately by, respectively, getString, getTextDataFor3GPPTT, and getTextDataForWebVTT. In the case of CFF timed text (TTML), text data is handled separately by the getTextDataforTTML method.

For CEA 708 closed captions, please see NexEIA708Struct and NexEIA708CaptionView.

The instance of NexClosedCaption is delivered through the onTextRenderRender method for regular subtitles.

When timed text, CEA 608 closed captions, or WebVTT are implemented however, it is necessary to create and display the captions in a separate caption renderer, like NexCaptionRendererForTimedText, NexCaptionRenderer, and. For example, CEA 608 captions can be displayed one character at a time and thus the position of each character must be considered. The vertical position of each character is set by a row number, rowbetween 0 and 15, while the horizontal position of the character is set by a column number, colbetween 0 and 32. NexPlayer.IListener.onTextRenderRender, NexCaptionRenderer, NexEIA708Struct, NexEIA708CaptionView, NexCaptionRendererForTimedText, and NexCaptionRendererForWebVTT for additional details.
**Classes**

- `enum CaptionColor`


    This enumeration sets the text display and background colors of CEA 608 closed captions.
- `enum CaptionMod`


    This enumeration sets how CEA 608 closed captions will be displayed (in FULL mode only).
- `enum Charset`


    This enumerator defines the encoding character set to be used for CEA 608 closed captions (in FULL mode only).
- `class TextBlink`


    This property requests blinking text for the indicated character range.
- `class TextHighlight`


    This property specifies the position of the highlighted text.
- `class TextHighlightColor`


    This property specifies the color of the highlighted text.
- `class TextHyperText`


    This property specifies the hyperlink of text that describes the hypertext information.
- `class TextKaraoke`


    This property specifies the number of highlighted text.
- `class TextKaraokeEntry`


    This property specifies the karaoke type highlighted text.
- `class TextScrollDelay`


    This property specifies the delaying time of the scrolling text.
- `class TextStyle`


	This property specifies the style of the text and sets the TextStyleEntry.
- ´class TextStyleEntry´


    Both the sample format and the sample description contain style records, so it is define here for compactness.
- `enum TextWrap`


    This property specifies the text wrap behavior.
- `enum TTML_DisplayAlign`


    This enumeration determines the display alignment of CFF timed text (TTML) in content.
- `enum TTML_Fontstyle`


    This enumeration determines the font style of CFF timed text (TTML) in content.
- `enum TTML_LengthType`


    This enumeration specifies which type of length is being used in the style properties of a content’s timed text (TTML).
- `class TTML_StyleLength`


    This class describes the length of every timed text (TTML) attribute.
- `enum TTML_TextAlign`


    This enumeration determines the horizontal alignment of timed text (TTML) in content.
- `class TTML_TextOutlineStyleLength`


    This class determines how timed text (TTML) in content should be displayed in text outline format.
- `enum TTML_UnicodeBIDI`


    This enumeration specifies a directional embedding or override of text direction for timed text (TTML) in content.
- `enum TTML_WritingMode`


    This enumeration specifies the mode in which timed text (TTML) in content will be displayed.
- `class TTMLRenderingData`


- `enum WebVTT_CueSpanTag`


    This enumeration defines the text track cue span tags for how WebVTT text tracks should be displayed.
- `enum WebVTT_TextAlign`


    This enumeration determines the horizontal alignment of timed text (WebVTT) in content.
- `enum WebVTT_WritingDirection`


    This enumeration specifies how WebVTT captions in content will be displayed.
- `class WebVTTRenderingData`



**Static Public Attributes**

- `static final int TEXT_TYPE_UNKNOWN = 0`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_GENERAL = 1`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_EXTERNAL_TTML = 5`


	This is a possiblereturnvalue for NexClosedCaption.getTextType().

- `static final int TEXT_TYPE_ATSCMH_CC = 0x11`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_ATSCMH_BAR = 0x12`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_ATSCMH_AFD = 0x13`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_NTSC_CC_CH1 = 0x14`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_NTSC_CC_CH2 = 0x15`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_3GPP_TIMEDTEXT = 0x20`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_TTML_TIMEDTEXT = 0x25`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_WEBVTT = 0x30`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_SMI = 0x40`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_SRT = 0x41`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int TEXT_TYPE_SUB = 0x42`


    This is a possiblereturnvalue for NexClosedCaption.getTextType().
- `static final int ENCODING_TYPE_ISO8859_1 = 0x0`


    This is a possiblereturnvalue for NexClosedCaption.getEncodingType().
- `static final int ENCODING_TYPE_UTF16 = 0x1`


    This is a possiblereturnvalue for NexClosedCaption.getEncodingType().
- `static final int ENCODING_TYPE_UTF16_BE = 0x2`


    This is a possiblereturnvalue for NexClosedCaption.getEncodingType().
- `static final int ENCODING_TYPE_UTF8 = 0x3`


    This is a possiblereturnvalue for NexClosedCaption.getEncodingType().
- `static final int ENCODING_TYPE_ASCII = 0x10`


    This is a possiblereturnvalue for NexClosedCaption.getEncodingType().
- `static final int ENCODING_TYPE_UNICODE = 0x20`


    This is a possiblereturnvalue for NexClosedCaption.getEncodingType().
- `static final int ENCODING_TYPE_EUC_KR = 0x21`


    This is a possiblereturnvalue for NexClosedCaption.getEncodingType().
- `static final int ENCODING_TYPE_UNKNOWN = 0xFFFFFFFF`


    This is a possiblereturnvalue for NexClosedCaption.getEncodingType().
- `static final int ROLLED_OUT_ROW = -1`


    In FULL mode, when CEA 608 closed captions are to be displayed and "rolled up" with animation, this defines the row that is being "rolled out" of the display during the animation, in other words the row that is disappearing as the next, new row of captions appears.

**Static Protected Attributes**

- `static final float[ ] DEFAULT_RAISED_PARAM = {2.0f, 0.0f, 3.0f}`
- `static final float[ ] DEFAULT_DEPRESSED_PARAM = {2.0f, -3.0f, -3.0f}`
- `static final float[ ] DEFAULT_SHADOW_PARAM = {####f, 0.0f, ####f}`
- `static final int DEFAULT_SHADOW_COLOR = 0xCC000000`



#### int getAlignTypeForWebVTT ( )

This method gets the align type data of a WebVTT cue.

**Returns**

 
A byte array with the align type data for the content’s WebVTT.
 
 
#### boolean getAvailableCaptionChannel (int channelNumber)

This method checks if CEA 608 closed caption information is available for the given channel.

By checking how much time has passed since the channel information was updated (with the method getCaptionUpdateTime), this method can determine if there is any closed caption information available on this channel to be displayed. This allows the player to present the available CEA 608 channels to the user in order for the desired channel to be selected.

Different channels often provide different closed caption information, for example in different languages, but the four specified channels may not always be used or available for any particular content.

**Parameters**

| Name    | Description                |
|---------|--------|
|channelNumber| The CEA 608 channel number to check for closed caption information availability. This will be 1, 2, 3, or 4.|
 
**Returns**
 
TRUE if the channel has available information, FALSE if no recent closed caption information is available on the given channel.
 
**See Also**

getCaptionUpdateTime
 
 
#### int getBackgroundColorFor3GPPTT ( )

This property gets color of the rectangle text box.

**Returns**

 
The color of the rectangle text box.
 
#### CaptionColorgetBGColor (int row, int col)

This determines the background color to display behind the character in CEA 608 closed captions (FULL mode).

Parameters
**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.|
|col| The column or horizontal position of the character to be displayed.|
  
**Returns**

 
The background color to display.
 
**See Also**

 
CaptionColor for color options available for CEA 608 closed captions in FULL mode.
 
#### int getBGColor ( )

This method returns the background color of CEA 608 closed captions.

**Returns**

 
The background color of the displayed caption text as an ARGB hexacode. This will be one of:
 
- White = 0xFFFFFFFF
- Green = 0xFF00FF00
- Blue = 0xFF0000FF
- Cyan = 0xFF00FFFF
- Red = 0xFFFF0000
- Yellow = 0xFFFFFF00
- Magenta = 0xFFFF00FF
- Black = 0xFF000000 (default)
- Transparent = 0x00000000

> **Deprecated** Do not use.

#### int getBGColorforTTML ( )

This method gets the background color for timed text (TTML) in content.

It corresponds to the tts:backgroundColorattribute, and specifies the color of the background region on which timed text (TTML) should be displayed.

**Returns**

 
The background color of the timed text (TTML) as an integer.
 
 
#### int getCaptionColor ( )

This method returns the text display color of CEA 608 closed captions.

**Returns**

 
The color of the displayed caption text as an ARGB hexacode. This will be one of:
 
- White = 0xFFFFFFFF (default)
- Green = 0xFF00FF00
- Blue = 0xFF0000FF
- Cyan = 0xFF00FFFF
- Red = 0xFFFF0000
- Yellow = 0xFFFFFF00
- Magenta = 0xFFFF00FF
- Black = 0xFF000000
- Transparent = 0x00000000

> **Deprecated** Do not use.

#### CaptionModegetCaptionMode ( )

This gets the display mode for the CEA 608 closed captions when supported in FULL mode.

**Returns**

 
The CaptionMode of how the captions should be displayed. This will be one of:
 
- CaptionMode.None
- CaptionMode.RollUp
- CaptionMode.PopOn
- CaptionMode.PaintOn
- CaptionMode.Text

See Also

 
The CaptionMode enumeration for more details on the ways in which captions can be displayed. displaytext/rollup/paint on modes etc
 
#### int getCaptionType ( )

This method returns the caption type converted from the NexClosedCaption type to the NexContentInformation.

**Returns**

 
The type of text to be displayed. This will be one of:
 
- NEX\_TEXT\_UNKNOWN = 0x00000000: Unknown caption format.
- NEX\_TEXT\_EXTERNAL\_SMI = 0x00000002: SMI subtitles.
- NEX\_TEXT\_EXTERNAL\_SRT = 0x00000003: SRT subtitles.
- NEX\_TEXT\_3GPP\_TIMEDTEXT = 0x####: 3GPP timed text.
- NEX\_TEXT\_WEBVTT = 0x####: WebVTT text tracks.
- NEX\_TEXT\_TTML = 0x####: TTML timed text.
- NEX\_TEXT\_CEA = 0x####: Closed captions.
- NEX\_TEXT\_CEA608 = 0x####: CEA608 caption.
- NEX\_TEXT\_CEA708 = 0x####: CEA708 caption.

#### long getCaptionUpdateTime (int channelNumber)

This gets the time at which the CEA 608 closed captions in the given channel were last updated.

This function allows NexPlayer™ to determine if caption information is available on the given channel, and thus determine which CEA 608 channels are available for the playing content, using the method getAvailableCaptionChannel.

**Parameters**

| Name    | Description                |
|---------|--------|
|channelNumber| The CEA 608 channel in which to get the time at which the captions were last updated. This will be 1, 2, 3, or 4.|
 
**Returns**

 
The time at which the caption content was last updated for the channel passed, in milliseconds (ms).
 
**See Also**

 
getAvailableCaptionChannel

 
#### char getCharCode (int row, int col)

This gets the character to display in CEA 608 closed captions (FULL mode).

**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.|
|col| The column or horizontal position of the character to be displayed.|

 
**Returns**

 
The character to be displayed.
 
#### CharsetgetCharset (int row, int col)

This gets the encoding set for the character in CEA 608 closed captions.

**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.|
|col| The column or horizontal position of the character to be displayed.|
 
**Returns**

 
The character encoding set to be used. This will be one of:
 
- UNICODE\_UCS2(0) : Unicode characters, including special characters for French and Spanish accents.
- PRIVATE\_1(1): Not currently used but reserved for future use. Can be ignored.
- PRIVATE\_2(2): Not currently used but reserved for future use. Can be ignored.
- KSC\_####\_1987(3): Korean characters encoding.
- GB\_2312\_80(4): Chinese characters encoding.

#### boolean getContinuousKaraoke ( )

This property specifies the ContinuousKaraoke.

**Returns**

 
TRUE if YES , FALSE if No.
 
#### int getCueIDForWebVTT ( )

This method gets the ID of the current WebVTT text cue.

**Returns**

 
The ID of the current WebVTT text cue, as an integer.
 
 
> **Deprecated** Do not use.

#### List < byte[ ] > getCueTagListForWebVTT ( )

This method gets the list of WebVTT cue tags in WebVTT text tracks in content.

**Returns**

 
A list of byte arrays with the WebVTT cue tags.
 
> **Deprecated** Do not use.

#### int getCurrentTimeStampForWebVTT ( )

This method gets the current timestamp for WebVTT text cue captions.

**Returns**

 
The current timestamp of WebVTT text cue captions, as an integer.
 
 
> **Deprecated** Do not use.

#### int getDirectionForWebVTT ( )

This method gets the text direction data of a WebVTT cue.

**Returns**

 
A byte array with the text direction data for the content’s WebVTT.
 
 
#### TTML\_DisplayAligngetDisplayAlignforTTML ( )

This method gets the display alignment for timed text (TTML) in content.

It corresponds to the tts:displayAlignattribute and returns the relevant alignment in the display region that is determined in the TTML\_DisplayAlign enumeration.

**Returns**

 
The display alignment, which will be one of:
 
- Default = 0
- Before = 1
- Center = 2
- After = 3

**See Also**

 
TTML\_DisplayAlign for more information.
 

#### int getEncodingType ( )

This determines the encoding type of the content’s captions or subtitles, when available.

**Returns**

 
The encoding type of the subtitles or captions. This will be one of the following values:
 
- ENCODING\_TYPE\_ISO8859\_1 (0x0)
- ENCODING\_TYPE\_UTF16 (0x1)
- ENCODING\_TYPE\_UTF16\_BE (0x2)
- ENCODING\_TYPE\_UTF8 (0x3)
- ENCODING\_TYPE\_ASCII (0x10)
- ENCODING\_TYPE\_UNICODE (0x20)
- ENCODING\_TYPE\_EUC\_KR (0x21)
- ENCODING\_TYPE\_UNKNOWN (0xFFFFFFFF)

#### int getEndTimeStampForWebVTT ( )

This method gets the ending timestamp for WebVTT text cue captions.

**Returns**

 
The ending timestamp of the WebVTT text cue as an integer.
 
 
#### TTML\_StyleLengthgetExtentHeight ( )

This method gets the height of the region area where timed text (TTML) in content is to be displayed.

It corresponds to the height dimension specified in tts:extentattribute, and may also be the height of the root
container region.

Note that if the tts:extentattribute is set toauto, the display region should be considered to have the same
height as the root container extent.

**Returns**

 
The height of the text region as a TTML\_StyleLength object.
 
 
#### TTML\_StyleLengthgetExtentWidth ( )

This method gets the width of the region area where timed text (TTML) in content is to be displayed.

It corresponds to the width dimension specified in tts:extentattribute, and may also be the width of the root container region.

Note that if the tts:extentattribute is set toauto, the display region should be considered to have the same width as the root container extent.

**Returns**

 
The width of the text region as a TTML\_StyleLength object.
  
#### CaptionColorgetFGColor (int row, int col)

This determines the color to display the character in CEA 608 closed captions (FULL mode).


**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.|
|col| The column or horizontal position of the character to be displayed.|
 
 
**Returns**

 
TRUE if italicized, FALSE if not.
 
#### boolean getFillTextRegion ( )

This property bacground region of the text.

**Returns**

 
TRUE if YES , FALSE if No.
 
#### int getFontColorforTTML ( )

This method gets the font color for timed text (TTML) in content.

It corresponds to the tts:colorattribute, and specifies the font color that should be displayed for timed text (TTML).

**Returns**

 
The foreground color of the timed text (TTML) as an integer.
 
 
#### String getFontFamilyNameforTTML ( )

This method determines the font family to be used for timed text (TTML) in content.

It corresponds to the tts:fontFamilyattribute.

**Returns**

 
The font family to be used for timed text (TTML) as a string.
 
 
#### TTML\_StyleLength[ ] getFontSize ( )

This method gets the font size of timed text (TTML) in content.

It corresponds to the tts:fontSizeattribute, and indicates how large timed text (TTML) should be displayed.

**Returns**

 
The font size as a TTML\_StyleLength array, where if only one length is specified, it is to be used as the horizontal and vertical scaling of text glyph’s square, and if two are specified, the first length corresponds to the horizontal scaling and the second to the vertical scaling of the text glyph.
 
#### TTML\_FontstylegetFontStyleforTTML ( )

This method gets the font style for timed text (TTML) in content.

It corresponds to the tts:fontStyleattribute and indicates how timed text should be displayed.

**Returns**

 
The font style for the timed text (TTML) in content. This will be one of:
 
- Default (0)
- Normal (1)
- Italic (2)
- Oblique (3)

**See Also**

 
TTML\_Fontstyle for more information.
 
#### int [ ] getFontTableIndex ( )

This property describes the font index of the text.

#### int getForegroundColorFor3GPPTT ( )

This property gets default color of the text.

**Returns**

 
The color of the text.
 
#### int getHorizontalJustification ( )

This property justify the alignment of the text horizontally, which are left, centre and right.

**Returns**

 
The alignment of the text. This will be one of the following values:
 
- Left (0)
- Centre (1)
- Right (-1)

#### String getHtmlDataForWebVTT ( )

This method gets the HTML data for WebVTT text cues in WebVTT text tracks in content.

**Returns**

 
a string including the HTML data of the specified WebVTT text cue.
 
 
> **Deprecated** Do not use.

#### int getIndent ( )

This method returns the text’s horizontal position for CEA 608 closed captions only.

CEA 608 closed captions will be indented horizontally based on this value. There are 8 possible horizontal column positions, 1 being at the far left of the screen and 8 indented to the far right.

**Returns**

 
The horizontal position at which to display the caption. This will be an integer value from 1 to 8.
 
#### TTML\_StyleLengthgetLineHeight ( )

This method gets the line height of timed text (TTML) in content.

It corresponds to the tts:lineHeightattribute, and can be used to vertically space out lines of timed text
(TTML) when displayed.

**Returns**

 
The line height as a TTML\_StyleLength object.
 
 
#### String getLinePositionForWebVTT ( )

This method gets the line position data of a WebVTT cue.

**Returns**

 
A byte array with the line position data for the content’s WebVTT.
 
 
#### float getOpacityforTTML ( )

This method gets the opacity of the timed text (TTML) in content.

It corresponds to the tts:opacityattribute, and specifies the opacity or transparency of a region of timed text (TTML) in content.

It should be a value between 0 and 1, where 0 is fully transparent and 1 is opaque.

**Returns**

 
The opacity of the timed text (TTML) as afloatbetween 0 and 1.
 
#### TTML\_StyleLength[ ] getOrigin ( )

This method gets the origin of the text display region for timed text (TTML) in content with respect to the root
container extent or external authoring context.

This corresponds to the tts:originattribute and will either beauto, where the origin can be treated as the same as the root container origin, or as two lengths, the first of which must be interpreted as the x coordinate and
the second as the y coordinate of the origin of the text display region.

**Returns**

 
The origin of the text display region for timed text (TTML) as a TTML\_StyleLength array.
 
#### TTML\_StyleLength[ ] getPadding ( )

This method gets the padding to be included around timed text (TTML) in content.

It corresponds to the tts:paddingattribute and can include up to four lengths, indicating the padding to be included around the timed text (TTML) when displayed.

If only one length is specified, it applies to all edges of the text display box. If there are two lengths specified, the first applies to the "before" and "after" edges (the top and bottom edges of the text box for typical Latin script) and the second to the "start" and "end" edges (or right and left edges for typical Latin script). If there are three length specifications, the first corresponds to the "before" edge, the second to the "start" and "end" edges, and the third to the "after" edge. Lastly, if four padding lengths are provided, they should be applied to the before, end, after, and start edges in the corresponding order.

**Returns**

 
The available padding lengths as a TTML\_StyleLength array.
 
 
#### int [ ] getRegionAnchorForWebVTT ( )

This method gets the region anchor data of a WebVTT cue.

**Returns**

 
A byte array with the region anchor data for the content’s WebVTT.

 
> **Deprecated** Do not use.

#### String getRegionIDForWebVTT ( )

This method gets the region ID data of a WebVTT cue in content.

**Returns**

 
A String with region ID of the content’s WebVTT text.
 
#### long getRollUpElapsedTime ( )

This gets the time to be taken to "roll up" between rows or the animation time for CEA 608 closed captions in FULL
mode.

**Returns**

 
The time in milliseconds it takes for a row to "roll up" to the next row, as along.
 
#### int getRollUpNumRows ( )

This gets the number of roll-up rows to be displayed when CEA 608 closed captions are to be displayed "rolling up"
in FULL mode.

**Returns**

 
The number of roll up rows to be displayed: 2, 3, or 4.

#### int getRows ( )

This method returns the text’s vertical position for CEA 608 closed captions only.

CEA 608 closed captions are positioned vertically based on this value. There are 15 possible rows in which the
captions can be displayed, 1 being at the top of the screen and 15 at the bottom.

**Returns**

 
The vertical position at which to display the caption. This will be an integer value from 1 to 15.
 
#### int getScrollDirection ( )

This property specifies the direction of the text entering or exiting the rectangle text box.

**Returns**

 
The direction of the text. This will be one of the following values:
 
- Bottom to top (0)
- Right to left (1)
- Top to bottom (2)
- Left to right (3)

#### boolean getScrollIn ( )

This property specifies the text entering from outside the rectangle box.

**Returns**

 
TRUE if ON , FALSE if OFF.
 
#### boolean getScrollOut ( )

This property specifies the text exiting from inside the rectangle box.

**Returns**

 
TRUE if ON , FALSE if OFF.
 
#### int getSizeForWebVTT ( )

This method gets the size data of a WebVTT cue.

**Returns**

 
A byte array with the cue size data for the content’s WebVTT.
 
#### int getSnapToLineForWebVTT ( )

This method gets the snap-to-line data of a WebVTT cue.

**Returns**

 
A byte array with the snap-to-line data for the content’s WebVTT.
 
 
#### int getStartTimeStampForWebVTT ( )

This method gets the starting timestamp for WebVTT text cue captions.

**Returns**

 
The starting timestamp of the WebVTT text cue as an integer.
 
 
#### String getString ( )

This method returns the String data for CEA 608 closed captions in content.

This method allows CEA 608 closed captions to be implemented in a caption renderer other than the NexCaptionRenderer provided by the NexPlayer SDK.

If this method returns null, do not use it. Otherwise, use the string to implement and display CEA 608 closed captions with your specific renderer.

**Returns**

 
A String of CEA 608 closed caption data. If this method returns null, no caption data was received and no captions should be displayed.
 
 
#### TTML\_TextAligngetTextAlignforTTML ( )

This method gets the horizontal text alignment of timed text (TTML) in content.

It corresponds to the tts:textAlignattribute, and indicates how timed text should be aligned horizontally in
the display region when displayed.

**Returns**

 
The horizontal text alignment as a TTML\_TextAlign object, which will be one of:
 
- Default (0)
- Start (1)
- Left (2)
- Center (3)
- Right (4)
- End (5)

**See Also**


TTML\_TextAlign for more information.
 
#### TextBlink[ ] getTextBlink ( )

This property gets the array of the current TextBlink class.

**Returns**

 
The array of the current TextBlink class.
 
#### Rect getTextBox ( )

This property gets the rectangle box for text drawing.

**Returns**

 
The rectangle box.
 
#### int [ ] getTextboxCoordinatesFor3GPPTT ( )

This property gets the coordination of the rectangle text box.

**Returns**

 
The coordination of the rectangle text box.
 
#### byte [ ] getTextData ( )

This method gets the text data of local subtitle files in content.

> **Warning** This method can only be used for standard subtitle files including SMI, SRT, SUB, and Smooth Streaming subtitles. It may NOT be used to determine the text of CEA 608 closed captions or CFF and 3GPP timed text.
 
The byte array of text data returned here can be used to display the content’s subtitles as desired.

The caption text of CEA 608 closed captions can be received by calling NexClosedCaption.getString and text for 3GPP Timed Text is received by calling getTextDataFor3GPPTT. Text for CFF timed text is received by calling getTextDataForTTML.

**Returns**

 
A byte array of the subtitle text data for the current content.
 
#### byte [ ] getTextDataFor3GPPTT ( )

This property gets data of the text.

**Returns**

 
Data of the text.
 
#### byte [ ] getTextDataforTTML ( )

This method is used to handle the text data for timed text (TTML) in content.

**Returns**

 
A byte array with the text data for the content’s timed text (TTML).
 
 
#### byte [ ] getTextDataForWebVTT ( )

This method gets the text data for a WebVTT cue.

**Returns**

 
A byte array with the text data for the content’s WebVTT.
 
 
#### TextHighlightgetTextHighlight ( )

This property gets the current TextHighlight class.

**Returns**

 
The current TextHighlight class.

#### TextHighlightColorgetTextHighlightColor ( )

This property gets the current TextHighlightColor class.

**Returns**

 
The current TextHighlightColor class.
 
#### TextHyperTextgetTextHyperText ( )

This property gets the current TextHyperText class.

**Returns**

 
The current TextHyperText class.
 
#### TextKaraokegetTextKaraoke ( )

This property gets the current TextKaraoke class.

**Returns**

 
The current TextKaraoke class.
 
#### TTML\_TextOutlineStyleLengthgetTextOutline ( )

This method gets the text outline style to be used to display timed text (TTML) in text outline.

It corresponds to thetts:textOutlineattribute and is returned as a TTML\_TextOutlineStyleLength object
including the color, outline thickness, and blur radius if present.

**Returns**

 
A TTML\_TextOutlineStyleLength object with the relevant information to display timed text (TTML) in outline form.
 
**See Also**

 
TTML\_TextOutlineStyleLength for more information.
 
 
#### int getTextPositionForWebVTT ( )

This method gets the position data of a WebVTT cue.

**Returns**

 
A byte array with the position data for the content’s WebVTT.
 
#### TextScrollDelaygetTextScrollDelay ( )

This property gets the current TextScrollDelay class.

**Returns**

 
The current TextScrollDelay class.
 
#### String getTextStringForWebVTT ( )

This method gets the full text of a caption from WebVTT text tracks as a string.

**Returns**

 
The WebVTT cue text as a string.
 
 
#### List < byte[ ] > getTextStrListForWebVTT ( )

This method gets a list of the text strings in WebVTT text cues content.

**Returns**

 
A list of byte arrays containing the strings of WebVTT cue text.
 
 
> **Deprecated** Do not use.

#### TextStylegetTextStyle ( )

This property gets the current TextStyle class.

**Returns**

 
The current TextStyle class.
 
#### int getTextType ( )

This method determines the type of text captions used by the content.

Most subtitles will be displayed without further processing but CEA 608 closed captions can include additional text
attributes.

**Returns**

 
The type of text to be displayed. This will be one of:
 
- TEXT\_TYPE\_UNKNOWN The type of text is unknown. The text is treated like a general text file.
- TEXT\_TYPE\_GENERAL This is text only and requires no additional processing.
- TEXT\_TYPE\_ATSCMH\_CC Not a format currently supported.
- TEXT\_TYPE\_ATSCMH\_BAR The text includes text bar data. Not currently supported.
- TEXT\_TYPE\_ATSCMH\_AFD The text includes Active Format Description data. Not currently supported.
- TEXT\_TYPE\_NTSC\_CC\_CH1 The text is CEA 608 closed captions on Data Channel 1.
- TEXT\_TYPE\_NTSC\_CC\_CH2 The text is CEA 608 closed captions on Data Channel 2.

#### TextWrapgetTextWrap ( )

This property gets the current TextWrap class.

**Returns**

 
The current TextWrap class.
 
#### int [ ] getTTMLTimeData2Array ( )

This method gets the time information of the timed text (TTML) in the content.

**Returns**

 
An int array with the time information of the timed text. The first index of the array is the start time to draw the timed text, the second is the final time to draw the timed text, and the third is the clear time.
 
 
#### TTML\_UnicodeBIDIgetUnicodeBIDIforTTML ( )

This method gets the directionality of timed text (TTML) in content.

It corresponds to thetts:unicodeBidiattribute, and either defines and override of the Unicode directionality or a directional embedding.

**Returns**

 
The directionality of timed text (TTML) as a TTML\_UnicodeBIDI. This will be one of:
 
- Default (0)
- Normal (1)
- Embed (2)
- BidiOverride (3)

See Also

 
TTML\_UnicodeBIDI for more information.
 

#### int getVerticalJustification ( )

This property justify the alignment of the text vertically, which are top, centre and bottom.

**Returns**

 
The alignment of the text. This will be one of the following values:
 
- Top (0)
- Centre (1)
- Bottom (-1)

#### int [ ] getViewportAnchorForWebVTT ( )

This method gets the viewport anchor data of a WebVTT region.

**Returns**

 
A byte array with the viewport anchor data for the content’s WebVTT.
 
 
> **Deprecated** Do not use.

#### int getWidthForWebVTT ( )

This method gets the width data of a WebVTT region.

Returns

 
A byte array with the width data for the content’s WebVTT.
 
 
> **Deprecated** Do not use.

#### TTML\_WritingModegetWritingModeforTTML ( )

This method gets the writing mode of timed text (TTML) in content.

It corresponds to thetts:writingModeattribute and indicates how timed text (TTML) should be displayed in
the text display region.

**Returns**

 
The writing mode of timed text (TTML) as a TTML\_WritingMode object. This will be one of:
 
- Default (0)
- Left-to-Right, Top-to-Bottom (1)
- Right-to-Left, Top-to-Bottom (2)
- Top-to-Bottom, Right-to-Left (3)


### NexClosedCaption Class Reference 262

- Top-to-Bottom, Left-to-Right (4)
- Left-to-Right (5)
- Right-to-Left (6)
- Top-to-Bottom (7)

**See Also**

 
TTML\_WritingMode for more information.
 
 
#### boolean getWritingVertically ( )

This property vertical position the text will be written in.

**Returns**
 
TRUE if YES , FALSE if No.
 
#### int getzIndexforTTML ( )

This method gets the zIndex for timed text (TTML) in content.

It corresponds to the tts:zIndexattribute, and defines the front-to-back order of timed text (TTML) region areas if they overlap. For example, if several blocks of timed text (TTML) were to be staggered, layered, and displayed at once, the block with the zIndex of 2 would be in front (like the top sheet of paper in a pile), the block with zIndex of 1 would be next, and the block with zIndex of 0 would be under the others (like the bottom sheet of paper in pile).

**Returns**

 
The zIndex of the timed text (TTML) as an int.
 
 
#### boolean isBoldforTTML ( )

This method determines whether or not timed text (TTML) in content should be displayed in bold.

It corresponds to the tts:fontWeightattribute.

**Returns**


TRUE if the timed text (TTML) should be displayed in bold or FALSE if it should be displayed normally.
 

#### boolean isDisplayAutoforTTML ( )

This method determines whether timed text (TTML) in content is displayed automatically or not.

It corresponds to the tts:displayattribute, and allows certain text to be displayed in timed intervals while other text remains on the screen.

**Returns**

 
TRUE if timed text (TTML) is labeled auto, or FALSE if it is labeled none.
 
 
#### boolean isDrawBackground (int row, int col)

This determines if the background of the character in CEA 608 closed captions is to be displayed or not (FULL mode).

If the background is not to be displayed, it will be transparent and the background color value of the caption will be ignored.

**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.|
|col| The column or horizontal position of the character to be displayed.|
 
**Returns**

 
TRUE if background color is to be displayed, FALSE if not.
 
#### int isEnable ( )

This method controls whether CEA 608 closed captions are enabled or disabled.

**Returns**

Always 0.
 
> **Deprecated** Do not use.

#### boolean isFlashing (int row, int col)

This determines if the character in CEA 608 closed captions is to be displayed flashing (FULL mode).

**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.|
|col| The column or horizontal position of the character to be displayed.|

**Returns**

 
TRUE if flashing, FALSE if not.
 
#### boolean isItalic (int row, int col)

This determines if the character in CEA 608 closed captions is to be displayed in italics.

(FULL mode)

**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.|
|col| The column or horizontal position of the character to be displayed.|
 
**Returns**

 
`TRUE` if italicized, `FALSE` if not.
 
#### int isItalic ( )

This method determines CEA 608 closed captions italics.

**Returns**

 
Zero if the text is displayed normally; 1 if the text should be displayed initalics.
 
Deprecated Do not use.

#### boolean isLarge (int row, int col)

This determines if the character in CEA 608 closed captions is to be displayed in BOLD (FULL mode).

**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.|
|col| The column or horizontal position of the character to be displayed.|
 
**Returns**

TRUE if bold , FALSE if not.
 
#### int isOpaque ( )

This method determines the opacity of CEA 608 closed captions background color.

**Returns**

Always 1 (opaque) for CEA 608 closed captions.
 
> **Deprecated** Do not use.

#### boolean isOverflowVisibleforTTML ( )

This method determines whether or not timed text (TTML) in content that overflows the displayed block should be visible or not.

It corresponds to the tts:overflowattribute, and determines whether timed text that overflows the display region will be visible or not.

**Returns**

 
TRUE if overflowing timed text (TTML) should be visible, FALSE if the overflow should be hidden.
 
 
#### boolean isShowBackgroundforTTML ( )

This method determines when the background of timed text (TTML) in content should be visible.

It corresponds to the tts:showBackgroundattribute, indicates whether the background should always be
visible or should be visible only when there is timed text displayed.

**Returns**


TRUE if the background should always be visible, or FALSE when background should only be visible when text is displayed.

#### boolean isTextDecorationforTTML ( )

This method determines if any text decoration should be displayed in timed text (TTML) in content.

It corresponds to the tts:textDecorationattribute, and allows text features like underline, overline,
 and lineThrough to be displayed in timed text (TTML).

**Returns**

TRUE if text should be underlined, FALSE if there is no text decoration. 
 
#### boolean isUnderline (int row, int col)

This determines if the character in CEA 608 closed captions is to be underlined when displayed (FULL mode).

**Parameters**

| Name    | Description                |
|---------|--------|
|row| The row or vertical position of the character to be displayed.| 
|col| The column or horizontal position of the character to be displayed.|
 
**Returns**


`TRUE` if underlined, `FALSE` if not.
 
#### int isUnderline ( )

This method determines whether CEA 608 closed captions are underlined.

**Returns**

Zero if the text is displayed normally; 1 if the text should be underlined.
 
> **Deprecated** Do not use.

#### boolean isVisibilityforTTML ( )

This method determines whether or not timed text (TTML) in content should be displayed (visible) or hidden.

It corresponds to the tts:visibility attribute, and allows timed text to be displayed and hidden at different intervals as desired.

**Returns**

TRUE when text should be visible, FALSE when it should be hidden.
 
#### boolean isWrapforTTML ( )

This method determines whether timed text (TTML) in content should wrap automatically to the following line or not.

It corresponds to the tts:wrapOptionattribute and determines whether line wrapping will happen automatically when timed text (TTML) reaches the end of the display region, or if the text will only wrap to the next line on included line breaks.

**Returns**

 
`TRUE` if timed text (TTML) should wrap automatically within a displayed region, or `FALSE` if it should only wrap on included line breaks.
 
#### boolean isWriteLefttoRightforTTML ( )

This method determines the direction of timed text (TTML) in content.

It corresponds to the tts:directionattribute, which indicates whether timed text should be displayed from left-to-right or from right-to-left.

**Returns**
 
`TRUE` if text is to be displayed left-to-right like standard Latin script, or `FALSE` if it should be displayed right-to-left.
 
#### void setHtmlDataForWebVTT (byte[ ] textData, int byteLen)

This method sets a String with the full HTML data about a WebVTT text track cue.

**Parameters**

| Name    | Description                |
|---------|--------|
 
|textData| A byte array with the full HTML data about the WebVTT cue.|
|byteLen| The length of the HTML data in the parameter,textData.|

> **Deprecated** Do not use.

#### void setTextForWebVTT (byte[ ] textData, int byteLen)

This method sets the text data of WebVTT text tracks in content.

**Parameters**

| Name    | Description                |
|---------|--------|
|textData| A byte array with the text data of the WebVTT text cue to be set.|
|byteLen| The length of the WebVTT text data in the parameter,textData.|

> **Deprecated** Do not use.


#### final int ENCODING\_TYPE\_ASCII = 0x10 [static]

This is a possiblereturnvalue for NexClosedCaption.getEncodingType().

#### final int ENCODING\_TYPE\_EUC\_KR = 0x21 [static]

This is a possiblereturnvalue for NexClosedCaption.getEncodingType().

#### final int ENCODING\_TYPE\_ISO8859\_1 = 0x0 [static]

This is a possiblereturnvalue for NexClosedCaption.getEncodingType().

#### final int ENCODING\_TYPE\_UNICODE = 0x20 [static]

This is a possiblereturnvalue for NexClosedCaption.getEncodingType().

#### final int ENCODING\_TYPE\_UNKNOWN = 0xFFFFFFFF [static]

This is a possiblereturnvalue for NexClosedCaption.getEncodingType().

#### final int ENCODING\_TYPE\_UTF16 = 0x1 [static]

This is a possiblereturnvalue for NexClosedCaption.getEncodingType().

#### final int ENCODING\_TYPE\_UTF16\_BE = 0x2 [static]

This is a possiblereturnvalue for NexClosedCaption.getEncodingType().

#### final int ENCODING\_TYPE\_UTF8 = 0x3 [static]

This is a possiblereturnvalue for NexClosedCaption.getEncodingType().

#### byte [ ] mCEA708Data

This is an array containing the CEA 708 closed caption data for the given content.

**See Also**
 
- NexEIA708Struct
- NexEIA708CaptionView
 
#### int mCEA708Len

This is the size of the mCEA708Dataarray containing the text data for CEA 708 closed captions within content.

 
#### int mCEA708ServiceNO

This is the service number of the CEA 708 closed captions to be used to display captions for the given content.

Different service numbers contain different closed caption data for the same content, for example captions of different languages.
 
#### final int ROLLED\_OUT\_ROW = -1 [static]

In FULL mode, when CEA 608 closed captions are to be displayed and "rolled up" with animation, this defines the row that is being "rolled out" of the display during the animation, in other words the row that is disappearing as the next, new row of captions appears.

This can be ignored if animation of the display is not being used.

#### final int TEXT\_TYPE\_3GPP\_TIMEDTEXT = 0x20 [static]

This is a possible return value for NexClosedCaption.getTextType().

It indicates the contents include 3GPP timed text.

#### final int TEXT\_TYPE\_ATSCMH\_AFD = 0x13 [static]

This is a possible return value for NexClosedCaption.getTextType().

This format is not currently supported.

#### final int TEXT\_TYPE\_ATSCMH\_BAR = 0x12 [static]

This is a possible return value for NexClosedCaption.getTextType().

This format is not currently supported.

#### final int TEXT\_TYPE\_ATSCMH\_CC = 0x11 [static]

This is a possible return value for NexClosedCaption.getTextType().

This format is not currently supported.

#### final int TEXT\_TYPE\_EXTERNAL\_TTML = 5 [static]

This is a possible return value for NexClosedCaption.getTextType().

This indicates that the text type is external TTML (∗.dfxp, or the Distribution Format Exchange Profile).

#### final int TEXT\_TYPE\_GENERAL = 1 [static]

This is a possible return value for NexClosedCaption.getTextType().

This indicates general text type and requires no special processing of the text.

#### final int TEXT\_TYPE\_NTSC\_CC\_CH1 = 0x14 [static]

This is a possible return value for NexClosedCaption.getTextType().

It indicates the contents include CEA 608 closed captions on Data Channel 1 and processes the attributes accordingly.

#### final int TEXT\_TYPE\_NTSC\_CC\_CH2 = 0x15 [static]

This is a possible return value for NexClosedCaption.getTextType().

It indicates the contents include CEA 608 closed captions on Data Channel 2 and processes the attributes accordingly.

#### final int TEXT\_TYPE\_SMI = 0x40 [static]

This is a possible return value for NexClosedCaption.getTextType().

#### final int TEXT\_TYPE\_SRT = 0x41 [static]

This is a possible return value for NexClosedCaption.getTextType().

#### final int TEXT\_TYPE\_SUB = 0x42 [static]

This is a possible return value for NexClosedCaption.getTextType().

#### final int TEXT\_TYPE\_TTML\_TIMEDTEXT = 0x25 [static]

This is a possible return value for NexClosedCaption.getTextType().

It indicates the contents include CFF timed text (TTML).

#### final int TEXT\_TYPE\_UNKNOWN = 0 [static]

This is a possible return value for NexClosedCaption.getTextType().

When the text type is unknown, NexPlayer™ doesn’t perform any special processing on the text (the same as in the case of general subtitles.)

#### final int TEXT\_TYPE\_WEBVTT = 0x30 [static]

This is a possible return value for NexClosedCaption.getTextType().

It indicates the contents include WebVTT text tracks.

### NexContentInformation Class Reference

Stores and provides information about an individual codec used by the NexPlayer™ engine.

#### NexCodecInformation(String strCodecVersion, int iMediaType, int iCodecClass,int iCodecID,int iCpuInfo)

The sole initializer for this class.

The arguments match the names of the relevant member variables, and are simply assigned on a 1-to-1 basis.

**Parameters**

| Name    | Description                |
|---------|--------|
|strCodecVersion | Initializes mCodecVersion.|
|iMediaType| Initializes mMediaType.|
|iCodecClass| Initializes mCodecClass.|
|iCodecID| Initializes mCodecID.|
|iCpuInfo| Initializes mCpuInfo.|
 
#### int mCodecClass

The classification of the codec.

Possible Values:

- 0 : SW codec
- 1 : HW codec

#### int mCodecID

This can be one of the following video codec constants:

- NEXOTI\_MPEG4V
- NEXOTI\_H263
- NEXOTI\_H264
- NEXOTI\_WMV
- NEXOTI\_RV

This can be one of the following audio codec constants:

- NEXOTI\_AAC
- NEXOTI\_AAC\_GENERIC
- NEXOTI\_AAC\_PLUS
- NEXOTI\_MPEG2AAC
- NEXOTI\_MP3inMP4
- NEXOTI\_MP2
- NEXOTI\_MP3
- NEXOTI\_BSAC
- NEXOTI\_WMA
- NEXOTI\_RA
- NEXOTI\_AC3
- NEXOTI\_EC3
- NEXOTI\_AC4
- NEXOTI\_DRA Or (in future versions) one of the following speech codec constants:
- NEXOTI\_AMR
- NEXOTI\_EVRC
- NEXOTI\_QCELP
- NEXOTI\_QCELP\_ALT
- NEXOTI\_SMV
- NEXOTI\_AMRWB
- NEXOTI\_G711
- NEXOTI\_G723

#### String mCodecVersion

The codec version as a string.

E.g., "1.0" or "1.0.0"


#### int mCpuInfo

The CPU architecture information.

This is one of:

- NEX\_SUPPORT\_CPU\_ARMV5 
- NEX\_SUPPORT\_CPU\_ARMV6
- NEX\_SUPPORT\_CPU\_ARMV7

#### int mMediaType

The type of media.

Possible Values:

- 1 : Audio codec
- 2 : Video codec

### NexContentInformation Class Reference

Provides information on content.

This is returned by NexPlayer.getContentInfo. See that method for details.

#### static String getMediaCodecMimeType (int mediaType, int codecType) [static] , [protected]

This method converts codec information to mime type.

**Returns**
 
Returns mime type of the given codec type
 
#### final int H264\_BASELINE\_PROFILE = 66 [static]

Possible H.264 profile value for mVideoProfile.

#### final int H264\_HIGH\_PROFILE = 100 [static]

Possible H.264 profile value for mVideoProfile.

#### final int H264\_MAIN\_PROFILE = 77 [static]

Possible H.264 profile value for mVideoProfile.

#### NexStreamInformation[ ] mArrStreamInformation

This is an array describing the streams that are available for the current content.

Streams have semantically different content (for example, presented in different languages or presented from different camera angles) and are generally intended to be selected via the user interface.

For each stream, there can be multiple tracks. Generally, tracks contain content that is equivalent but presented with different trade-offs between quality and bandwidth. While streams are selected by the user, tracks are usually selected automatically based on available bandwidth and system capabilities, in order to provide the best experience to the user.

For formats that do not support multiple streams or multiple tracks, these arrays may be empty or may contain only a single element.

#### int mAudioBitRate

Audio bitrate, in bits per second.

#### int mAudioCodec

Audio codec used by the currently open media.

This can be one of the following audio codec constants:

- NEXOTI\_AAC
- NEXOTI\_AAC\_GENERIC
- NEXOTI\_AAC\_PLUS
- NEXOTI\_MPEG2AAC
- NEXOTI\_MP3inMP4
- NEXOTI\_MP2
- NEXOTI\_MP3
- NEXOTI\_BSAC
- NEXOTI\_WMA
- NEXOTI\_RA
- NEXOTI\_AC3
- NEXOTI\_EC3
- NEXOTI\_DRA
- NEXOTI\_DTS

Or (in future versions) one of the following speech codec constants:

- NEXOTI\_AMR
- NEXOTI\_EVRC
- NEXOTI\_QCELP
- NEXOTI\_QCELP\_ALT
- NEXOTI\_SMV
- NEXOTI\_AMRWB
- NEXOTI\_G711
- NEXOTI\_G723
- 
#### int mAudioCodecClass

Classification of audio codec.

Possible Values:

- 0 : SW codec
- 1 : HW codec

#### int mAudioFourCC

Additional information about the audio codec in use, namely the FOURCC (or "four character code") of the codec.

When the audio codec of the current content is DTS, this will be one of the following values:

- 0x64747363 : DTSC
- 0x64747363 : DTSH
- 0x64747363 : DTSL
- 0x64747363 : DTSE
 
> **Warning** This information is not supported by current API version.
 
#### int mAudioNumOfChannel

Number of audio channels.

#### int mAudioSamplingRate

Audio sampling rate in samples per second.

#### String [ ] mCaptionLanguages

A list of the caption languages available for the current content (for example, from a subtitle file).

The format of this depends on the caption file. This may be the language name spelled out, or it may be a language identifier such as EN for English or KR for Korean.

For SMI files, this is the class name of a given subtitle track, as specified in the SMI file.

There is currently no way to access the additional data associated with a subtitle track, but it is possible to guess the language (and therefore the encoding) indirectly from the track’s class name.

Although the class name is arbitrary, many files follow the convention "LLCCTT" where LL is the language (EN for English, KR for Korean and so on), CC is the country (and may be omitted) and TT is the type (for example "CC" for closed captions).

For example, "ENUSCC" would be EN(English), US(United States), CC(Closed Captions). "KRCC" would be KR(Korean), CC(Closed Captions).

Currently, the safest way is to check only the first two letters of the class name to find the language, and assume the most common encoding for that language.

#### int mCaptionType

The type of captions available in the current content.

This value will be set afterNexPlayer.openis called and will be one of:

- NEX\_TEXT\_UNKNOWN = 0x00000000: Unknown caption format.
- NEX\_TEXT\_EXTERNAL\_SMI = 0x00000002: SMI subtitles.
- NEX\_TEXT\_EXTERNAL\_SRT = 0x00000003: SRT subtitles.
- NEX\_TEXT\_3GPP\_TIMEDTEXT = 0x####: 3GPP timed text.
- NEX\_TEXT\_WEBVTT = 0x####: WebVTT text tracks.
- NEX\_TEXT\_TTML = 0x####: TTML timed text.

In the current version, only the types listed above will be recognized and if captions in another format exist, this will be set to NEX\_TEXT\_UNKNOWN.

Furthermore, if an external subtitle file is included in addition to another format, this member will be set to the external subtitle type (SMI or SRT).

Since CEA 608 and CEA 708 closed captions cannot be identified until decoding begins, mCaptionType will also be set to NEX\_TEXT\_UNKNOWN when they are included in content.
 
#### int mCurrAudioStreamID

ID of currently selected audio stream, for content types with multiple streams.

This matches the ID member of an entry in the NexContentInformation.mArrStreamInformation() array.

#### int mCurrTextStreamID

ID of currently selected text stream, for content types with multiple streams.

This matches the ID member of an entry in the NexContentInformation.mArrStreamInformation() array.

#### int mCurrVideoStreamID

ID of currently selected video stream, for content types with multiple streams.

This matches the ID member of an entry in the NexContentInformation.mArrStreamInformation() array.

#### NexID3TagInformationmID3Tag

The picture associated with the current content, for formats such as MP3 and AAC that can have an optional associated still image.

This is generally used in place of video for content that does not have video. The exact use of the still image is up to the content producer. In the case of an MP3 or AAC audio file, it is usually the album cover artwork. In the case of HTTP Live Streaming, audio-only tracks often have a still image to be shown in place of the video.

#### int mIsPausable

If the media supports pausing, this is 1; otherwise it is 0.

#### int mIsSeekable

Whether or not it is possible for the player to seek in the current content.

Depending on the kind of content playing, seeking may or may not be possible throughout the content or the prefetch
buffer that contains content data that has already been received but not yet played.

The possible seek modes in content are indicated by an integer from 0 to 7, and are described as follows:

1. NEXPLAYER\_SEEKABLE\_NONE: Seeking is not available in the current content.
2. NEXPLAYER\_SEEKABLE\_IN\_CONTENT: Seeking is possible within the current content.
3. NEXPLAYER\_SEEKABLE\_IN\_BUFFER: Seeking is possible within the prefetch buffer.
4. NEXPLAYER\_SEEKABLE\_IN\_CONTENT | NEXPLAYER\_SEEKABLE\_IN\_BUFFER: Seeking is possible
    within the current content or the prefetch buffer.
5. NEXPLAYER\_SEEKABLE\_TO\_ZERO: Can only seek to 0 seconds. (The only I-frame within the current
    content is at 0 seconds.)
6. NEXPLAYER\_SEEKABLE\_IN\_CONTENT | NEXPLAYER\_SEEKABLE\_TO\_ZERO: Seeking is possible
    within the current content or to 0 seconds.
7. NEXPLAYER\_SEEKABLE\_IN\_BUFFER | NEXPLAYER\_SEEKABLE\_TO\_ZERO: Seeking is possible
    within the prefetch buffer or to 0 seconds.
8. NEXPLAYER\_SEEKABLE\_IN\_CONTENT | NEXPLAYER\_SEEKABLE\_IN\_BUFFER | NEXPLAYER\_SE-
    EKABLE\_TO\_ZERO: Seeking is possible within the current content, the prefetch buffer, and to 0 seconds.

 
#### int mMediaDuration

Length of open media in milliseconds.

If the value is -1, the media is live content.

#### int mMediaType

Type of media that has been opened.

Possible Values:

- 1 : Audio Only
- 2 : Video Only
- 3 : AV

#### int mRotationDegree

Additional information about the rotation degree of video content being played.

This value will be one of the following:

- 0
- 90
- 180
- 270

#### int mStreamNum

The number of streams (audio and video) available for the current content.

This is the same as the length of the NexContentInformation.mArrStreamInformation() array. For formats that don’t support multiple streams, this may be zero, or it may describe a single default stream.

#### int mSubSrcType

Additional information about the type of content being played.

Possible values ofmSubSrcTypeinclude:

- 0 : type none : When the type of content is unknown.
- 1 : 3GPP RTSP
- 2 : Real Media Type
- 3 : MS RTSP
- 4 : Window Media Streaming
- 5 : HTTP Live Streaming
- 6 : Smooth Streaming
- 7 : MPEG DASH
- 8 : Progressive Download
- 9 : Remote File Cache
- 10 : Rich Communication Service
- 11 : Local
 
#### int mVideoCodec

Video codec used by the currently open media.

This is one of:

- NEXOTI\_MPEG4V
- NEXOTI\_H263
- NEXOTI\_H264
- NEXOTI\_WMV
- NEXOTI\_RV

#### int mVideoCodecClass

Classification of video codec.

Possible Values:

- 0 : SW codec
- 1 : HW codec

#### int mVideoCodecError

Error information about video codec.

This is one of:

- NexErrorCode.NONE
- NexErrorCode.NOT\_SUPPORT\_VIDEO\_CODEC
- NexErrorCode.NOT\_SUPPORT\_VIDEO\_RESOLUTION
- NexErrorCode.SYSTEM\_FAIL
- NexErrorCode.NOT\_SUPPORT\_DEVICE

#### int mVideoFrameRate

Frame rate of the video, in frames per second.

This is the frame rate specified in the content.

If the device isn’t powerful enough to decode and display the video stream in real-time, the actual number of displayed frames may be lower than this value.

For the actual number of displayed frames, call getContentInfoInt with the value

CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_AVE\_DSP.

#### int mVideoLevel

Video codec level used by the currently open media.

Currently, only H.264 is supported.

#### int mVideoProfile

Video codec profile used by the currently open media.

Currently, only H.264 profiles are supported.

This is one of:

- H264\_BASELINE\_PROFILE
- H264\_MAIN\_PROFILE
- H264\_HIGH\_PROFILE


#### final int NEX\_TEXT\_3GPP\_TIMEDTEXT = 0x#### [static]

Possible caption type for subtitles for mCaptionType, when content includes timed text.

#### final int NEX\_TEXT\_CEA = 0x#### [static]

Possible caption type for subtitles for mCaptionType, content can include CEA-608 or CEA-708.

#### final int NEX\_TEXT\_CEA608 = 0x#### [static]

Possible caption type for subtitles for mCaptionType, when content includes CEA-608.

#### final int NEX\_TEXT\_CEA708 = 0x#### [static]

Possible caption type for subtitles for mCaptionType, when content includes CEA-708.

#### final int NEX\_TEXT\_EXTERNAL\_SMI = 0x00000002 [static]

Possible caption type for subtitles for mCaptionType, when content includes SMI subtitles.

#### final int NEX\_TEXT\_EXTERNAL\_SRT = 0x00000003 [static]

Possible caption type for subtitles for mCaptionType, when content includes SRT subtitles.

#### final int NEX\_TEXT\_EXTERNAL\_SUB = 0x00000004 [static]

Possible caption type for subtitles for mCaptionType, when content includes SUB subtitles.

#### final int NEX\_TEXT\_TTML = 0x#### [static]

Possible caption type for subtitles for mCaptionType, when content includes TTML timed text.

#### final int NEX\_TEXT\_UNKNOWN = 0x00000000 [static]

Possible caption type for subtitles for mCaptionType, when content includes subtitles in an unrecognized format.

#### final int NEX\_TEXT\_WEBVTT = 0x#### [static]

Possible caption type for subtitles for mCaptionType, when content includes WebVTT text tracks.

#### final int NEXOTI\_AAC = 0x00000040 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_AAC\_GENERIC = 0x00000041 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_AAC\_PLUS = 0x00000041 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_AC3 = 0x00002000 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_AC4 = 0x00002002 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_AMR = 0x000000D0 [static]

Possible speech codec value for mAudioCodec.

This is not supported in the current version; do not use it.

Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_AMRWB = 0x000000D4 [static]

Possible speech codec value for mAudioCodec.

This is not supported in the current version; do not use it.

Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_BSAC = 0x00000016 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_DRA = 0x000000E0 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_DTS = 0x40000003 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_EC3 = 0x00002001 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_EVRC = 0x000000D1 [static]

Possible speech codec value for mAudioCodec.

This is not supported in the current version; do not use it.

Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_G711 = 0x000000DF [static]

Possible speech codec value for mAudioCodec.

This is not supported in the current version; do not use it.

> Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_G723 = 0x000000DE [static]

Possible speech codec value for mAudioCodec.

This is not supported in the current version; do not use it.

> Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_H263 = 0x000000C0 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_H264 = 0x000000C1 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_HEVC = 0x10010400 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_MP2 = 0x00000021 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_MP3 = 0x0000016B [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_MP3inMP4 = 0x0000006B [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_MP43 = 0x3334####d [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_MPEG1 = 0x000000F2 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_MPEG2 = 0x000000F3 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_MPEG2AAC = 0x00000067 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_MPEG4Sv1 = 0x00000001 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_MPEG4Sv2 = 0x00000002 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_MPEG4V = 0x00000020 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_QCELP = 0x000000D2 [static]

Possible speech codec value for mAudioCodec.

This is not supported in the current version; do not use it.

Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_QCELP\_ALT = 0x000000E1 [static]

Possible speech codec value for mAudioCodec.

This is not supported in the current version; do not use it.

> Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_RA = 0x000000DA [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_RV = 0x000000DB [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_S263 = 0x000000C2 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_SMV = 0x000000D3 [static]

Possible speech codec value for mAudioCodec.

This is not supported in the current version; do not use it.

> Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_TEXT\_3GPP = 0x000000E0 [static]

Possible text codec for subtitles.

This is not supported in the current version; do not use it.

> Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_TEXT\_SKT = 0x000000E2 [static]

Possible text codec for subtitles.

This is not supported in the current version; do not use it.

> Deprecated Not supported in the current version; do not use.

#### final int NEXOTI\_WMA = 0x####D41 [static]

Possible audio codec value for mAudioCodec.

#### final int NEXOTI\_WMV = 0x####D56 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_WMV1 = 0x31####d57 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_WMV2 = 0x32####d57 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_WMV3 = 0x33####d57 [static]

Possible video codec value for mVideoCodec.

#### final int NEXOTI\_WVC1 = 0x3143#### [static]

Possible video codec value for mVideoCodec.

#### final int NEXPLAYER\_SEEKABLE\_IN\_BUFFER = 2 [static]

One of the possible values for mIsSeekable in NexContentInformation.mIsSeekable.

This indicates that the player can seek within the prefetch buffer of the current content.

#### final int NEXPLAYER\_SEEKABLE\_IN\_CONTENT = 1 [static]

One of the possible values for mIsSeekable in NexContentInformation.mIsSeekable.

This indicates that the player can seek within the current content.

#### final int NEXPLAYER\_SEEKABLE\_NONE = 0** [static]

One of the possible values for mIsSeekable in NexContentInformation.mIsSeekable.

This indicates that seeking is not available in the current content.

#### final int NEXPLAYER\_SEEKABLE\_TO\_ZERO = 4 [static]

One of the possible values for mIsSeekable in NexContentInformation.mIsSeekable.

This indicates that the player can only seek to 0 seconds in the current content (in other words, the player can seek and return to the beginning of the content).

### NexDateRangeData Class Reference

This class provides information about an individual content track, for formats that use multiple tracks (such as HLS).

**Public Attributes**

- String mID
	
	The unique string used to identify the dataRange.

- String mClass
	
	The defined client that specifies a set of attributes and their associated semantic values.

- String mStartDate
	
	The start date.

- String mEndDate

	The end date.

- String mSCTE35CMD
	
	The SCTE35-CMD data.

- String mSCTE35IN
	
	The SCTE35-IN data.

- String mSCTE35OUT
	
	The SCTE35-OUT data.

- String mFullString
	
	The #EXT-X-DATERANGE tag.

- int mPlanDuration
	
	The plan duration.

- int mDuration
	
	The duration of the dataRange.

- int mEndOnNext
	
	The END-ON-NEXT value.


### NexEIA708CaptionView Class Reference

**Public Member Functions**

- `NexDateRangeData` (String mID, String mClass, String mStartDate, String mEndDate, String mSCTE35CMD, String mSCTE35IN, String mSCTE35OUT, String mFullString, int mPlanDuration, int mDuration, int mEndOnNext)

**Public Attributes**

- String mID
    The unique string used to identify the dataRange.
- String mClass
    The defined client that specifies a set of attributes and their associated semantic values.
- String mStartDate
    The start date.
- String mEndDate
    The end date.
- String mSCTE35CMD
    The SCTE35-CMD data.
- String mSCTE35IN
    The SCTE35-IN data.
- String mSCTE35OUT
    The SCTE35-OUT data.
- String mFullString
    The #EXT-X-DATERANGE tag.
- int mPlanDuration
    The plan duration.
- int mDuration
    The duration of the dataRange.
- int mEndOnNext
    The END-ON-NEXT value.

### NexEIA708CaptionView Class Reference

This class defines a caption view for rendering and displaying CEA 708 closed captions.

All of the information about how CEA 708 closed captions is contained within a `NexEIA708Struct` object, and the
caption view defined here provides an example text renderer which can be used to display the captions.

Whenever new CEA 708 closed caption data is received, it should be handled by calling the `setEIA708CC` method.

For other subtitle formats, including CEA 608 closed captions, please see the `NexClosedCaption`, `NexCaptionRenderer`, and `NexCaptionRendererForTimedText` classes instead.

**Classes**

- `class ComparatorRect`


**See Also**

- `NexEIA708Struct`
- `NexClosedCaption`


#### NexEIA708CaptionView (Context context)

This is the constructor for the CEA 708 closed captions caption view.

**Parameters**

| Name    | Description                |
|---------|--------|
| context | The handle for the player. |

#### NexEIA708CaptionView (Context context,AttributeSet attrs)

This is an alternative constructor for the CEA 708 closed captions caption view.

>**Warning** If the caption view is to be used in Android xml, this constructor must be used.

**Parameters**

| Name    | Description                                     |
|---------|---------|
| context | The handle for the player.                      |
| attrs   | The set of attributes associated with the view. |



#### void changeFontSize (int rate)

This method changes the font size of CEA 708 closed captions.

To double the size of the font, the parameter *rate* should be set to 200. In contrast, to have the size of the font,
rate should be set to 50 (in other words, 50%).

**Parameters**

| Name | Description                                              |
|------|------------------|
| rate | The change in size of the caption font, as a percentage. |

#### void changeOrientation (Boolean isChange)

This method indicates when the orientation of a device has changed; deprecated in the current API version.

**Deprecated** Not supported in current API version; do not use.

**Parameters**

| Name     | Description                                                                                     |
|----------|-----------------|
| isChange | 0 when the device orientation remains unchanged or 1 when the device’s orientation has changed. |

#### void clearCaptionString ( )

This method clears the current caption string in CEA 708 closed captions.

#### void initCaptionStyle ( )

This method initializes the style attributes of CEA 708 closed captions that may be set by a user, including the colors
of the text, background, and caption window as well as the edge style and the font size.

This API does not effect the default caption style attributes of specific streaming content.

#### void resetEdgeEffect ( )

This method resets the edge effects on CEA 708 closed captions.

Possible edge effects include setShadow, setCaptionStroke, setRaise, and setDepressed.


#### void setBGCaptionColor (CaptionColor background,int bgOpacity)

This sets the background color of CEA 708 closed captions.

For a full list of colors , please refer to `NexClosedCaption.CaptionColor`.

**Parameters**

| Name       | Description                                                                    |
|------------|--------------------|
| background | The background color, or *null* to use the color from the original caption data. |
| bgOpacity  | The background opacity, from 0 (transparent) to 255 (fully opaque).            |

#### void setBold (boolean isBold)

This method sets whether or not CEA 708 closed captions should be displayed in **bold** text.

Caption data includes attributes such as **bold** anditalics.

Normally, the caption renderer displays each character in normal, **bold** , or italics based on the attributes included
in the caption data.

However in some cases (such as for users with visual impairment) it may be desirable to force the use of bold text.

By enabling this option, the bold attributes in the caption data are ignored and a bold font is used for all characters.

**Parameters**

| Name   | Description                                                                                       |
|--------|-------------------|
| isBold | Set this to TRUE to force bold text, or FALSE to use the bold attribute in the original captions. |

#### void setCaptionStroke (CaptionColor strokeColor, float strokeWidth)

This method sets the CEA 708 closed caption renderer stroke color and width.

For a full list of colors, please refer to `NexClosedCaption.CaptionColor`. The stroke line width is in pixels. Antialiasing is supported, so fractions of a pixel are allowed.

**Parameters**

| Name        | Description                                                                |
|-------------|----------------|
| strokeColor | The stroke color, or null to use the color from the original caption data. |
| strokeWidth | The stroke width in pixels.                                                |

#### void setCaptionWindowColor (CaptionColor windowColor, int windowOpacity)

This method sets the color and opacity of the CEA 708 closed caption window.

**Parameters**

| Name          | Description                                                         |
|---------------|-----------------------------|
| windowColor   | The color of the caption window to set, as a *CaptionColor* object. |
| windowOpacity | The opacity of the window to set, as an integer.                    |

#### void setDepressed (boolean isDepressed)

This method sets whether or not CEA 708 closed captions should be displayed as if depressed into the content.

To have depressed closed captions be displayed in a user-defined color, see the method *setDepressedWithColor* instead.

**Parameters**

| Name        | Description                                            |
|-------------|----------------|
| isDepressed | TRUE if captions should be depressed, otherwise FALSE. |

**See Also**


- `NexEIA708CaptionView.setDepressedWithColor`

#### void setDepressedWithColor (boolean isDepressed, CaptionColor depColor, int depOpacity)**

This method indicates wheather or not CEA 708 closed captions should be displayed as if "depressed" (in a set font
color).

If CEA 708 closed captions are "depressed", they should be displayed as if they are pressed into the video display
slightly, and the color of the depressed part of the caption text can be set by the user.

**Parameters**

| Name        | Description                                                                                  |
|-------------|----------------------------------|
| isDepressed | TRUE if captions are depressed,FALSE if not.                                                 |
| depColor    | The color of the depressed part set by the user, or null to use the default color.           |
| depOpacity  | The opacity of the depressed part as an integer, from 0 (transparent) to 255 (fully opaque). |

#### void setDisplayArea (int left, int top, int width, int height)

This method sets the area where CEA 708 closed captions will be displayed.

**Parameters**

| Name   | Description                                                                                      |
|--------|------------------|
| left   | The horizontal (X) position of the top left corner of the area where captions will be displayed. |
| top    | The vertical (Y) position of the top left corner of the area where captions will be displayed.   |
| width  | The width of the area where captions will be displayed.                                          |
| height | the height of the area where captions will be displayed.                                         |

#### void setEIA708CC (NexEIA708Struct eia708)

This sets the CEA 708 closed captions for a given content.

Whenever new CEA 708 content data becomes available, this method is called to specify the data to the caption
view.

**Parameters**

| Name   | Description                                                           |
|--------|-------------------------------|
| eia708 | The CEA 708 closed captions to set, as a `NexEIA708Struct` structure. |

**See Also**


- `NexEIA708Struct`

#### void setEmbossBlurRadius (float radius)

This method sets the blur radius of the Emboss Mask filter used when a user sets CEA 708 captions to be ’Raised’
or ’Depressed’ in the UI.

**Parameters**

| Name   | Description                                |
|--------|------------------------|
| radius | The blur radius of the Emboss Mask filter. |

#### void setEmbossSpecular (float specular)

This method sets the specular level of the Emboss Mask filter used when a user sets CEA 708 captions to be
’Raised’ or ’Depressed’ in the UI.

**Parameters**

| Name     | Description                                   |
|----------|---------------------------|
| specular | The specular level of the Emboss Mask filter. |

#### void setFGCaptionColor (CaptionColor foreground, int fgOpacity)

This sets the CEA 708 closed captions foreground (text) color.

For a full list of colors, please refer to `NexClosedCaption.CaptionColor`.

**Parameters**

| Name       | Description                                                                    |
|------------|--------------------|
| foreground | The foreground color, or null to use the color from the original caption data. |
| fgOpacity  | The foreground opacity, from 0 (transparent) to 255 (fully opaque).            |

#### void setFonts (Typeface normType, Typeface boldType, Typeface italicType, Typeface boldItalicType)

This method sets the fonts to be used for CEA 708 closed captions.

Four typefaces may be specified for different combinations of **bold** and italics. The caption renderer will select the
appropriate typeface from among these based on the CEA 708 captions being displayed.

For best results, specify all four typefaces. Any typeface can be set to *null*, in which case the system default
typeface will be used.

**Parameters**

| Name           | Description                                                                 |
|----------------|-----------------|
| normType       | Typeface to be used for captions that are neither bold nor italic.          |
| boldType       | Typeface to be used for bold CEA 708 captions.                              |
| italicType     | Typeface to be used for italic CEA 708 captions.                            |
| boldItalicType | Typeface to be used for CEA 708 captions that are both bold and in italics. |

#### void setRaise (boolean isRaise)

This method sets whether or not CEA 708 closed captions should be displayed as if embossed or "raised".

To have raised closed captions be displayed in a user-defined color, see the method setRaiseWithColor instead.

**Parameters**

| Name    | Description                                                       |
|---------|---------------------------|
| isRaise | TRUE if captions should be embossed or "raised", otherwise FALSE. |

**See Also**

- `NexEIA708CaptionView.setRaiseWithColor`

#### void setRaiseWithColor (boolean isRaise, CaptionColor raisedColor, int raisedOpacity)

This method indicates whether or not CEA 708 closed captions should be displayed as if "raised" (in a set font
color).

If CEA 708 closed captions are "raised", they should be displayed as if they rise from the video display slightly, and
the color of the raised part of the caption text can be set by the user.

**Parameters**

| Name          | Description                                                                               |
|---------------|-------------------------------|
| isRaise       | TRUE if captions are raised,FALSE if not.                                                 |
| raisedColor   | The color of the raised part set by the user, or null to use the default color.           |
| raisedOpacity | The opacity of the raised part as an integer, from 0 (transparent) to 255 (fully opaque). |

#### void setShadow (boolean isShadow)

This method sets whether the CEA 708 closed captions should be displayed with a shadow.

**Parameters**

| Name    | Description                                                                           |
|---------|---------------------------|
| isShadow | Set this to TRUE to force text to be displayed with a shadow, or FALSE for no shadow. |

#### void setShadowWithColor (boolean isShadow, CaptionColor shadowColor, int shadowOpacity)

This method sets whether CEA 708 closed captions should be displayed with a colored shadow.

> **Warning** Note that to set a colored shadow for CEA 608 closed captions, the *NexClosedCaption*::*setShadowWithColor* method should be used instead.


**Parameters**

| Name          | Description                                                                           |
|---------------|---------------------------|
| isRaise       | Set this to TRUE to force text to be displayed with a shadow, or FALSE for no shadow. |
| shadowColor   | The shadow color, or null to use the color from the original caption data.            |
| shadowOpacity | The shadow opacity as an integer, from 0 (transparent) to 255 (fully opaque).         |

#### boolean SetSourceByteStream (int serviceNo, byte[ ] Data, int len)

This method sets the source of the byte stream for CEA 708 closed captions.

Similar to the channels in CEA 608 closed captions, CEA 708 services often provide different closed caption information for the given content, for example captions in different languages.

**Parameters**

| Name      | Description                                                                 |
|-----------|-----------------|
| serviceNO | The CEA 708 service number to use as the source of the caption byte stream. |
| Data      | The CEA 708 closed caption data, as an array of bytes.                      |
| len       | The size of the array of CEA 708 closed caption data, in bytes.             |

**Returns**


Returns 1 if there is update in the CEA 708 closed caption view, otherwise 0.

#### void setTextSize (int px)

This method sets the text size of CEA 708 closed captions.


**Parameters**

| Name | Description                                          |
|------|--------------|
| px   | The font size to set closed caption text, in pixels. |

#### void setValidateUpdate (boolean isvalid)

This method sets whether a CEA 708 closed caption should be updated or not.

In order to update CEA 708 closed captions, it is necessary to call this method and then call *invalidate*.

**Parameters**

| Name    | Description                                                      |
|---------|--------------------------|
| isvalid | Whether or not to update captions:TRUE if valid, otherwiseFALSE. |

### NexEIA708Struct Class Reference


This class defines a structure to handle CEA 708 closed captions in content.

CEA 708 (also known as EIA 708) closed captions should be rendered seperately, using for example an instance of the `NexEIA708CaptionView` class.

Since CEA 708 closed captions include multiple services where different closed caption data is provided for the same content, for example different languages, the method `SetSourceByteStream` can be used to set which service should be used to receive CEA 708 closed caption data.

**See Also**

- `NexEIA708CaptionView`

**Classes**

- `class EIA708Service`
    
    This class defines a CEA 708 service.
- `class EIA708Window`
    
    This class describes the window where CEA 708 closed captions will be displayed.


**Public Attributes**

- `EIA708Service[ ] mService`


#### static final int byte2int (byte[ ] data, int offset, int len) *[static]*

This method handles byte of data in CEA 708 closed captions.

#### static final int ConvARGBColor (byte Opacity, byte Color) *[static]*

This method handles color conversion of CEA 708 closed captions.

#### boolean IsEnableService (int ServiceNo)

This method checks if the CEA 708 service number is enabled.

**Parameters**

| Name      | Description                 |
|-----------|---------|
| ServiceNO | The CEA 708 service number. |

**Returns**


- `TRUE if the CEA 708 service is enabled, otherwise FALSE.`

#### boolean SetSourceByteStream (int serviceNo, byte[ ] Data, int len)

This method sets the source byte stream for CEA 708 closed captions.

Like the different channels in CEA 608 closed captions, each CEA 708 service provides different caption information
for the same content, for example captions in different languages. The option to change the CEA 708 service may
be beneficial to offer to application users.

**Parameters**

| Name      | Description                                                                   |
|-----------|-------------------|
| serviceNO | The CEA 708 service number from which to receive CEA 708 closed caption data. |
| data      | The CEA 708 closed caption data as an array of bytes.                         |
| len       | The size of the CEA 708 closed caption data array.                            |

**Returns**


- `TRUE is successful, otherwise FALSE.`

### NexEmsgData Class Reference

This class contains information about an event message of the emsg box.

#### long mEndTime

The `mEndTime` provides the actual end time of event in the Media Presentation time.

It is expressed in Unix Epoch Time in milliseconds.

#### int mEventDuration

The `mEventDuration` provides the duration of event in media presentation time.

The value 0xFFFF indicates an unknown duration.

#### int mId

The `mId` is a field identifying this instance of the message.

Messages with equivalent semantics shall have the same value,

- i.e. processing of any one event message box with the same id is sufficient.

#### byte [ ] mMessageData

The `mMessageData` is body of the message, which fills the remainder of the message box.

This may be empty depending on the above information. The syntax and semantics of this field must be defined by
the owner of the scheme identified in the `mSchemeIdUri` field.

#### long mPresentationTime

ThemPresentationTime.

- If `mVersion` is 0, provides the Media Presentation time delta of the media presentation time of the event and
    the earliest presentation time in this segment. The timescale is provided in the `mTimescale` field.
- If `mVersion` is 1, provides the Media Presentation time of the event measured on the Movie timeline, in the timescale provided in the `mTimescale` field.

#### String mSchemeIdUri

The `mSchemeIdUri` used identify the message scheme.

The semantics and syntax of the `mMessageData` are defined by the owner of the scheme identified.

For SCTE-35 event, the `mSchemeIdUri` is equal to "urn:scte:scte35:2013:bin", "urn:scte:scte35:2013:xml" and
"urn:scte:scte35:2014:xml+bin".

#### long mStartTime

The `mStartTime` provides the actual start time of event in the Media Presentation time.

It is expressed in Unix Epoch Time in milliseconds.

### NexPlayer.NexErrorCategory Enum Reference

This enum defines the categories for errors.

> **CAUTION:** This is experimental and is subject to change.

Each error code has an associated category. The intent of this is to group errors based on cause so that a friendlier message can be displayed to the user. The exact groupings may change in future versions.

#### API

Something is wrong with what was passed to the API; indicates a bug in the host application.

#### AUTH

Authentication error; not authorized to view this content, or a DRM error while determining authorization.

#### BASE

An error code base value (these shouldn’t be used, so this should be treated as an internal error).

#### CONTENT_ERROR

Something is wrong with the content itself, or it uses a feature we don’t recognize.

#### GENERAL

General errors.

#### INTERNAL

Something went wrong internally; this could be due to API misuse, something wrong with the OS, or a bug.

#### NETWORK

A network error was detected.


#### NOT_SUPPORT

Some feature of the media is not supported.

#### SYSTEM

Errors we can’t control relating to the system (for example, memory allocation errors).

### NexPlayer.NexErrorCode Enum Reference

Possible error codes that `NexPlayer`™ can return.

This is a Java *enum* so each error constant is an object, but you can convert to or from a numerical code using
instance and class methods.

To get the error constant for a given code, call `fromIntegerValue(int)`.

To get the error code given an error constant, call `getIntegerCode()`.

Because this is a Java *enum*, it is very easy to include the name of the error constant in an error message instead
of just the number. For example, the following code logs the errors that are received from the `NexPlayer`™ engine:

```java
void onError( NexPlayer mp, NexErrorCode errorCode )
{
	NexLog.d( "onError",
		"Received the error: "
			+ errorCode.name()
			+ " (0x"
			+ Integer.toHexString(
				errorCode.getIntegerCode())
			+ ")."
		);
}
```

#### static NexErrorCode fromIntegerValue (int code) *[static]*

Returns a `NexErrorCode` object for the specified error code.

**Parameters**

| Name | Description                                               |
|------|-------------------|
| code | The integer code to convert into a `NexErrorCode` object. |

**Returns**


The corresponding `NexErrorCode` object or null if an invalid code was passed.

#### NexErrorCategory getCategory ( )

Returns the category of the error.

>**CAUTION:** This is experimental and is subject to change. Error categories are an experimental feature. The idea is that the application can provide a friendlier (and possibly
more useful) message based on the category of the error. For example, if the category is NETWORK, the application
may suggest that the user check their network connection. This is experimental, so the set of categories may change in future versions of the API, or the feature may be
removed entirely. Use it with caution.

**Returns**


The category to which the error belongs.

#### String getDesc ( )

Gets a description of the error suitable for display in an error pop-up.

>**CAUTION:** This is experimental and is subject to change. The strings returned by this method may change in future
versions, may not cover all possible errors, and are not currently localized.

**Returns**


A string describing the error.

#### int getIntegerCode ( )

Gets the integer code associated with a given error.

**Returns**


An integer error code as provided by the `NexPlayer`™ engine.


#### String getSubDesc ( )

Gets the integer sub error code when unknown error occurs.

**Returns**


An integer sub error code of UNKNOWN as provided by the `NexPlayer`™ engine.

#### static int getUnknownSubCode ( ) *[static]*

Gets the integer sub error code when unknown error occurs.

**Returns**

An integer sub error code of UNKNOWN as provided by the `NexPlayer`™ engine.

#### CODEC_DECODING_ERROR = (0x0000000E,NexErrorCategory.GENERAL, "The codec reported an error")

Audio or video decoding error.

E.g. `NexPlayer` get a failure during parsing the content for playback or during decoding the audio or video bitstreams..

#### DATA_INACTIVITY_TIMEOUT = ( 0x00000026,NexErrorCategory.GENERAL, "The response timed out")

There is no response from the server within the set time of DATA_INACTIVITY_TIMEOUT property.

The default value of the DATA_INACTIVITY_TIMEOUT property is 60 seconds.

#### DRM_INIT_FAILED = ( 0x0000002c,NexErrorCategory.NOT_SUPPORT, "The content DRM initialization fail")

The content DRM Inital Fail Ex.

Invalid LAURL,

#### ERROR_AES_KEY_RECV_FAIL = ( 0x00010011,NexErrorCategory.GENERAL, "Failed to download AES key file.")

Failed to download the key file to decrypt the file that has been encrypted with AES.

(HLS)

#### ERROR_CONTENTINFO_PARSING_FAIL = ( 0x00010003,NexErrorCategory.NOT_SUPPORT, "ContentInfo parse fail.")

ContentInfo parse fail.

(SDP, ASF Header, Playlist...)

#### ERROR_DISABLED_MEDIA = ( 0x00010010,NexErrorCategory.GENERAL, "No track to play by Bitrate/Resolution limit.")

No track to play due to a bitrate/resolution limit.

E.g. The MIN_BW property is set to 2 Mbps and the playlist of playing contain has only 500 Kbps and 1 Mbps
tracks.

#### ERROR_INVALID_RESPONSE = ( 0x00010002,NexErrorCategory.NOT_SUPPORT, "The syntax of the response is invalid.")

The syntax of the response is invalid.

Ex. Mandatory header is missed in the response.

#### ERROR_INVALID_SERVER_STATUSCODE = ( 0x00020000,NexErrorCategory.PROTOCOL, "The HTTP response data recevied from the Server is error.")

The HTTP response data recevied from the Server is error.

It’s not 200 in HTTP response. Ex. 500, 503 ...

#### ERROR_MEDIA_NOT_FOUND = ( 0x0000002A,NexErrorCategory.GENERAL, "The content media was not found.")

The content media was not found on the server.

Ex. 403 forbidden, 404 not found,....

#### ERROR_NETWORK_PROTOCOL = ( 0x00000029,NexErrorCategory.PROTOCOL, "Network or protocol error")

Network related error such as socket errors.

Ex. socket open fail, connect fail, bind fail,...

#### HAS_NO_EFFECT = ( 0x00000001,NexErrorCategory.API,"Method has no effect")

The same command has been called already in the same state or the command is invalid.

E.g. If an open API is called while processing an open API, the engine does not regard it as an error.

#### HTTPDOWNLOADER_ERROR_EVENT_FULL = (0x00100000 + 9, NexErrorCategory.DOWNLOADER, "Http downloader event is full")

**Deprecated** For internal use only. Please do not use.

#### HTTPDOWNLOADER_ERROR_HAS_NO_EFFEECT = (0x00100000 + 7, NexErrorCategory.DOWNLOADER, "Http downloader - method has no effect")

The user attempted to call the same method many times.

All duplicates(except the first one) will be regarded as an error.

#### HTTPDOWNLOADER_ERROR_WRITE_FAIL = (0x00100000 + 6, NexErrorCategory.DOWNLOADER, "Http downloader file writing failure")

**Deprecated** For internal use only. Please do not use.

#### INVALID_MEDIA = ( 0x00000007,NexErrorCategory.CONTENT_ERROR, "File contains invalid syntax")

The content file contains invalid syntax.

It should be checked whether or not the content is a normal DRM file.


#### INVALID_STATE = ( 0x00000004,NexErrorCategory.API,"State is invalid")

The command is invalid at the current state.

E.g. `pause()` is called when the current state is NEXPLAYER_STATE_STOP.

#### NOT_SUPPORT_AUDIO_CODEC = ( 0x00000009,NexErrorCategory.NOT_SUPPORT, "The audio codec is not supported")

`NexPlayer` does not support the audio codec of the content.

E.g. The content is not yet supported by NexPlayer or a customer could not include codecs of `NexPlayer` SDK due
to licensing issues.

#### NOT_SUPPORT_MEDIA = ( 0x0000000C,NexErrorCategory.NOT_SUPPORT, "The content format is not supported or is not playable A/V track")

The format of the content is not supported.

The content has unavailable protocol(HLS,DASH, etc) or no playable A/V track which has audio or video codecs
that are not supported.

#### NOT_SUPPORT_TEXT = ( 0x0000001E,NexErrorCategory.NOT_SUPPORT, "The text is not supported")

The content has an unsupported text type.

For supported text, refer to `Supported Subtitles`, `Timed Text`, and `Closed Captions`.

#### NOT_SUPPORT_TO_SEEK = ( 0x00000018,NexErrorCategory.NOT_SUPPORT, "The media source does not support seeking.")

The media source does not support seeking.

The only Iframe content(Content is composed of I, B, and P frames), chunked mode based PD content, or live
content with an wide interval between each Iframe cannot be seeked.

#### NOT_SUPPORT_VIDEO_CODEC = ( 0x0000000A,NexErrorCategory.NOT_SUPPORT, "The video codec is not supported")

`NexPlayer` does not support the video codec of the content.

E.g. The content is not yet supported by `NexPlayer` or the customer did not include codecs of `NexPlayer` SDK due
to licensing issues.

#### NOT_SUPPORT_VIDEO_RESOLUTION = ( 0x0000000B,NexErrorCategory.NOT_SUPPORT, "The video resolution is not supported")

The resolution of the content is too high to play back.

E.g. The device has a resolution limit of 1080P but the content is 4K.

#### SOURCE_OPEN_TIMEOUT = ( 0x00000023,NexErrorCategory.GENERAL, "The media source open timed out")

There is no response from the server within the set time of SOURCE_OPEN_TIMEOUT property while calling
`open()`.

The default value of the SOURCE_OPEN_TIMEOUT property is 300 seconds.

#### UNKNOWN = ( 0x00000017,NexErrorCategory.GENERAL,"Unknown Error")

Unknown error.

This error is a kind of internal error such as "system failure". E.g. `NexPlayer` returns this when memory allocation is
failed for unknown reasons. It’s mostly an error that the user can not handle. Please contact a `NexPlayer` developer
for more details.

#### UNSUPPORTED_SDK_FEATURE = (0x70000001, NexErrorCategory.API, " JNI - SDK called unsupported feature" )

`NexPlayer` detected an unsupported feature(i.e.

recording or timeshift) or called a specific feature(i.e. call video capture in H/W mode).

### NexEventReceiver Class Reference

This class implements all `NexPlayer` interfaces.

An instance of *NexEventReceiver* can be used for parameter of NexPlayer.addEventRecevier, `NexPlayer.removeEventReceiver`

**Static Protected Attributes**

- `static Integer HAS_NO_EFFECT = 0xF000F000`


#### void onAsyncCmdComplete (NexPlayer mp,int command,int result,int param1,int param2)**

When an asynchronous method of `NexPlayer`™ has completed successfully or failed, this event occurs.

**Parameters**

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>mp</th>
  <td>The NexPlayer™ object generating the event.</td>
</tr>
  <th rowspan="16">command</th>
  <tr><td>NEXPLAYER_ASYNC_CMD_OPEN_LOCAL(0x00000001)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_OPEN_STREAMING(0x00000002)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_OPEN_TV(0x00000003)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_START_LOCAL(0x00000005)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_START_STREAMING(0x00000006)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_START_TV(0x00000007)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_STOP(0x00000008)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_PAUSE(0x00000009)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_RESUME(0x0000000A)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_SEEK(0x0000000B)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_STEP_SEEK(0x0000000E)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_REINITVIDEO(0x00000013)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_FASTPLAY_START(0x00000027)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_FASTPLAY_STOP(0x00000028)</td></tr>
  <tr><td>NEXPLAYER_ASYNC_CMD_SET_MEDIA_STREAM(0x00000031)</td></tr>
</tr>
<tr>
  <th>result</th>
  <td>Zero if the command was successful, otherwise an error code.</td>
</tr>
</table>                                                         

Below are the possible error codes for async_command_value.

- NEXPLAYER_ASYNC_CMD_OPEN_LOCAL

	- INVALID_STATE
	- INVALID_PARAMETER
	- SOURCE_OPEN_TIMEOUT
	- NOT_SUPPORT_AUDIO_CODEC
	- NOT_SUPPORT_VIDEO_CODEC
	- NOT_SUPPORT_MEDIA
	- FILE_INVALID_SYNTAX
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_OPEN_STREAMING

	- INVALID_STATE
	- INVALID_PARAMETER
	- SOURCE_OPEN_TIMEOUT
	- NOT_SUPPORT_AUDIO_CODEC
	- NOT_SUPPORT_VIDEO_CODEC
	- NOT_SUPPORT_MEDIA
	- FILE_INVALID_SYNTAX
	- ERROR_NETWORK_PROTOCOL
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_START_LOCAL

	- INVALID_STATE
	- INVALID_PARAMETER
	- DATA_INACTIVITY_TIMEOUT
	- NOT_SUPPORT_AUDIO_CODEC
	- NOT_SUPPORT_VIDEO_CODEC
	- NOT_SUPPORT_MEDIA
	- FILE_INVALID_SYNTAX
	- ERROR_NETWORK_PROTOCOL
	- CODEC_DECODING_ERROR
	- NOT_SUPPORT_VIDEO_RESOLUTION
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_START_STREAMING

	- INVALID_STATE
	- INVALID_PARAMETER
	- DATA_INACTIVITY_TIMEOUT
	- NOT_SUPPORT_AUDIO_CODEC
	- NOT_SUPPORT_VIDEO_CODEC
	- NOT_SUPPORT_MEDIA
	- FILE_INVALID_SYNTAX
	- ERROR_NETWORK_PROTOCOL
	- CODEC_DECODING_ERROR
	- NOT_SUPPORT_VIDEO_RESOLUTION
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_STOP

	- NOT_SUPPORT_MEDIA
	- ERROR_NETWORK_PROTOCOL
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_PAUSE

	- INVALID_STATE
	- INVALID_PARAMETER
	- ERROR_NETWORK_PROTOCOL
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_RESUME

	- INVALID_STATE
	- INVALID_PARAMETER
	- NOT_SUPPORT_AUDIO_CODEC
	- NOT_SUPPORT_VIDEO_CODEC
	- NOT_SUPPORT_MEDIA
	- FILE_INVALID_SYNTAX
	- ERROR_NETWORK_PROTOCOL
	- UNKNOWN

- NEXPLAYER_ASYNC_CMD_SEEK

	- INVALID_STATE
	- NOT_SUPPORT_TO_SEEK
	- DATA_INACTIVITY_TIMEOUT
	- NOT_SUPPORT_VIDEO_CODEC
	- CODEC_DECODING_ERROR
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_SETEXTSUBTITLE

	- INVALID_STATE
	- INVALID_PARAMETER
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_REINITVIDEO

	- INVALID_STATE
	- NOT_SUPPORT_VIDEO_CODEC
	- FILE_INVALID_SYNTAX
	- ERROR_NETWORK_PROTOCOL
	- CODEC_DECODING_ERROR
	- NOT_SUPPORT_TO_SEEK
	- DATA_INACTIVITY_TIMEOUT
	- UNKNOWN

- NEXPLAYER_ASYNC_CMD_FASTPLAY_START

	- INVALID_STATE
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_FASTPLAY_STOP

	- NOT_SUPPORT_AUDIO_CODEC
	- CODEC_DECODING_ERROR


- NEXPLAYER_ASYNC_CMD_SET_MEDIA_STREAM

	- INVALID_STATE
	- INVALID_PARAMETER
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_OPEN_STORE_STREAM

	- INVALID_PARAMETER
	- SOURCE_OPEN_TIMEOUT
	- NOT_SUPPORT_AUDIO_CODEC
	- NOT_SUPPORT_VIDEO_CODEC
	- ERROR_NETWORK_PROTOCOL
	- NOT_SUPPORT_MEDIA
	- FILE_INVALID_SYNTAX
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_START_STORE_STREAM

	- INVALID_STATE
	- INVALID_PARAMETER
	- NOT_SUPPORT_AUDIO_CODEC
	- NOT_SUPPORT_VIDEO_CODEC
	- NOT_SUPPORT_MEDIA
	- ERROR_NETWORK_PROTOCOL
	- FILE_INVALID_SYNTAX
	- UNKNOWN

**Parameters**

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>param1</th>
  <td>A value specific to the command that has completed. The following commands use this value (for all other commands, the value is undefined and reserved for future use, and must be ignored): - NEXPLAYER_ASYNC_CMD_SEEK: The actual position at which the seek command completed. Depending on the media format, this may be different than the position that was requested for the seek operation.</td>
</tr>
<tr>
  <th>param2</th>
  <td>A value specific to the command that has completed. Currently there are no commands that pass this parameter, and it is reserved for future use. Applications should ignore this value.</td>
</tr>
</table>

Implements `NexPlayer.IListener`.

#### void onAudioRenderCreate (NexPlayer mp, int samplingRate, int channelNum)

Notification that the audio rendering thread has been created.

Under previous versions of the SDK, it was necessary to create and manage the audio renderer. However, under
the current version this is done automatically, and the *onAudioRenderCreate* method should be empty or
contain only diagnostic code.

**Parameters**

| Name         | Description                                               |
|--------------|-------------------|
| mp           | The `NexPlayer`™ object to which this event applies.      |
| samplingRate | The sample rate (in Hz) of the content to be played back. |
| channelNum   | The number of channels in the content (1=mono, 2=stereo). |

Implements `NexPlayer.IListener`.

#### void onAudioRenderDelete (NexPlayer mp)

Notification that the audio rendering thread has been destroyed.

Under previous versions of the SDK, it was necessary to destroy the audio renderer. However, under the current
version this is done automatically, and the *onAudioRenderDelete* method should be empty or contain only
diagnostic code.


**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The `NexPlayer`™ object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onAudioRenderPrepared (NexPlayer mp)

This method is called when `NexPlayer`™ recognizes which audio render will be used.

Because `NexPlayer`™ supports only a SW audio render, this method will not be used.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The `NexPlayer`™ object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onBuffering (NexPlayer mp,int progress_in_percent)

This reports the current buffering status.

**Parameters**

| Name                | Description                                          |
|---------------------|--------------|
| mp                  | The `NexPlayer`™ object to which this event applies. |
| progress_in_percent | The current buffering percentage.                    |

Implements `NexPlayer.IListener`.

#### void onBufferingBegin (NexPlayer mp)

Reports the start of buffering.

**Parameters**


Implements NexPlayer.IListener.

#### void onBufferingEnd (NexPlayer mp)

This reports the end of buffering.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The `NexPlayer`™ object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onDataInactivityTimeOut (NexPlayer mp)

Reports Data Inactivity Timeout.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The `NexPlayer`™ object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onDateRangeData (NexPlayer mp, NexDateRangeData[ ] data)

This method reports the dataRange value that is contained in the EXT-X-DATERANGE tag.

**Parameters**

| Name | Description                                                                                                  |
|------|------|
| mp   | The `NexPlayer`™ object to which this event applies.                                                         |
| data | The array of `NexDateRangeData` object that includes dataRange and datacontained in the EXT-X-DATERANGE tag. |

Implements NexPlayer.IListener.

#### void onDownloaderAsyncCmdComplete (NexPlayer mp, int msg, int param1, int param2)

This function is called when an asynchronous command in the Downloader module is complete.

This method will be called whenever DownloaderOpen(), DownloaderClose(), DownloaderStart() or DownloaderStop() finish asynchronously.

**Parameters**

<table>
<tr>
  <th>Parameter</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="5">msg</th>
  <tr><td>NEXDOWNLOADER_ASYNC_CMD_OPEN = 0x00200001</td></tr>
  <tr><td>NEXDOWNLOADER_ASYNC_CMD_CLOSE = 0x00200002</td></tr>
  <tr><td>NEXDOWNLOADER_ASYNC_CMD_START = 0x00200003</td></tr>
  <tr><td>NEXDOWNLOADER_ASYNC_CMD_STOP = 0x00200004</td></tr>
</tr>
<tr>
  <th>param1</th>
  <td>This integer indicates the result of the command. It will be 0 in the event of success, or will be an error code in the event of failure.</td>
 </tr>
<tr>
  <th>param2</th>
  <td>Additional information, if available, concerning the result reported in param1. For example if the error is invalid response, param2 gives the HTTP status code.</td>
 </tr>
  
</table>

Implements `NexPlayer.IListener`.

#### void onDownloaderError (NexPlayer mp, int msg, int param1)

This function is called when an error is generated by the Downloader module.

**Parameters**

| Name   | Description                                                                               |
|--------|-------------------------------|
| mp     | The `NexPlayer`™ object to which this event applies.                                      |
| msg    | An integer indicating the error generated by the Downloader module.                       |
| param1 | This parameter is currently undefined but reserved for future use and should not be used. |

Implements `NexPlayer.IListener`.

#### void onDownloaderEventBegin (NexPlayer mp, int param1, int param2)

This method reports when a Downloader event has started.

**Parameters**

| Name   | Description                                                                           |
|--------|---------------------------|
| mp     | The `NexPlayer`™ object to which this event applies.                                  |
| param1 | This parameter is currently undefined and is not used but is reserved for future use. |
| param2 | The total size of the content file to be downloaded.                                  |

Implements `NexPlayer.IListener`.

#### void onDownloaderEventComplete (NexPlayer mp, int param1)

This function is called when a Downloader event has completed.

**Parameters**

| Name   | Description                                                                           |
|--------|---------------------------|
| mp     | The `NexPlayer`™ object to which this event applies.                                  |
| param1 | This parameter is currently undefined and is not used but is reserved for future use. |

Implements `NexPlayer.IListener`.

#### void onDownloaderEventProgress (NexPlayer mp, int param1, int param2, long param3, long param4)

This function is called to pass the downloading progress of a Downloader event.

**Parameters**

| Name   | Description                                                                                  |
|--------|----------------------------------|
| mp     | The `NexPlayer`™ object to which this event applies.                                         |
| param1 | This parameter is currently undefined and is not used but is reserved for future use.        |
| param2 | The time remaining until the downloading file has saved completely, in *msec*(milliseconds). |
| param3 | The size of the portion of the downloading file already received. in bytes (B).              |
| param4 | The total size of the content file being downloaded, in bytes (B).                           |

Implements `NexPlayer.IListener`.

#### void onDownloaderEventState (NexPlayer mp, int param1, int param2)

This method reports the current state of a Downloader event.

**Parameters**

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>mp</th>
  <td>The NexPlayer™ object to which this event applies.</td>
 </tr>
<tr>
  <th>param1</th>
  <td>This parameter is currently undefined and is not used but is reserved for future use.</td>
 </tr>
<tr>
  <th rowspan="5">param2</th>
  <tr><td>NEXDOWNLOADER_STATE_NONE = 0</td></tr>
  <tr><td>NEXDOWNLOADER_STATE_CLOSED = 2</td></tr>
  <tr><td>NEXDOWNLOADER_STATE_STOP = 3</td></tr>
  <tr><td>NEXDOWNLOADER_STATE_DOWNLOAD = 4</td></tr>
</tr>
  
</table>

Implements `NexPlayer.IListener`.

#### void onDynamicThumbnailData (NexPlayer mp, int width, int height, int cts, Object bitmap)**

This method will be called by the `NexPlayer`™ engine when thumbnail data is created.

If the *enableDynamicThumbnail()* method is called before Smooth Streaming content is in the *open* state,
then this method will be called and gets the thumbnail information associated with the content.

**Parameters**


| Name   | Description                                        |
|--------|------------|
| mp     | The `NexPlayer`™ object generating the event.      |
| width  | The width of the thumbnail image.                  |
| height | The height of the thumbnail image.                 |
| cts    | The current timestamp of the thumbnail image.      |
| bitmap | RGB buffer pointer(RGB565) of the thumbnail image. |

Implements `NexPlayer.IDynamicThumbnailListener`.

#### void onDynamicThumbnailRecvEnd (NexPlayer mp)

This callback method informs the Dynamic Thumbnail listener when the end of thumbnail data is received.

**Parameters**

| Name   | Description                                        |
|--------|------------|
| mp     | The `NexPlayer`™ object generating the event.      |

Implements `NexPlayer.IDynamicThumbnailListener`.

#### void onEndOfContent (NexPlayer mp)

This method indicates when playback has completed successfully up to the end of the content.

This event occurs when the player reaches the end of the file or stream. In most cases, applications should respond
to this by calling `NexPlayer.stop` and then updating the user interface.


**Parameters**

| Name   | Description                                        |
|--------|------------|
| mp     | The `NexPlayer`™ object generating the event.      |

Implements `NexPlayer.IListener`.

#### void onError (NexPlayer mp, NexErrorCode errorcode)

An error has occurred during playback.

**Parameters**

| Name      | Description                                   |
|-----------|---------------------------|
| mp        | The `NexPlayer`™ object generating the event. |
| errorcode | The error code for the generated error.       |

Implements `NexPlayer.IListener`.

#### int onHTTPABRTrackChange (NexPlayer mp, int param1, int param2, int param3)

This method will be called by the `NexPlayer`™ engine when the ABR track is switched.

**Parameters**

| Name   | Description                                   |
|--------|---------------------------|
| mp     | The `NexPlayer`™ object generating the event. |
| param1 | The current network bandwidth.                |
| param2 | The current track bandwidth.                  |
| param3 | The target track bandwidth.                   |

**Returns**


The exact track bandwidth that the user wants to set to forcibly.

Implements `NexPlayer.IHTTPABRTrackChangeListener`.


#### void onHTTPRequest (NexPlayer mp, String strRequest)

This method allows `NexPlayer`™ to pass HTTP request messages to an application.

While `NexPlayer`™ normally handles HTTP requests and responses internally, in cases where additional information
is required from the server (for example user cookies), this method can be used in conjunction with *onHTTPResponse* to allow an application to handle that information directly.

>**Note** This should be called before a request is sent to an HTTP server. To modify an HTTP request, see *onModifyHttpRequest*. To handle the response received, call *onHTTPResponse*.

**Parameters**

| Name       | Description                                               |
|------------|-------------------|
| mp         | The `NexPlayer`™ object to which this event applies.      |
| strRequest | The HTTP request to be sent to the server, as a *String*. |

**See Also**

- `NexPlayer.onHTTPResponse`
- `NexPlayer.onModifyHttpResponse`

Implements `NexPlayer.IListener`.

#### void onHTTPResponse (NexPlayer mp, String strResponse)

This method allows responses from an HTTP server to be received and handled in a more customized way.

While `NexPlayer`™ normally handles HTTP requests and responses internally, in cases where additional information
is required from the server (for example user cookies), this method can be used in conjunction with *onHTTPRequest* to handle that information directly.

>**Note** This should be called after a response has been received from the server. To change the requests being
made,on *ModifyHttpRequest* should be called.


**Parameters**

| Name        | Description                                          |
|-------------|--------------|
| mp          | The `NexPlayer`™ object to which this event applies. |
| strResponse | The response from the HTTP server, as a *String*.    |

**See Also**


- `NexPlayer.onHTTPRequest`
- `NexPlayer.onModifyHttpRequest`

Implements `NexPlayer.IListener`.

#### String onModifyHttpRequest (NexPlayer mp, int param1, Object input_obj)

This method provides the HTTP Request that will be used by `NexPlayer`™ when an HTTP request is modified.

**Parameters**

| Name      | Description                                          |
|-----------|--------------|
| mp        | The `NexPlayer`™ object to which this event applies. |
| param1    | The length of the current HTTP Request data.         |
| input_obj | The modified HTTP Request data.                      |


**Returns**

A String with the modified HTTP request. This value will be used by NexPlayer™ instead of the previous HTTP
request.

**See Also**


- Enabling Modified HTTP Requests for more information.

Implements `NexPlayer.IListener`.

#### void onOfflineKeyExpiredListener (NexPlayer mp)

This method will be called by the `NexPlayer`™ engine when the keyId of media DRM should be expired.


**Parameters**

| Name | Description                                   |
|------|---------------------------|
| mp   | The `NexPlayer`™ object generating the event. |

**Returns**


the key ID of media drm stored with onOfflineKeyStoreListener.

Implements `NexPlayer.IOfflineKeyListener`.

#### byte [ ] onOfflineKeyRetrieveListener (NexPlayer mp)

This method will be called by the NexPlayer™ engine when the keyId of media DRM should be retrieved.

**Parameters**

| Name | Description                                   |
|------|---------------------------|
| mp   | The `NexPlayer`™ object generating the event. |

**Returns**


the key ID of media drm stored with onOfflineKeyStoreListener.

Implements `NexPlayer.IOfflineKeyListener`.

#### void onOfflineKeyStoreListener (NexPlayer mp,byte[ ]keyId)

This method will be called by the `NexPlayer`™ engine when the keyId of media DRM should be stored.

**Parameters**


| Name  | Description                                   |
|-------|---------------------------|
| mp    | The `NexPlayer`™ object generating the event. |
| keyId | The Key ID of Media drm for offline playback. |

**Returns**

void.


Implements `NexPlayer.IOfflineKeyListener`.

#### void onPauseSupervisionTimeOut (NexPlayer mp)

Reports Pause Supervision Timeout.

**Parameters**

| Name | Description                                   |
|------|---------------------------|
| mp   | The `NexPlayer`™ object generating the event. |

Implements `NexPlayer.IListener`.

#### void onPictureTimingInfo (NexPlayer mp, NexPictureTimingInfo[ ] arrPictureTimingInfo)**

This method provides SEI picture timing information about video frames of H.264 content when available.

This method is called when *ENABLE_H264_SEI* is enabled and the H.264 content contains supplemental enhancement information (SEI). While SEI may include a variety of attributes, this method specifically receives SEI
picture timing information when available.

`NexPlayer`™ delivers the timing information through this method by passing an instance of `NexPictureTimingInfo`
whenever SEI picture timing information is received.

**Parameters**


| Name                 | Description                                                                                         |
|----------------------|---------------------|
| mp                   | The `NexPlayer`™ object to which this event applies.                                                |
| arrPictureTimingInfo | The `NexPictureTimingInfo` object that includes the SEI picture timing information for the content. |

Implements `NexPlayer.IListener`.

#### void onProgramTime (NexPlayer mp, String strTag, long offset)

This retrieves the program time and date information from HLS content when the #EXT-X-PROGRAM-DATE-TIME tag is present.

This event happens approximately once every second when a .ts file is decoding (approximately every 30 frames). The *strTag* value will remain the same until a new #EXT-X-PROGRAM-DATE-TIME tag is received in a subsequent segment, whereas the value of the time *offset* parameter will continuously rise in subsequent frames until a new #EXT-X-PROGRAM-DATE-TIME tag is received.

The values from *strTag* and *offset* parameters can be added to determine the current frame’s timestamp. The time can then be used to help sync content and text streams or to determine when content should play.

>**Note** If the program time is required at a more specific moment in time, the same information can be retrieved by calling the method, getProgramTime.

**Parameters**

| Name   | Description                                                                                                                           |
|--------|-----------|
| mp     | The `NexPlayer`™ object generating the event.                                                                                         |
| strTag | The most recent #EXT-X-PROGRAM-DATE-TIME tag in the HLS content, as a *String*.                                                       |
| offset | The time offset of the currently decoding frame’s timestamp with respect to the #EXT-X-PR- OGRAM-DATE-TIME tag time, in milliseconds. |

**See Also**


- `getProgramTime`

Implements `NexPlayer.IListener`.

#### void onRecording (NexPlayer mp, int recDuration, int recSize)

This reports `NexPlayer`™’s recording status.


**Parameters**

| Name        | Description                                                 |
|-------------|---------------------|
| mp          | The `NexPlayer`™ object generating the event.               |
| recDuration | An integer indicating the duration of the recording so far. |
| recSize     | An integer indicating the size of the recording so far.     |

**Deprecated** Not available in current version; do not use.

Implements `NexPlayer.IListener`.

#### void onRecordingEnd (NexPlayer mp, int success)

This indicates when `NexPlayer`™ recording has ended.

**Parameters**

| Name    | Description                                   |
|---------|---------------------------|
| mp      | The `NexPlayer`™ object generating the event. |
| success |                                               |

**Deprecated** Not available in current version; do not use.

Implements `NexPlayer.IListener`.

#### void onRecordingErr (NexPlayer mp,int err)

This indicates when there has been a `NexPlayer`™ recording error.

**Parameters**


| Name | Description                                   |
|------|---------------------------|
| mp   | The `NexPlayer`™ object generating the event. |
| err  | An error while recording.                     |

**Deprecated** Not available in current version; do not use.

Implements `NexPlayer.IListener`.

#### void onRTSPCommandTimeOut (NexPlayer mp)

Reports RTSP command Timeout.

**Parameters**

| Name | Description                                   |
|------|---------------------------|
| mp   | The `NexPlayer`™ object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onSessionData (NexPlayer mp, NexSessionData[ ] data)

This method reports the arbitrary session data of the HLS master playlist.

**Parameters**

| Name | Description                                                                                               |
|------|---------------------------|
| mp   | The `NexPlayer`™ object to which this event applies.                                                      |
| data | The array of `NexSessionData` object that includes the arbitrary session data of the HLS master playlist. |

Implements `NexPlayer.IListener`.

#### void onSignalStatusChanged (NexPlayer mp, int pre, int now)

`NexPlayer`™’s signal status has been changed.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The `NexPlayer`™ object to which this event applies. |
| pre  | The previous signal status.                          |
| now  | The current signal status.                           |

Implements `NexPlayer.IListener`.

#### void onStartAudioTask (NexPlayer mp)

The `NexPlayer`™ audio task has started.

**Deprecated** This method is only included for compatibility with older code and should not be used.

This is provided for compatibility with older code, and new applications may safely ignore this event.

**Parameters**

| Name | Description                                  |
|------|--------------------------|
| mp   | The `NexPlayer`™ object generating the event |

Implements `NexPlayer.IListener`.

#### void onStartVideoTask (NexPlayer mp)

The `NexPlayer`™ video task has started.

**Deprecated** This method is only included for compatibility with older code and should not be used.

This is provided for compatibility with older code, and new applications may safely ignore this event.

**Parameters**

| Name | Description                                  |
|------|--------------------------|
| mp   | The `NexPlayer`™ object generating the event |

Implements `NexPlayer.IListener`.

#### void onStateChanged (NexPlayer mp, int pre, int now)

`NexPlayer`™’s state has been changed.

This method is called when `NexPlayer`™’s state has been changed but it does not mean that the changing operation
has completed. Therefore, the next operation can be carried out only after the event *onAsyncCmdComplete* is
received, not when this event,*onStateChanged*, is called.

**Parameters**

| Name | Description                                  |
|------|--------------------------|
| mp   | The `NexPlayer`™ object generating the event |
| pre  | The previous play status.                    |
| now  | The current play status.                     |

Implements `NexPlayer.IListener`.

#### void onStatusReport (NexPlayer mp, int msg, int param1)

This function is called when there is a change in the available content information.

This can happen, for example, if the track changes during HLS playback, resulting in changes to the bitrate, resolution, or even the codec in use.

Themsgparameter contains information about the condition that has changed.

Because multiple calls to this function can be issued for the same event, unknown values for *msg* should generally be ignored. To handle general status changes that affect content information without processing duplicate
messages, the best approach is just to handle NEXPLAYER_STATUS_REPORT_CONTENT_INFO_UPDATED.

To determine the new content information when this event occurs, call `getContentInfo` or `getContentInfoInt`.

**Parameters**

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>mp</th>
  <td>The NexPlayer™ object to which this event applies.</td> 
</tr>
<tr>
  <th rowspan="22">msg</th>
</tr>
  <tr><td><b>NEXPLAYER_STATUS_REPORT_NONE (0x00000000)</b>: No status change (this value is not normally passed to *onStatusReport*, and should generally be ignored)</td></tr>
  <tr><td><b>NEXPLAYER_STATUS_REPORT_AUDIO_GET_CODEC_FAILED (0x00000001)</b>: Failed to determine the audio codec. This notification can happen at the beginning of playback, or during playback if there is an audio codec change. This can happen because of a switch to a new codec that NexPlayer™ does not support, or due to an error in the format of the content or corrupted data in the content.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_VIDEO_GET_CODEC_FAILED (0x00000002)</b>: Failed to determine the video codec. This notification can happen at the beginning of playback, or during playback if there is a video codec change. This can happen because of a switch to a new codec that NexPlayer™ does not support, or due to an error in the format of the content or corrupted data in the content.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_AUDIO_INIT_FAILED (0x00000003)</b>: The audio codec failed to initialize. This can happen for several reasons. The container may     indicate the wrong audio codec, or the audio stream may be incorrect or corrupted, or the audio stream may use a codec version or features that NexPlayer™ doesn’t support.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_VIDEO_INIT_FAILED (0x00000004)</b>: The video codec failed to initialize. This can happen for several reasons. The container may     indicate the wrong video codec, or the video stream may be incorrect or corrupted, or the video stream may use a codec version or features that NexPlayer™ doesn’t support.</td></tr>
	
<tr><td><b>NEXPLAYER_STATUS_REPORT_TRACK_CHANGED (0x00000005)</b>: The track has changed. This happens for protocols such as HLS that provide the content in multiple formats or at multiple resolutions or bitrates. The ID of the new track can be found in mCurrTrackID, and also inparam1. When this event occurs, `NexPlayer`™ also enerates a eNEXPLAYER_CONTENT_INFO_UPDATED event.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_STREAM_CHANGED (0x00000006)</b>: The stream being played back has changed (between the states Audio-Only, Video-Only and     Audio+Video). The new stream type is in mMediaType, and also in param1.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_DSI_CHANGED (0x00000007)</b>: An attribute relating to the video or audio format (such as the resolution, bitrate, etc.) has changed. This is considered Decoder Specific Information (DSI).</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_OBJECT_CHANGED (0x00000008)</b>: One of the codec objects in use has changed (that is, the audio or video codec in use has     changed). See mAudioCodec and mVideoCodec to get the ID of the new codec.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_CONTENT_INFO_UPDATED (0x00000009)</b>: The content information has changed. When onStatusReport is called with any other non-Failure value for msg, it will also be called with this as well. This is a good place to monitor insignificant changes to the content information.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_DOWNLOAD_PROGRESS (0x00000080)</b>: Reports the progress made storing content for offline play. This message will be called     when content is opened with NEXPLAYER_SOURCE_TYPE_STORE_STREAM type. For this notification, the parameter param1 returns the percentage of downloading     complete (0-100).</td></tr>
	
<tr><td><b>NEXPLAYER_STATUS_REPORT_AVMODE_CHANGED (0x0000000A)</b>: The stream being played back has changed and the new stream has a different media type. This event happens whenever the state changes between video-only, audio-only and audio-video. param1 contains the new media type: 1 for audio, 2 for video, 3 for     both.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_HTTP_INVALID_RESPONSE (0x0000000B)</b>: An HTTP error response was received from the server.*param1* contains the error code     (this is a normal HTTP response code, such as 404, 500, etc.)</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_DISCONTINUITY_EXIST (0x00000012)</b>: There is a discontinuity tag found in the HLS content playlist.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_OBJECT_CHANGED (0x00000008)</b>: One of the codec objects in use has changed (that is, the audio or video codec in use has     changed). See mAudioCodec and mVideoCodec to get the ID of the new codec.</td></tr>

 <tr><td><b>NEXPLAYER_STATUS_REPORT_EXTERNAL_DOWNLOAD_CANCELED (0x00000020)</b>: The player canceled External PD Mode and played content on Normal PD Mode. (e.g. The engine attempted to play regular content instead of piff content on External PD Mode).</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED (0x00000021)</b>: Either the Minimum bandwidth or Maximum bandwidth has been changed</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_STREAM_RECV_PAUSE (0x00000060)</b>: When the prefetch buffer exceeds the maximum value, the player pauses the buffer control.     The user can adjust the maximum value of the prefetch buffer by using setProperty of the properties MAX_BUFFER_RATE or MAX_BUFFER_DURATION.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_STREAM_RECV_RESUME (0x00000061)</b>: When the prefetch buffer is below the minimum value, the player resumes the buffer control.     The user can adjust the mimimum value of the prefetch buffer by using setProperty of the properties MIN_BUFFER_RATE or MIN_BUFFER_DURATION.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_DOWNLOAD_PROGRESS (0x00000080)</b>: Reports the progress made storing content for offline play. This message will be called     when content is opened with NEXPLAYER_SOURCE_TYPE_STORE_STREAM type. For this notification, the parameter param1 returns the percentage of downloading     complete (0-100).</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_MAX (0xFFFFFFFF)</b>: This value is reserved; do not use it.</td></tr>
	
<tr>
  <th>param1</th>
  <td>Additional information. The meaning of this depends on the value of msg. If the description above doesn’t refer to param1, then this parameter is undefined for that value of msg and should not be used.</td> 
</tr>
</table>                                                                                                                                                       

Implements `NexPlayer.IListener`.
 
 
#### void onTextRenderInit (NexPlayer mp, int numTracks)


Called when initially beginning playback of media content with associated subtitles.

**Parameters**


| Name      | Description                                                                                                                                           |
|-----------|---------------------------|
| mp        | The `NexPlayer`™ object to which this event applies.                                                                                                  |
| numTracks | The number of subtitle tracks available for this media. Note that this may be 0 if there are no subtitles, or this function may not be called at all. |

Implements `NexPlayer.IListener`.

#### void onTextRenderRender (NexPlayer mp, int trackIndex, NexClosedCaption textInfo)

This function is called when new subtitle data is ready for display.

This is called whenever playback reaches a point in time where subtitles on any track need to be displayed or
cleared.

The text to display is provided in a *NexClosedCaption* object as a byte array; it is the responsibility of the
application to convert this to text with the appropriate encoding. Where possible, the encoding information will
be provided in the NexClosedCaption.mEncodingType, but many subtitle file formats do not explicitly specify an
encoding, so it may be necessary for the application to guess the encoding or allow the user to select it.


**Parameters**


| Name       | Description                                                          |
|------------|------------------------------|
| mp         | The `NexPlayer`™ object to which this event applies.                 |
| trackIndex | This is always zero and should always be ignored.                    |
| textInfo   | The text to be displayed (cast this to a *NexClosedCaption* object). |

Implements `NexPlayer.IListener`.

#### void onTime (NexPlayer mp,int millisec)

This method indicates that playback has progressed to the specified position.

This event occurs once per second. If the application is displaying the current play position, it should update it to
reflect this new value.

Applications that wish to update the play time more often that once per second or with a greater accuracy may
ignore this event and create their own timer, in which case they can use the current play time reported in `NexContentInformation`.

**Parameters**

| Name     | Description                                  |
|----------|--------------------------|
| mp       | The `NexPlayer`™ object generating the event |
| millisec | Current play position in milliseconds.       |

Implements `NexPlayer.IListener`.

#### void onTimedMetaRenderRender (NexPlayer mp, NexID3TagInformation TimedMeta)

This method is called when new timed metadata is ready for display in HLS.

Timed metadata includes additional information about the playing content that may be displayed to the user and this
information may change at different times throughout the content. Each time new metadata is available for display,
this method is called.

**See Also**


- NexID3TagInformation for more details on the available metadata information.


**Parameters**

| Name      | Description                                                                                                    |
|-----------|--------|
| mp        | The `NexPlayer`™ object to which this event applies.                                                           |
| TimedMeta | An `NexID3TagInformation` object that contains the timed metadata associated with the content to be displayed. |

Implements `NexPlayer.IListener`.

#### void onTimeshift (NexPlayer mp, int currTime, int TotalTime)

This is a deprecated method that formerly reported `NexPlayer`™’s Time shift status.

**Parameters**

| Name      | Description                                   |
|-----------|---------------------------|
| mp        | The `NexPlayer`™ object generating the event. |
| currTime  | The current time.                             |
| TotalTime | The total time.                               |

**Deprecated** Not available in current version; do not use.

Implements `NexPlayer.IListener`.

#### void onTimeshiftErr (NexPlayer mp, int err)

This is a deprecated method that formerly reported any `NexPlayer`™ Time shift error.

**Deprecated** Not available in current version; do not use.

Implements `NexPlayer.IListener`.

#### void onVideoRenderCapture (NexPlayer mp, int width, int height, int pixelbyte, Object bitmap)

Called when a frame of video has been captured.

**Deprecated** Not available in current version; use IVideoRendererListener instead.

After calling `captureVideo` to set up video capture, this function will be called whenever a frame is captured, and can
process the captured frame as necessary.

	Bitmap bitmap = Bitmap.createBitmap(width, height, pixelbyte==2?Config.RGB_565:Config.ARGB_8888 );
	ByteBuffer RGBBuffer = (ByteBuffer)rgbBuffer;
	RGBBuffer.asIntBuffer();
	bitmap.copyPixelsFromBuffer(RGBBuffer);

**Parameters**

| Name      | Description                                               |
|-----------|-------------------|
| mp        | The `NexPlayer`™ object to which this event applies.      |
| width     | The width of the captured frame.                          |
| height    | The height of the captured frame.                         |
| pixelbyte | The number of bytes per pixel (2 for RGB565; 4 for RGBA). |
| bitmap    | The object where the captured video frame data is stored. |

Implements `NexPlayer.IListener`.

#### void onVideoRenderCreate (NexPlayer mp, int width, int height, Object rgbBuffer)**

This method is called when `NexPlayer`™ needs the application to create a surface on which to render the video.

**Deprecated** Not available in current version; use IVideoRendererListener instead.

The application must respond to this by calling `setDisplay`.

Generally speaking, the application will actually create the surface earlier, during GUI layout, and will simply use
the existing handle in response to this call. There are, however, some threading considerations. See `setDisplay` for
details.

**Parameters**

| Name      | Description                                                                                       |
|-----------|-------------------|
| mp        | The `NexPlayer`™ object to which this event applies.                                              |
| width     | The width of the source video.                                                                    |
| height    | The height of the source video.                                                                   |
| rgbBuffer | Direct RGB Buffer(RGB565 format). This RGB buffer is shared with `NexPlayer`™ Engine native code. |

Implements `NexPlayer.IListener`.

#### void onVideoRenderDelete (NexPlayer mp)

This method is called when `NexPlayer`™ no longer needs the render surface.

**Deprecated** Not available in current version; use IVideoRendererListener instead.

If a surface was created in *onVideoRenderCreate*, this is the place to destroy it. However, if (as in most cases)
an existing surface was used, then this function need not take any special action, other than updating whatever state
the application needs to track.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The `NexPlayer`™ object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onVideoRenderPrepared (NexPlayer mp)

This method is called when `NexPlayer`™ recognizes which video render type will be used.

> **Deprecated** Not available in current version; use IVideoRendererListener instead.

At first, `NexPlayer`™ does not know which renderer will be used. When this method is called, the application can determine the video renderer mode by calling `GetRenderMode` and prepare for the specified video renderer, as in the following example code:

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
				FrameLayout view = (FrameLayout)findViewById(R.id.gl_container);
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
			if(mNexPlayer.GetRenderMode() == NexPlayer.NEX_USE_RENDER_AND
)
			{
				mSurfaceHolder.setType(SurfaceHolder.SURFACE_TYPE_NORMAL);//For Gingerbread Android Renderer
			}
			else
			{
				mSurfaceHolder.setType(SurfaceHolder.SURFACE_TYPE_PUSH_BUFFERS);/ For HW Renderer
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

| Name | Description                                          |
|------|--------------|
| mp   | The `NexPlayer`™ object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onVideoRenderRender (NexPlayer mp)

This requests to display Video frame data at JAVA application.

> **Deprecated** Not available in current version; use IVideoRendererListener instead.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The `NexPlayer`™ object to which this event applies. |

Implements `NexPlayer.IListener`.

### NexLogsToFile.NexFileLogPreset Enum Reference

**Public Member Functions**

- `NexFileLogPreset (int preset)`
- `int getIntegerCode ()`

**Static Public Member Functions**

- `static NexFileLogPreset fromIntegerValue (int preset)`

**Public Attributes**

- `DEFAULT = (0)`
- `FOR_PROTOCOL = (1)`
- `FOR_ENGINE = (2)`
- `FOR_AUDIO = (3)`
- `FOR_VIDEO = (4)`
- `FOR_DRM = (5)`
- `FOR_CAPTION = (6)`
- `FULL_LOGS = (7)`

### NexHDManager Class Reference

**Static Public Member Functions**

- `static native int initManager (String strEngineLibName)`

### NexHLSAES128DRMManager Class Reference

**Classes**

- `interface IAESCallbackListener`
    
    An interface for GetKeyExternal and IsSupportKey Callbacks.

#### native int initDRMManager (String strEnginePath)

Initializes and registers `NexHLSAES128DRMManager`.


**Parameters**

| Name             | Description                                     |
|------------------|---------|
| strEngineLibName | The relevant engine library name as a *string*. |

#### native int initDRMManagerMulti (Object nexPlayerHandle, String strEnginePath)

For internal use only.

Please do not use.

#### void setAESCallbackListener (IAESCallbackListener listener)

This method sets and registers a *IAESCallbackListener* listener.

**Parameters**

| Name     | Description            |
|----------|----|
| listener | `IAESCallbackListener` |

**See Also**


- `NexPlayer.IHTTPABRTrackChangeListener`

### NexID3TagInformation Class Reference

This class contains information about the metadata associated with the content, from sources such as ID3 tags.

This includes a series of text fields (the set of fields that actually contain information will vary depending on the format and which fields the content creator has filled in). These fields include information such as the album name, artist, lyrics and so on.

This also includes the picture associated with the content, for formats such as MP3 and AAC that can have an optional associated still image, included as a `NexID3TagPicture` object.

This image is generally used in place of video for content that does not have video. The exact use of the still image is up to the content producer. In the case of an MP3 or AAC audio file, it is usually the album cover artwork. In the case of HTTP Live Streaming, audio-only tracks often have a still image to be shown in place of the video. This image may change during playback (for example, some audio-only HLS streams provide a new image every ten seconds or so).

When timed metadata is used with HLS content, the `NexID3TagInformation` object associated with the content will be updated each time new metadata is available during playback, and should be updated accordingly.

#### ArrayList < NexID3TagText > getArrExtraData ( )

This method gets a list of customized ID3 tags and the extra data they contain included in content timed metadata.

For the list of customized ID3 tags to be recognized and handled by `NexPlayer`™, they should be set using the
NexProperty *TIMED_ID3_META_KEY* after `NexPlayer`™ is initialized but before *NexPlayer.open* is called.

**Returns**


The customized ID3 tags and the additional data they contain as an ArrayList of `NexID3TagText` objects.

**See Also**


- `setArrExtraData`
- `TIMED_ID3_META_KEY`

#### NexID3TagText getComment ( )

This method gets the data included in the comment frame of the current content’s ID3 tags.

**Returns**


The comment frame data as a `NexID3TagText` object.


#### NexID3TagText getPrivateFrame ( )

This method gets the information included in private frames of the current content’s ID3 tags.

The private frames in ID3 tags are used to include additional information that is required by a program but can’t be
included in the other ID3 tag frames, and are tagged:

	<Header for ’Private frame’, ID: "PRIV">
	Owner identifier 	<text string> $00
	The private data 	<binary data>

Where the ’Owner identifier’ string includes contact information for the organization which is responsible for the
frame and its provided binary data.

`NexPlayer`™ merely passes the private frame information to the client application where it can be handled as desired.

#### NexID3TagText getText ( )

This method gets the data in the text frame included in the ID3 tags of the current content, if available.

**Returns**


The text frame data as a `NexID3TagText` object.

#### int getTimeCode ( )

This method gets the timestamp of timed metadata.

**Returns**


The timestamp of timed metadata in millisecond unit.

#### void setArrExtraData (ArrayList < NexID3TagText > ExtraData)

This method sets the list of customized ID3 tags and the extra data they contain included in content timed metadata.

For the list of customized ID3 tags to be recognized and handled by `NexPlayer`™, they should be set using the
NexProperty *TIMED_ID3_META_KEY* after `NexPlayer`™ is initialized but before *NexPlayer.open* is called.

**Parameters**

| Name      | Description                                                                                                  |
|-----------|------|
| ExtraData | The list of customized ID3 tags and the extra data they contain, as an ArrayList of `NexID3TagText` objects. |

**See Also**


- `getArrExtraData`
- `TIMED_ID3_META_KEY`

#### void setComment (NexID3TagText comment)

This method sets the information from the comment frame in the current content’s ID3 tags.

**Parameters**

| Name    | Description                                                |
|---------|--------------------|
| comment | The data in the comment frame as a `NexID3TagText` object. |

#### void setPicture (NexID3TagPicture picture)

This method sets the picture associated with the current content, if available.

This may be used as a still image to display in the event that video for particular content may not be displayed (due to network variability or perhaps an unsupported video codec is in use).

**Parameters**

| Name    | Description                                                            |
|---------|------------|
| picture | A `NexID3TagPicture` object containing the picture data and MIME type. |

#### void setPrivateFrame (NexID3TagText privateFrame)

This method sets the information included in private frames of the current content’s ID3 tags.

**See Also**


- `getPrivateFrame` for more information.

#### void setText (NexID3TagText text)

This method sets the text frame data in this class.

**Parameters**

| Name | Description                                      |
|------|----------|
| text | The text frame data as a `NexID3TagText` object. |

### NexID3TagPicture Class Reference

This class allows `NexPlayer`™ to handle picture information included in timed metadata ID3 tags.

`NexPlayer`™ passes an instance of this class whenever new picture information for the current content is received from its ID3 tags, and is included in an updated `NexID3TagInformation` object.


#### byte [ ] getPictureData ( )

This method gets the picture data associated with current content from the content’s timed metadata ID3 tags.

**Returns**

A byte array of the picture data.

#### NexID3TagText getMimeType()

This method gets the MIME type of the picture associated with the current content (from the content’s timed metadata ID3 tags).


### NexID3TagText Class Reference

This class determines the encoding of text data included in content ID3 tags.

**Public Member Functions**

- `int getEncodingType ()`
    
    This method gets the encoding type of text included in content ID3 tags.
- `String **getEncodingTypeName** ()`
- `byte[ ] getTextData ()`
    
    This method gets the text data included in content ID3 tags.
- `byte[ ] getExtraDataID ()`
    
    This method gets the customized ID3 tags of the extra data added to content timed metadata so they can be passed to the app.

#### int getEncodingType ( )

This method gets the encoding type of text included in content ID3 tags.

**Returns**


The encoding type of the text.

#### byte [ ] getExtraDataID ( )

This method gets the customized ID3 tags of the extra data added to content timed metadata so they can be passed to the app.

>**Warning** This method can only be used if the customized ID3 tag names have already been set using the NexProperty *TIMED_ID3_META_KEY*.

**Returns**

The customized ID3 tags as a byte array, or *null* if *TIMED_ID3_META_KEY* has not been set.

**See Also**


- `TIMED_ID3_META_KEY`

#### byte [ ] getTextData ( )

This method gets the text data included in content ID3 tags.

**Returns**

The text data as an array.

#### final int ENCODING_TYPE_ASCII = 0x20000000 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_ISO_8859 = 0x30000000 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_ISO_8859_1 = 0x30000010 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_UNICODE = 0x10000000 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_UNKNOWN = 0x00000000 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_UTF16 = 0x10000020 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_UTF16_BE = 0x10000030 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_UTF32 = 0x10000040 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_UTF32_BE = 0x10000050 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

#### final int ENCODING_TYPE_UTF8 = 0x10000010 *[static]*

A possible return value for `NexID3TagText.getEncodingType`.

### NexLog Class Reference

API for sending log output.

Generally, use the `NexLog.v() NexLog.d() NexLog.i() NexLog.w()` and `NexLog.e()` methods.

> **Deprecated** For internal use only. Please do not use.

#### static void d (String tag, String msg) *[static]*

This method sends a DEBUG log message.

**Parameters**

| Name | Description                                                                                                          |
|------|--------------|
| tag  | Used to identify the source of a log message. It usually identifies the class or activity where the log call occurs. |
| msg  | The message to be logged.                                                                                            |

#### static void e (String tag, String msg) *[static]*

This method sends an ERROR log message.

**Parameters**

| Name | Description                                                                                                          |
|------|--------------|
| tag  | Used to identify the source of a log message. It usually identifies the class or activity where the log call occurs. |
| msg  | The message to be logged.                                                                                            |

#### static void i (String tag, String msg) *[static]*

This method sends an INFO log message.

**Parameters**

| Name | Description                                                                                                          |
|------|--------------|
| tag  | Used to identify the source of a log message. It usually identifies the class or activity where the log call occurs. |
| msg  | The message to be logged.                                                                                            |

#### static void v (String tag, String msg) *[static]*

This message sends a VERBOSE log message.

**Parameters**

| Name | Description                                                                                                          |
|------|--------------|
| tag  | Used to identify the source of a log message. It usually identifies the class or activity where the log call occurs. |
| msg  | The message to be logged.                                                                                            |

#### static void w (String tag, String msg) *[static]*

This message sends a WARN log message.

**Parameters**

| Name | Description                                                                                                          |
|------|--------------|
| tag  | Used to identify the source of a log message. It usually identifies the class or activity where the log call occurs. |
| msg  | The message to be logged.                                                                                            |

#### boolean Debug = false *[static]*

Whether or not a log message should be sent to log output.

If this value is *TRUE*, the log message will be sent to log output.

### NexLogsToFile Class Reference

Runnable
 
**Classes**

- class Builder
- enum NexFileLogPreset

**Public Member Functions**

- void **run** ()
- void **clean** ()
- void **kill** ()

**Protected Member Functions**

- void **finalize** () throws Throwable

### NexLogStringQueue Class Reference

**Classes**

- `class CharUnit`
    
	This class defines a character unit in CEA 708 closed captions.


**Public Attributes**

- `CharUnit mCharAttr`

**Static Public Attributes**

- `static final int LOGSTRQ_MAX_LINE = 15`
- `static final int LOGSTRQ_MAX_COUNT_IN_A_ROW = 42`

**See Also**
 
- NexEIA708CaptionView
- NexEIA708Struct
  
> **Deprecated** For internal use only. Please do not use.

#### int GetHeight ()

This method gets the height of CEA 708 closed captions.
 
#### int GetWidth ()

This method gets the width of CEA 708 closed captions.

#### void PushChar (int nChar)

This method pushes a character in the display of CEA 708 closed captions.

#### void Reset ()

This method resets CEA 708 closed captions.
 
#### void SetAttr (byte ww, byte j, byte sd, byte pd)

This method sets the attributes of CEA 708 closed captions.
 
#### void SetLocation (int row, int col)

This method sets the position of CEA 708 closed captions.
 
#### void SetSize (int rc, int cc, int rl, int cl, int maxcol)

This method sets the size of CEA 708 closed captions.
 
### NexMediaDrmSession Class Reference

**Classes**

- `interface ProvisioningManager`

**Public Member Functions**

- `boolean release()`
- `final int getState()`
- `void updateDRMKey()`

### NexMediaDrmSessionManager Class Reference

**Classes**

- `interface EventListener`

**Public Member Functions**

- `void provisionRequired(NexMediaDrmSession session)`
- `void onProvisionError(Exception error)`
- `void onProvisionCompleted()`
- `void updateDRMKey()`

**Protected Member Functions**

- `void releaseMediaDrm()`

### NexNetAddrTable Class Reference

This class allows an application to retrieve host information by using the hostname and its corresponding custom IP address registered by the developer.


**Classes**

- `class NetAddrTableInfo`
	
	This class defines the information possible for an entry made with the method addEntry, including the hostname and its corresponding IP address when a customized IP address is desired.

#### boolean addEntry (String hostname, String address)

This method adds an entry to the table of customized IP addresses.

An entry includes a hostname and its corresponding custom IP address. Depending on the table type set with the parameter nNetAddrTableType when calling NexPlayer.setNetAddrTable, the IP address corresponding to a particular hostname will be used to retrieve host information.

This table can be used as a fallback option (NETADDR\_TABLE\_FALLBACKtype) to retrieve host information, or it can be used to override (NETADDR\_TABLE\_OVERRIDEtype) the information in the existing host database.

A maximum of 5 entries can be assigned to a table.

**Parameters**

| Name  | Description  | 
|---|---|
| hostname | The hostname as aString.|  
| address | The custom IP address corresponding to the hostname set by the developer as aString.|  
 
**Returns**

1 if successful, otherwise 0.
 
#### final int NETADDR\_TABLE\_FALLBACK = 1 [static]

This is a possible table type for the method setNetAddrTable.

When the parameter `nNetAddrTableType` in `NexPlayer.setNetAddrTable` is set to this table type, the method will try to retrieve the host information from the existing host database using the given hostname. If this fails, the method will check the table registered as the parametertableto retrieve the custom IP address corresponding to the given hostname.

In other words, this means that the table of net addresses can be used as a fallback option when the needed host information cannot be retrieved.
 
#### final int NETADDR\_TABLE\_OVERRIDE = 0 [static]

This is a possible table type for the methodsetNetAddrTable.

When the parameter nNetAddrTableType in NexPlayer.setNetAddrTableis set to this table type, the method will try to get the host information using the hostname and its corresponding custom IP address, set by the developer, from the table registered as the parameter table. If this fails, the player will try to get the host information from the existing host database.

In other words, this means that the information in the table registered will be used with priority, overriding the information from the existing host database.
 
### NexOfflineStoreController Class Reference

The new offline playback feature is an expansion, which is a better way of saving and managing the data required for offline playback storing than a database.

**Classes**

- `interface IOfflineStoreListener`
    
	This interface allows the application to get events about the Offline Store from NexOfflineStoreController.
    
- `enum NexOfflineStoreSetting`
    
    The parameters needed for the offline storing are defined as follows.

**Static Public Attributes**

- static final int **MEDIA\_TYPE\_AUDIO** = 0x00
- static final int **MEDIA\_TYPE\_VIDEO** = 0x01
- static final int **MEDIA\_TYPE\_TEXT** = 0x02

**See Also**

Section How to store HLS content for more details.
 
#### NexOfflineStoreController(NexPlayer player, Context context)

Constructor for NexOfflineStoreController.

To use the storing feature of new offline playback, the user must create an instance of NexOfflineStoreController.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | NexPlayer instance.|  
| context | The current context; from `Activity` subclasses, you can just passthis.| 


#### static int deleteOfflineCache (File storedInfoFile) [static]

This method deletes the cache directory files and then the stored info files.

**Parameters**

| Name  | Description  | 
|---|---|
| storedInfoFile | The file descriptor of the info file created from storing.|  
 
**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### static int deleteOfflineCache (String storedInfoFilePath) [static]

This method deletes the cache directory files and then the stored info files.

**Parameters**

| Name  | Description  | 
|---|---|
| storedInfoFilePath | The absolute path of the stored info file.|   
 
**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### int pauseOfflineStore ()

This method pauses storing.

If `IOfflineStoreListener` is already registered, `offlineStorePaused` callback is called when the Offline Store is paused.

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### int resumeOfflineStore ()

This method resumes storing from where it paused.

If IOfflineStoreListener is already registered, offlineStoreResumed callback is called when the Offline Store is resumed.

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### void setListener (IOfflineStoreListener l)

The user must register IOfflineStoreListener in NexOfflineStoreController in order for the application to get Offline Store events.

The application must call setListener before calling startOfflineStore.

**Parameters**

| Name  | Description  | 
|---|---|
| l | The callback to be invoked.|   
 
#### void setOfflineStoreSetting (NexOfflineStoreSetting setting, int value)

This method sets the setting values needed for storing.

Settings that are not customized will be set to default values. The user must call this method before calling startOfflineStore(), but settings will be ignored for Continue Store and Retrieve.

**Parameters**

| Name  | Description  | 
|---|---|
| setting | The NexOfflineStoreSetting to set.|   
| value | The new integer value for the NexOfflineStoreSetting.|    
 
#### void setOfflineStoreSetting (NexOfflineStoreSetting setting, String value)

This method sets the setting values needed for storing.

Settings that are not customized will be set to default values. The user must call this method before calling startOfflineStore(), but settings will be ignored for Continue Store and Retrieve.

**Parameters**

| Name  | Description  | 
|---|---|
| setting | The NexOfflineStoreSetting to set.|   
| value | The new String value for the NexOfflineStoreSetting.|    
 
#### int startOfflineStore (String url, String storedInfoFilePath, int transportType)

This method starts Offline storing.

If `IOfflineStoreListener` is already registered, offlineStoreStarted callback is called when the Offline Store is started.

**Parameters**

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>url</th>
  <td>The URL to store.</td>
</tr>
<tr>
  <th>storedInfoFilePath</th>
  <td>The absolute path of the stored info file.</td>
</tr>
<tr>
  <th rowspan="3">transportType</th>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_TCP</td></tr>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_UDP</td></tr>
</tr>
</table> 
 

**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### int startOfflineStore (String url, String storedInfoFilePath, int transportType, Map <String, String> optionalHeaders)

This method starts Offline storing.

If IOfflineStoreListener is already registered, offlineStoreStarted callback is called when the Offline Store is started.

**Parameters**
<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>url</th>
  <td>The URL to store.</td>
</tr>
<tr>
  <th>storedInfoFilePath</th>
  <td>The absolute path of the stored info file.</td>
</tr>
<tr>
  <th rowspan="3">transportType</th>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_TCP</td></tr>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_UDP</td></tr>
</tr>
<tr>
  <th>optionalHeaders</th>
  <td>Optional Headers for the license request.</td>
</tr>
</table> 
 
**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.

#### int startOfflineStore (String url, String storedInfoFilePath, int transportType, Map <String, String> optionalHeaders, List <String> httpHeaders)

This method starts Offline storing.

If IOfflineStoreListener is already registered, offlineStoreStarted callback is called when the Offline Store is started.

**Parameters**
<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>url</th>
  <td>The URL to store.</td>
</tr>
<tr>
  <th>storedInfoFilePath</th>
  <td>The absolute path of the stored info file.</td>
</tr>
<tr>
  <th rowspan="3">transportType</th>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_TCP</td></tr>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_UDP</td></tr>
</tr>
<tr>
  <th>optionalHeaders</th>
  <td>Optional Headers for the license request.</td>
</tr>
<tr>
  <th>httpHeaders</th>
  <td>Http Headers for the rest of the requests.</td>
</tr>
</table>  

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### int startOfflineStore (FileDescriptor storedInfoFD, int transportType)

This method starts storing from where it left off based on the stored info file.

This will start storing where it left off, so changing the setting to setOfflineStoreSetting will not have any effect. If IOfflineStoreListener is already registered, offlineStoreStarted callback is called when the Offline Store is started.

**Parameters**
<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>storedInfoFD</th>
  <td>The file descriptor of the info file created from storing.</td>
</tr>
<tr>
  <th rowspan="3">transportType</th>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_TCP</td></tr>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_UDP</td></tr>
</tr>
</table>  

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### int startOfflineStore (String storedInfoFilePath, int transportType, Map< String, String> optionalHeaders)

This method starts storing from where it left off based on the stored info file.

This will start storing where it left off, so changing the setting to setOfflineStoreSetting will not have any effect. If
IOfflineStoreListener is already registered, offlineStoreStarted callback is called when the Offline Store is started.

**Parameters**
<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>storedInfoFilePath</th>
  <td>The absolute path of the stored.</td>
</tr>
<tr>
  <th rowspan="3">transportType</th>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_TCP</td></tr>
  <tr><td>NEXPLAYER_TRANSPORT_TYPE_UDP</td></tr>
</tr>
<tr>
  <th>optionalHeaders</th>
  <td>Optional Headers for the license request.</td>
</tr>
</table>   
 
**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### int stopOfflineStore()

This method stops storing.

When stopOfflineStore is called, data will be written in the stored info file, so this means the user must call this method after executing startOfflineStore. If IOfflineStoreListener is already registered, offlineStoreStopped callback is called when the Offline Store is stopped.

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
### NexOfflineStoreController.NexOfflineStoreSetting Enum Reference

The parameters needed for the offline storing are defined as follows.

#### INTEGER\_AUDIO\_STREAM\_ID

Possible key value for key parameter of `setOfflineStoreSetting( NexOfflineStoreSetting , int)`. This stores the audio stream that matches the set stream ID. If there is none, it stores the default stream. If you want to store all audio streams, set the value to STREAM\_ID\_ALL.

**Default value** : NexPlayer.MEDIA\_STREAM\_DEFAULT\_ID
 
#### INTEGER\_BANDWIDTH

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , int). This stores the nearest track to the set bandwidth. 

**Unit** : bps,  **Default value** : 3000000

#### INTEGER\_CUSTOM\_ATTRIBUTE\_ID

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , int).

This stores the custom attribute stream that matches the set stream ID. If there is none, it stores the default stream.

**Default value** : NexPlayer.MEDIA\_STREAM\_DEFAULT\_ID
 
#### INTEGER\_DRM\_TYPE

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , int).

This sets the DRM type whitch using MediaDrm interface or SW WideVine DRM module. Possible Values: 0 : No
DRM 1 : Usng Android MediaDrm interface 2 : Using SW WideVine CDM 3 : Using Automatic selection of SW/HW
WideVine Drm

**Default value** : 0

#### INTEGER\_TEXT\_STREAM\_ID

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , int).

This stores the text stream that matches the set stream ID. If there is none, it stores the default stream.

If you want to store all text streams, set the value to STREAM\_ID\_ALL.

**Default value** : NexPlayer.MEDIA\_STREAM\_DEFAULT\_ID
 
#### INTEGER\_VIDEO\_STREAM\_ID

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , int).

This stores the video stream that matches the set stream ID. If there is none, it stores the default stream.

If you want to store all video streams, set the value to STREAM\_ID\_ALL.

**Default value** : NexPlayer.MEDIA\_STREAM\_DEFAULT\_ID
 
#### static final int STREAM\_ID\_ALL = -3 [static]

Possible value forvalueparameter of setOfflineStoreSetting( NexOfflineStoreSetting , int).

If you want to store all streams of specific type, set the value to STREAM\_ID\_ALL.

Example:

```java
//This will store all audio streams.
setOfflineStoreSetting( INTEGER_AUDIO_STREAM_ID , STREAM_ID_ALL ) 
```

#### STRING\_MEDIA\_DRM\_KEY\_SERVER\_URL

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , String).

The URL of the Key Server. The user must adjust the settings to store media DRM content.

**Default value** : NULL
 
#### STRING\_OFFLINE\_KEY\_ID

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , String).

For offline playback in the future, the user must pass the keyID created with onOfflineKeyStoreListener to NexPlayer.

**See Also**

How to Store Media DRM Content in the document.

**Default value** : NULL
 
#### STRING\_PREFER\_LANGUAGE\_AUDIO

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , String).

This sets the audio language to store. If INTEGER\_AUDIO\_STREAM\_ID has a set value, this value will be ignored.

**Default value** :NULL
 
#### STRING\_PREFER\_LANGUAGE\_TEXT

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , String).

This sets the text language to store. INTEGER\_TEXT\_STREAM\_ID has a set value, this value will be ignored.
 
**Default value** :NULL
 
#### STRING\_STORE\_PATH

Possible key value forkeyparameter of setOfflineStoreSetting( NexOfflineStoreSetting , String).

This sets the directory to save the cache file.

**Default value** : 

`Environment.getExternalStorageDirectory().getPath() + File.separator + "NexPlayerCache" + File.separator`
 
### NexPictureTimingInfo Class Reference

This class allows NexPlayer™ to handle SEI picture timing information in H.264 content.

In summary, this class passes timing information about each video frame in H.264 content if the content provides SEI picture timing information. NexPlayer™ passes an instance of this class through the onPictureTimingInfo listener.

In most cases, this information will include `mFullTimestampFlag`, `mSeconds`, `mMinutes`, and `mHours`. But also note that `mSeconds`, `mMinutes`, and `mHours` are valid **only** if `mFullTimestampFlag` is `1`.

For more in depth information about SEI picture timing information, please see the H.264 specifications.

**See Also**
 
NexPlayer.IListener.onPictureTimingInfo for more information.
 
#### NexPictureTimingInfo(int clockTimeStampFlag, int ctType,int nuitFieldBasedFlag, int countingType, int FullTimeStampFlag, int discontinuityFlag, int countDroppedFlag, int nFrames, int seconds, int minutes, int hours, int timeOffset)

This provides the SEI picture timing information for H.264 content being played.

**Parameters**

| Name | Description | 
|---|---|
| clockTimeStampFlag | The clock timestamp flag in SEI picture timing information for H.264 content, as an integer. |   
| ctType |  The scan type of the source material in SEI picture timing information for H.264 content, as an integer. |    
| nuitFieldBasedFlag | The nuit\_field\_based\_flag value in SEI picture timing information for H.264 content.|   
| countingType | The counting\_type value in SEI picture timing information for H.264 content.|   
| FullTimeStampFlag | The full\_timestamp\_flag value in SEI picture timing information for H.264 content.|    
| discontinuityFlag | The discontinuity\_flag value in SEI picture timing information for H.264 content.|     
| countDroppedFlag | The cnt\_dropped\_flag value in SEI picture timing information for H.264 content.|
| nFrames | The n\_frames value in SEI picture timing information for H.264 content.|     
| seconds | The seconds\_value in SEI picture timing information for H.264 content.|     
| minutes | The minutes\_value in SEI picture timing information for H.264 content.|     
| hours | The hours\_value in SEI picture timing information for H.264 content.|     
| timeOffset | The time\_offset value in SEI picture timing information for H.264 content.|     
 
#### int mClockTimeStampFlag

This is the clock timestamp flag of SEI picture timing information in H.264 content.

**Values:**

- 1 : Indicates that several clock timestamp syntax elements are present and follow immediately.
- 0 : Indicates that the related clock timestamp elements are **present**.
 
#### int mCountDroppedFlag

This is the cnt\_dropped\_flag value in SEI picture timing information in H.264 content.

Based on the counting method set by mCountingType, this value specifies that one or more values of mNFrames should be skipped.
 
#### int mCountingType

This is the counting\_type value in SEI picture timing information in H.264 content.

It indicates the method of dropping values of the n\_framesin SEI picture timing information.

**Values:**

- 0 : no dropping of `n_framescount` values and no use of `time_offset`
- 1 : no dropping of `n_framescount` values
- 2 : dropping of individual zero values of `n_frames` count
- 3 : dropping of individual `MaxFPS-1` values of `n_frames` count
- 4 : dropping of the two lowest (value 0 and 1) `n_frames` counts when `seconds_value` is equal to 0 and `minutes_value` is not an integer multiple of 10
- 5 : dropping of unspecified individual `n_frames` count values
- 6 : dropping of unspecified numbers of unspecified `n_frames` count values
- 7..31 : Reserved.
 
#### int mCtType

This is the scan type of the source material from SEI picture timing information in H.264 content.

**Values:**

- 0 : Original picture scan was progressive.
- 1 : Original picture scan was interlaced.
- 2 : Original picture scan is unknown.
- 3 : Reserved.

#### int mDiscontinuityFlag

This is the `discontinuity_flag` value in SEI picture timing information in H.264 content.

Please see the H.264 specifications for details in how to interpret the values here.

**Values:**

- 0 : Continuous clock timestamps.
- 1 : Discontinuity in clock timestamps.
 
#### int mFullTimestampFlag

This is the `full_timestamp_flag` value in SEI picture timing information in H.264 content.

**Values:**

- 0 : Indicates that the `n_frames` element is followed only by the `seconds_flag`
- 1 : Indicates that a full timestamp is included and that the `n_frames` element is followed by `seconds_value`, `minutes_value`, and `hours_value`.

 
#### int mHours

This is the `hours_value` in SEI picture timing information in H.264 content.

**Values:** 0 to 23 (inclusive)
 
#### int mMinutes

This is the `minutes_value` in SEI picture timing information in H.264 content.

**Values:** 0 to 59 (inclusive)

#### int mNFrames

This is the `n_frames` value in SEI picture timing information in H.264 content.

It is used to determine the clock timestamp and is a frame-based counter.

#### int mNuitFieldBasedFlag

This is the `nuit_field_based_flag` in SEI picture timing information in H.264 content.

This value can be used to calculate the clock timestamp of H.264 video frames.
 
#### int mSeconds

This is the `seconds_value` in SEI picture timing information in H.264 content.

**Values:** 0 to 59 (inclusive)

#### int mTimeOffset

This is the `time_offset` value in SEI picture timing information in H.264 content.

It can be used to determine the clock timestamp.

### NexPlayer Class Reference

The primary interface to the NexPlayer™ engine.

For details on usage, see the NexPlayer™ Engine package documentation.

**Classes**

- `interface IDynamicThumbnailListener`

    This interface must be implemented in order for the application to receive Dynamic Thumbnail events from NexPlayer™.

- `interface IHTTPABRTrackChangeListener`

    This interface must be implemented in order for the application to receive an ABR Track switch event from NexPlayer™.

- `interface IListener`
    
    The application must implement this interface in order to receive events from NexPlayer™.

- `interface IMetaDataEventListener`

- `interface IOfflineKeyListener`

- `interface IReleaseListener`
    
    This interface can be implemented in an application in order to receive NexPlayer™ release events from NexPlayer™.

- `interface IVideoRendererListener`
    
    The application must implement this interface in order to receive video renderer-specific events from NexPlayer™.

- `class NexDRMInitInfo`

- `enum NexErrorCategory`
    
    This enum defines the categories for errors.

- `enum NexErrorCode`
	
	Possible error codes that NexPlayer™ can return.
 
- `enum NexProperty`
    
    This enumerator defines the possible properties that can be set on a NexPlayer™ instance.

- `class NexRTStreamInformation`

- `enum OfflineMode`

- `class PROGRAM_TIME`

    This class handles the date and time information included in the #EXT-X-PROGRAM-DATE-TIME tag in HLS content.

**Static Public Attributes**

- `static final int NEXPLAYER_SIGNAL_STATUS_NORMAL = 0`

    Normal signal status; see onSignalStatusChanged for details.

- `static final int NEXPLAYER_SIGNAL_STATUS_WEAK = 1`

    Weak signal status; see onSignalStatusChanged for details.

- `static final int NEXPLAYER_SIGNAL_STATUS_OUT = 2`

    No signal (out of service area); see onSignalStatusChanged for details.

- `static final int NEXPLAYER_ASYNC_CMD_NONE = 0x00000000`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_OPEN_LOCAL = 0x00000001`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_OPEN_STREAMING = 0x00000002`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_OPEN_TV = 0x00000003`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_START_LOCAL = 0x00000005`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_START_STREAMING = 0x00000006`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_START_TV = 0x00000007`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_STOP = 0x00000008`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_PAUSE = 0x00000009`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_RESUME = 0x0000000A`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_SEEK = 0x0000000B`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_STEP_SEEK = 0x0000000C`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_SETEXTSUBTITLE = 0x0000000F

- `static final int NEXPLAYER_ASYNC_CMD_RECORD_START = 0x0000001A`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_RECORD_STOP = 0x0000001B`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_RECORD_PAUSE = 0x0000001C`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_RECORD_RESUME = 0x0000001D`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_REINITVIDEO = 0x00000013`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_TIMESHIFT_CREATE = 0x00000021`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_TIMESHIFT_DESTROY = 0x00000022`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_TIMESHIFT_PAUSE = 0x00000023`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_TIMESHIFT_RESUME = 0x00000024`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_TIMESHIFT_FORWARD = 0x00000025`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_TIMESHIFT_BACKWARD = 0x00000026`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_FASTPLAY_START = 0x00000027`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_FASTPLAY_STOP = 0x00000028`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_SET_MEDIA_STREAM = 0x00000031`

    Possible value for command parameter of onAsyncCmdComplete.
    
- `static final int NEXPLAYER_ASYNC_CMD_SET_MEDIA_TRACK = 0x00000032`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_SET_MEDIA_STREAM_TRACK = 0x00000033`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXDOWNLOADER_ASYNC_CMD_OPEN = 0x00200001`

    Possible value for msg parameter of onDownloaderAsyncCmdComplete.

- `static final int NEXDOWNLOADER_ASYNC_CMD_CLOSE = 0x00200002`

    Possible value for msg parameter of onDownloaderAsyncCmdComplete.

- `static final int NEXDOWNLOADER_ASYNC_CMD_START = 0x00200003`

    Possible value for msg parameter of onDownloaderAsyncCmdComplete.

- `static final int NEXDOWNLOADER_ASYNC_CMD_STOP = 0x00200004`

    Possible value for msg parameter of onDownloaderAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_OPEN_STORE_STREAM = 0x00000101`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_ASYNC_CMD_START_STORE_STREAM = 0x00000102`

    Possible value for command parameter of onAsyncCmdComplete.

- `static final int NEXPLAYER_SOURCE_TYPE_LOCAL_NORMAL = 0`

    Treats path as a local media file; a possible value for the type parameter of NexPlayer.open.

- `static final int NEXPLAYER_SOURCE_TYPE_STREAMING = 1`

    Treats path as a URL to a streaming media source; a possible value for the type parameter of NexPlayer.open.

- `static final int NEXPLAYER_SOURCE_TYPE_STORE_STREAM = 2`

    Treats path as a URL to a streaming media source to be stored for offline playback; a possible value for the `type` parameter of NexPlayer.open.

- `static final int NEXPLAYER_TRANSPORT_TYPE_TCP = 0`

    Use TCP as the transport; possible value for the NexPlayer.open method.

- `static final int NEXPLAYER_TRANSPORT_TYPE_UDP = 1`

    Use UDP as the transport; possible value for the NexPlayer.open method.

- `static final int NEXPLAYER_TRACK_ENABLE_OPTION_DISABLED_TEMPORARY = 1`

    possible value for the NexPlayer.enableTrack method

- `static final int NEXPLAYER_TRACK_ENABLE_OPTION_DISABLED_PERFORMANCE = 2`

    Enable the track which is disabled by performance issues; possible value for the NexPlayer.enableTrack method.

- `static final int NEXPLAYER_STATE_NONE = 0`

    No state information available for NexPlayer™ (this is the state after release has been called); a possible return value of NexPlayer.getState.

- `static final int NEXPLAYER_STATE_CLOSED = 1`

    No media source is open (this is the state when the NexPlayer™ instance is initially created, and after close has completed); a possible return value of getState.

- `static final int NEXPLAYER_STATE_STOP = 2`

    A media source is open but is currently stopped (this is the state after open or stop has completed); a possible return value of getState.

- `static final int NEXPLAYER_STATE_PLAY = 3`

    A media source is open and playing (this is the state after start has completed); a possible return value of getState.

- `static final int NEXPLAYER_STATE_PAUSE = 4`

    A media source is open but has been paused (this is the state after pause has completed); a possible return value of getState.

- `static final int NEXPLAYER_STATE_PLAYxN = 5`

    A media source is open and fast playing(this is the state after start has completed); a possible return value of getState.

- `static final int CONTENT_INFO_INDEX_MEDIA_TYPE = 0`

    A possible argument value for getContentInfoInt.

- `static final int CONTENT_INFO_INDEX_MEDIA_DURATION = 1`

    A possible argument value for getContentInfoInt.
    

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC = 2`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_WIDTH = 3`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_HEIGHT = 4`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_FRAMERATE = 5`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_BITRATE = 6`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_AUDIO_CODEC = 7`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_AUDIO_SAMPLINGRATE = 8`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_AUDIO_NUMOFCHANNEL = 9`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_AUDIO_BITRATE = 10`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_MEDIA_ISSEEKABLE = 11`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_MEDIA_ISPAUSABLE = 12`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_FOURCC = 13`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC_CLASS = 14`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_PROFILE = 15`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_LEVEL = 16`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC_ERROR = 17`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_RENDER_AVE_FPS = 1000`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_RENDER_AVE_DSP = 1001`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_RENDER_COUNT = 1002`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_RENDER_TOTAL_COUNT = 1003`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC_DECODING_COUNT = 1004`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC_DECODING_TOTAL_COUNT = 1005`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC_AVG_DECODE_TIME = 1006`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC_AVG_RENDER_TIME = 1007`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC_DECODE_TIME = 1008`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_CODEC_RENDER_TIME = 1009	 
    
    A possible argument value for getContentInfoInt.
 
 - static final int CONTENT_INFO_INDEX_VIDEO_AVG_BITRATE = 1010`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_FRAMEBYTES = 1011`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_AUDIO_AVG_BITRATE = 1012`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_AUDIO_FRAMEBYTES = 1013`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_FRAME_COUNT = 1014`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_TOTAL_FRAME_COUNT = 1015`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_VIDEO_TOTAL_SKIP_COUNT = 1016`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_SPD_CURRENT_SYNC_DIFF = 1017`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_TOTAL_BUFFERING_TIME = 2000`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_MEDIA_OPEN_TIME = 2001`

    A possible argument value for getContentInfoInt.

-  `static final int CONTENT_INFO_INDEX_MEDIA_START_TIME = 2002`

    A possible argument value for getContentInfoInt.

-  `static final int NEXPLAYER_BUFINFO_INDEX_BUFSIZE = 0x0`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_INITBUFSIZE = 0x1`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_INITBUFTIME = 0x2`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_BUFFEREDSIZE = 0x3`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_BUFRATE = 0x4`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_FIRSTCTS = 0x5`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_LASTCTS = 0x6`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_DURATION = 0x7`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_FRAMECOUNT = 0x8`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_BUFINFO_INDEX_STATE = 0x9`

    A possible argument value for getBufferInfo.

-  `static final int NEXPLAYER_STATUS_REPORT_NONE = 0x0`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_AUDIO_GET_CODEC_FAILED = 0x1`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_VIDEO_GET_CODEC_FAILED = 0x2`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_AUDIO_INIT_FAILED = 0x3`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_VIDEO_INIT_FAILED = 0x4`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_TRACK_CHANGED = 0x5`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_STREAM_CHANGED = 0x6`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_DSI_CHANGED = 0x7`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_OBJECT_CHANGED = 0x8`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_CONTENT_INFO_UPDATED = 0x9`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_AVMODE_CHANGED = 0xa`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_HTTP_INVALID_RESPONSE = 0xb`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_DISCONTINUITY_EXIST = 0x12`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_EXTERNAL_DOWNLOAD_CANCELED = 0x20`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED = 0x21`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_STREAM_RECV_PAUSE = 0x60`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_STREAM_RECV_RESUME = 0x61`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_DOWNLOAD_PROGRESS = 0x80`

    Possible value for msg parameter of onStatusReport.

-  `static final int NEXPLAYER_STATUS_REPORT_MAX = 0xFFFFFFFF`

    Possible value for msg parameter of onStatusReport.

-  `static final String NEX_DEVICE_USE_AUTO = "Auto"`

    A possible value for the strRenderMode parameter of NexALFactory.init.

-  `static final String NEX_DEVICE_USE_ONLY_ANDROID = "Android"`

    A possible value for the strRenderMode parameter of NexALFactory.init.

-  `static final String NEX_DEVICE_USE_JAVA = "JAVA"`

    A possible value for the strRenderMode parameter of NexALFactory.init.

-  `static final String NEX_DEVICE_USE_OPENGL = "OPENGL"`

    A possible value for the strRenderMode parameter of NexALFactory.init.

-  `static final String NEX_DEVICE_USE_ANDROID_3D = "Android 3D"`

    A possible value for the strRenderMode parameter of NexALFactory.init.

-  `static final int NEX_AS_EARCOMFORT = 0x00000001`

    One of the NexSound audio modes to be set by th euiAudioMode parameter in audioSetParam().

-  `static final int NEX_AS_REVERB = 0x00000002`

    One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

-  `static final int NEX_AS_STEREO_CHORUS = 0x00000003`

    One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

-  `static final int NEX_AS_MUSIC_ENHANCER = 0x00000004`

    One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

-  `static final int NEX_AS_CINEMA_SOUND = 0x00000006`

    One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

-  `static final int NEX_USE_RENDER_AND = 0x00000002 
	
    Possible return value for NexPlayer.GetRenderMode. 

-  `static final int NEX_USE_RENDER_JAVA = 0x00000010`

    Possible return value for NexPlayer.GetRenderMode.

-  `static final int NEX_USE_RENDER_OPENGL = 0x00000020`

    Possible return value for NexPlayer.GetRenderMode.

-  `static final int NEX_USE_RENDER_IOMX = 0x00000040`

    Possible return value for NexPlayer.GetRenderMode.

-  `static final int MEDIA_STREAM_DEFAULT_ID = 0xFFFFFFFF`

    Possible value for arguments to NexPlayer.setMediaStream().

-  `static final int MEDIA_STREAM_DISABLE_ID = 0xFFFFFFFE`

    Possible value for arguments to NexPlayer.setMediaStream().

-  `static final int MEDIA_TRACK_DEFAULT_ID = 0xFFFFFFFF`

    Possible value for arguments to NexPlayer.setMediaTrack().

-  `static final int MEDIA_TRACK_DISABLE_ID = 0xFFFFFFFE`

    Possible value for arguments to NexPlayer.setMediaTrack().

-  `static final int MEDIA_STREAM_TYPE_AUDIO = 0x00`

    Possible value for NexStreamInformation.mType; see there for details.

-  `static final int MEDIA_STREAM_TYPE_VIDEO = 0x01`

    Possible value for NexStreamInformation.mType; see there for details.

-  `static final int MEDIA_STREAM_TYPE_TEXT = 0x02`

    Possible value for NexStreamInformation.mType; see there for details.

-  `static final int MEDIA_TRACK_TYPE_AUDIO = 0x10`

    Possible value for NexStreamInformation.mType; see there for details.

-  `static int RTSP_METHOD_DESCRIBE = 0x00000001`

    This is a possible value for the methods parameter of addRTSPHeaderFields.

-  `static int RTSP_METHOD_SETUP = 0x00000002`

    This is a possible value for the methods parameter of addRTSPHeaderFields.

-  `static int RTSP_METHOD_OPTIONS = 0x00000004`

    This is a possible value for the methods parameter of addRTSPHeaderFields.

-  `static int RTSP_METHOD_PLAY = 0x00000008`

    This is a possible value for the methods parameter of addRTSPHeaderFields.

-  `static int RTSP_METHOD_PAUSE = 0x00000010`

    This is a possible value for the methods parameter of addRTSPHeaderFields.

-  `static int RTSP_METHOD_GETPARAMETER = 0x00000020`

    This is a possible value for the methods parameter of addRTSPHeaderFields.

-  `static int RTSP_METHOD_TEARDOWN = 0x00000040`

    This is a possible value for the methods parameter of addRTSPHeaderFields.

-  `static int RTSP_METHOD_ALL`

    This is a possible value for the methods parameter of addRTSPHeaderFields.

-  `static final int RENDER_MODE_VIDEO_NONE = 0x00000000`

    This is a possible value for the iFlag parameter of setRenderOption.

-  `static final int RENDER_MODE_VIDEO_FILTERBITMAP = 0x00000001`

    This is a possible value for the iFlag parameter of setRenderOption.

-  `static final int RENDER_MODE_VIDEO_DITHERING = 0x00000002`

    This is a possible value for the iFlag parameter of setRenderOption.

-  `static final int RENDER_MODE_VIDEO_ANTIALIAS = 0x00000004`

    This is a possible value for the iFlag parameter of setRenderOption.

-  `static final int RENDER_MODE_VIDEO_ALLFLAG = 0xFFFFFFFF`

    This is a possible value for the iFlag parameter of setRenderOption.

-  `static final int NEXDOWNLOADER_OPEN_TYPE_CREATE = 0`

    This is a possible value for the parameter eType in the method DownloaderOpen().

-  `static final int NEXDOWNLOADER_OPEN_TYPE_APPEND = 1`

    This is a possible value for the parameter eType in the method DownloaderOpen().

-  `static final int NEXDOWNLOADER_STATE_NONE = 0`

    This is a possible value for the parameter param2 of onDownloaderEventState.

-  `static final int NEXDOWNLOADER_STATE_CLOSED = 2`

    This is a possible value for the parameter param2 of onDownloaderEventState.

-  `static final int NEXDOWNLOADER_STATE_STOP = 3`

    This is a possible value for the parameter param2 of onDownloaderEventState.

-  `static final int NEXDOWNLOADER_STATE_DOWNLOAD = 4`

    This is a possible value for the parameter param2 of onDownloaderEventState.

-  `static final int AVAILBITRATES_NONE = 0x00000000`

    This is a possible value for the option parameter in setVideoBitrates(int [ ] bitrates, int option).

-  `static final int AVAILBITRATES_MATCH = 0x00000001`

    This is a possible value for the option parameter in setVideoBitrates(int [ ] bitrates, int option).

-  `static final int AVAILBITRATES_NEAREST = 0x00000002`

    This is a possible value for the option parameter in setVideoBitrates(int [ ] bitrates, int option).

-  `static final int AVAILBITRATES_HIGH = 0x00000003`

    This is a possible value for the option parameter in setVideoBitrates(int [ ] bitrates, int option).

-  `static final int AVAILBITRATES_LOW = 0x00000004`

    This is a possible value for the option parameter in setVideoBitrates(int [ ] bitrates, int option).

-  `static final int AVAILBITRATES_INSIDERANGE = 0x00000005`

    This is a possible value for the option parameter in setVideoBitrates(int [ ] bitrates, int option).

-  `static final int OPTION_DYNAMIC_THUMBNAIL_INTERVAL = 1`

    This is one possible option property for the Dynamic Thumbnail feature in Smooth Streaming content and a possible value of the option parameter of setOptionDynamicThumbnail.

**Protected Attributes**

- `NexClientManager mClientManager`

**Static Protected Attributes**

- `static final int NEXPLAYER_PROPERTY_ENABLE_MEDIA_DRM = 215`
- `static final int NEXPLAYER_STATUS_REPORT_TARGET_BANDWIDTH_CHANGED = 0x22`
    Possible value for `msg` parameter of `onStatusReport`.
- `static final int NEXPLAYER_DEBUGINFO_HTTP_RESPONSE = 0x06`
- `static final int NEXPLAYER_DEBUGINFO_H264_SEI_PICTIMING_INFO = 0x09`
- `static final int NEXPLAYER_DEBUGINFO_HTTP_REQUEST = 0x11`
- `static final int NEXPLAYER_DEBUGINFO_SESSION_DATA = 0x13`
- `static final int NEXPLAYER_DEBUGINFO_DATERAGNE_DATA = 0x14`
- `static final int NEXPLAYER_DEBUGINFO_EMSG_DATA = 0x15`

#### NexPlayer( )

Sole constructor for NexPlayer™.

After constructing a NexPlayer™ object, you must call NexPlayer.init before you can call any other methods

#

#### boolean addEventReceiver (NexEventReceiver receiver)

This method adds aneventreceiver.

> **Note** If the developer wants to register several IListeners, they can register a receiver with this method. If the developer set a listener with NexPlayer.setListener and added event receivers, NexPlayer will use the return value of the listener. If the developer did not set a listener and added only receivers, NexPlayer will use the return value of the last registered event receiver. Events will be forwarded in sequence from receivers to listener.
 
**Parameters**

| Name | Description | 
|---|---|
| receiver | The object to which methods will be called when events occur.|  

**See Also**
 
- NexEventReceiver
- NexPlayer.removeReleaseListener
 
#### native int addHTTPHeaderFields (String str)

This function adds additional header fields to be sent along with the HTTP headers when sending streaming requests (HLS and Smooth Streaming).

The string should contain a single valid HTTP header, and should include the header name, value, and delimiter.

For example:

```java
addHTTPHeaderFields("X-Example: test value.");
```

> **Note** To add multiple header fields, simply call this function multiple times
 
**Parameters**
 
| Name | Description | 
|---|---|
| str | The header (including delimeter) to add to future HTTP requests.|  

**Returns**
 
Zero if successful, non-zero if there was an error.
 
#### int addNexClient (NexClient client)

This method adds a client module to NexPlayer™.

> **Warning** Do not call this method when playing local content. It should only be used for streaming content.  Note that client modules are optional features of the NexPlayer™ SDK. For more information on how to integrate and use a client module available in the SDK (as well as sample code), please see the relevant NexXXXClient class.

**Parameters**

| Name | Description | 
|---|---|
| client | The instance of the client module as aNexClientobject.|   
 
**Returns**

The client ID as an integer if successful, or -1 in the event of failure. Note that if no client module is available in the current version of the SDK, -1 will be returned.
 
**See Also**

- removeNexClient
- getClientStatus
 
#### void addReleaseListener (IReleaseListener listener)

Adds a callback that will be invoked when a NexPlayer™ instance is released.

This is a callback that provides certain minimal functionality. See the NexPlayer.IReleaseListener documentation for more information on implementation.

In an Android application, there are two common ways to implement this. The most typical approach is to have the Activity subclass implement the IReleaseListener interface.

The other approach is to define an anonymous class inline, as follows:

```java
mNexPlayer.addReleaseListener(new NexPlayer.IReleaseListener() {
	@Override
	public void onPlayerRelease(NexPlayer mp) {
	// ...event implementaton goes here...
	}
});
```

**Parameters**

| Name | Description | 
|---|---|
| listener |The object on which methods will be called when the instance of NexPlayer™ is released.| 


> This must implement the IReleaseListener interface.
 
**See Also**

- NexPlayer.IReleaseListener
- NexPlayer.removeReleaseListener
 
#### native int addRTSPHeaderFields (int methods, String str)

This function adds an RTSP header to be included with all future RTSP requests.

RTSP headers have the same format as HTTP headers, but the set of field names is different.

There are several request types that are part of the RTSP protocol, and when a header is added, you must specify with which request types it will be included. This is done by performing a bitwise OR on one or more of the following values, and specifying the result in the methods parameter:

- `RTSP_METHOD_DESCRIBE`
- `RTSP_METHOD_SETUP`
- `RTSP_METHOD_OPTIONS`
- `RTSP_METHOD_PLAY`
- `RTSP_METHOD_PAUSE`
- `RTSP_METHOD_GETPARAMETER`
- `RTSP_METHOD_TEARDOWN`
- `RTSP_METHOD_ALL`

For example, to set a different user agent for the SETUP and PLAY requests:

```java
addRTSPHeaderFields(RTSP_METHOD_SETUP | RTSP_METHOD_PLAY, "User-Agent: NexStreaming Android Player");
```

**Parameters**
 
 
| Name | Description | 
|---|---|
| methods |The set of request methods to which this will apply (RTSP\_METHOD\_∗ constants OR-ed together).| 
| str |The actual header to add (including header name and value).| 

**Returns**
 
Zero if successful, non-zero if there was an error.
 
#### native int audioSetParam (int uiAudioMode, int uiEffectStrength, int uiBassStrength)

This audio effect interface enhances sound on NexPlayer™ but is only available in some product categories.

> **Note** The audio effects available in this interface are optional. The availability of each NexSound audio component can be checked by calling getProperty on the property related to the component to be checked, namely one of:

- `AS_EARCOMFORT_AVAILABILITY (0x00050002)`
- `AS_REVERB_AVAILABILITY (0x00050003)`
- `AS_STEREO_CHORUS_AVAILABILITY (0x00050004)`
- `AS_MUSIC_ENHANCER_AVAILABILITY (0x00050005)`
- `AS_CINEMA_SOUND_AVAILABILITY (0x00050006)`

**Parameters**
 
| Name | Description | 
|---|---|
|uiEffectStrength| This sets the strength of the audio mode selected. It is an integer between 0 and 6.|
|uiBassStrength| This sets the bass strength of the audio mode selected. It is an integer between 0 and 6.|
| uiAudioMode |The NexSound mode to set. This is an integer and will be one of:|

- `NEX_AS_EARCOMFORT = 0x00000001` : EarComfort mode moves the sound image to a position outside of the listener’s head, simulating the more comfortable feeling of listening to speakers but through earphones.
	- Default Values :
		- uiEffectStrength = 2
		- uiBassStrength = 3
- `NEX_AS_REVERB = 0x00000002` : Reverb mode adds reverb to audio. 
	- Default Values :
		- uiEffectStrength = 3
		- uiBassStrength = 3
- `NEX_AS_STEREO_CHORUS = 0x00000003` : Stereo Chorus mode. 
	- Default Values :
		- uiEffectStrength = 5 
		- uiBassStrength = 3
- `NEX_AS_MUSIC_ENHANCER = 0x00000004` : Music Enhancer mode. 
	- Default Values :
		- uiEffectStrength = 6 
		- uiBassStrength = 5
- `NEX_AS_CINEMA_SOUND = 0x00000006` : Virtual surround sound effect on ordinary earphones. This mode can only be turned ON and OFF and parameters `uiEffectStrength` and `uiBassStrength` do not apply.
 
**Returns**

Zero if successful, or a non-zero error code, including:
 
- `NOT_SUPPORT (0x8000000FL)` : The requested NexSound audio mode is not supported in this version.

#### native int captureVideo (int iCount, int iInterval)

This function begins capturing video frames.

This may be used to capture a single frame immediately, or to capture a series of frames at regular intervals. In either case, the captured frames are actually sent to the onVideoRenderCapture handler, so your application must implement it to receive the frames.

When this function is called, the current frame will immediately be sent toonVideoRenderCapture, and then
any scheduled frames will be sent after the specified interval has elapsed.

> **Warning** captureVideo is NOT supported.
 
**Parameters**

| Name | Description | 
|---|---|
| iCount |The number of frames to capture; this should be at least 1 or the method has no effect.| 
| iInterval | If `iCount` is greater than 1, this is the number of milliseconds to wait between captures. For example, if `iCount` is 3 and `iInterval` is 100, then one frame will be captured immediately, another after 1/10sec, and a third after a further 1/10sec.| 
 
**Returns**
 
Zero if successful, non-zero if there was an error.
 
#### int changeMaxBandWidth (int iMaxBandWidth)

This method sets the maximum bandwidth for streaming playback dynamically during playback.

> **Warning** It is recommended that the method `NexABRController::changeMaxBandWidth()` be used to set
maximum bandwidth allowed instead of using this method.

> **Note** To dynamically change the maximum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the maximum bandwith can also be set before play begins by setting the `NexProperty,MAX_BW`, with `NexPlayer.setProperty(MAX_BW)`.
 
This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track over the maximum bandwidth when determining whether a track change is appropriate, even if it detects more bandwidth available.

If this method returns successfully, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED` Then, if the method `onStatusReport()` returns successfully, the maximum bandwidth will be changed.

Note that to remove a maximum that has been set with this method (so that NexPlayer™ will again consider all tracks regardless of bandwidth), set iMaxBandWidth to 0x00000000.

**Parameters**

| Name | Description | 
|---|---|
| iMaxBandWidth | Maximum bandwidth in kbps (kilobits per second). To reset to no maximum bandwidth, set iMaxBandWidth = 0x00000000.| 
 
**Returns**
 
Zero if successful, otherwise non-zero if there was an error.
 
**See Also**
 
NexABRController::changeMaxBandWidth()
 
 
#### native int changeMaxBandWidthBps (int maxBwBps)

This method sets the maximum bandwidth for streaming playback dynamically during playback.

> **Warning** It is recommended that the method `NexABRController::changeMaxBandWidth()` be used to set
maximum bandwidth allowed instead of using this method.
 
> **Note** To dynamically change the maximum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the maximum bandwith can also be set before play begins by setting the `NexProperty,MAX_BW`, with `NexPlayer.setProperty(MAX_BW)`.
 
This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track over the maximum bandwidth when determining whether a track change is appropriate, even if it detects more bandwidth available.

If this method returns successfully, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED` Then, if the method `onStatusReport()`
returns successfully, the maximum bandwidth will be changed.

Note that to remove a maximum that has been set with this method (so that NexPlayer™ will again consider all
tracks regardless of bandwidth), set `maxBwBps` to `0x00000000`.

**Parameters**

| Name | Description | 
|---|---|
| maxBwBps | Maximum bandwidth in bps (bits per second). To reset to no maximum bandwidth, set maxBwBps = 0x00000000.| 
 
**Returns**

Zero if successful, otherwise non-zero if there was an error.
 
**See Also**
 
NexABRController::changeMaxBandWidth()
  
#### native int changeMaxResolution (int maxWidth, int maxHeight)

This method changes the maxWidth and maxHeight while playing content.

This only works on HLS content, and switching to a track with bigger maxWidth and maxHeight will not be possible. If the currently playing track has width and height values bigger than maxWidth and maxHeight, it will switch to a track with smaller than those.

**Parameters**

 
| Name | Description | 
|---|---|
| maxWidth | Maximum width.| 
| maxHeight | Maximum height.| 
 
**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.

 
#### int changeMinBandWidth (int iMinBandWidth)

This method sets the minimum bandwidth for streaming playback dynamically during playback.

> **Warning** It is recommended that the method `NexABRController::changeMinBandWidth()` be used to set
minimum bandwidth allowed instead of using this method.
 
> **Note** To dynamically change the minimum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the minimum bandwith can also be set before play begins by setting the `NexProperty,MIN_BW`, with `NexPlayer.setProperty(MIN_BW)`.
 
This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum bandwidth when determining whether a track change is appropriate, even if it detects less bandwidth available.

If this method returns successfully, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED`. Then, if the method `onStatusReport()` returns successfully, the minimum bandwidth will be changed.

Note that to remove a minimum that has been set with this method (so that NexPlayer™ will again consider all tracks regardless of bandwidth), set `iMinBandWidth` to `0x00000000`.

**Parameters**

| Name | Description | 
|---|---|
| iMinBandWidth | Minimum bandwidth in kbps (kilobits per second). To reset to no minimum bandwidth, set iMinBandWidth = 0x00000000.| 
 
**Returns**
 
Zero if successful, otherwise non-zero if there was an error.
 
**See Also**
 
NexABRController::changeMinBandWidth()
 
#### native int changeMinBandWidthBps(int minBwBps)

This method sets the minimum bandwidth for streaming playback dynamically during playback.

> **Warning** It is recommended that the method NexABRController::changeMinBandWidth() be used to set
minimum bandwidth allowed instead of using this method.
 
> **Note** To dynamically change the minimum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the minimum bandwith can also be set before play begins by setting the `NexProperty.MIN_BW`, with `NexPlayer.setProperty(MIN_BW)`.
 
This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum bandwidth when determining whether a track change is appropriate, even if it detects less bandwidth available.

If this method returns successfully, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED`. Then, if the method `onStatusReport()` returns successfully, the minimum bandwidth will be changed.

Note that to remove a minimum that has been set with this method (so that NexPlayer™ will again consider all tracks regardless of bandwidth), set `minBwBps` to `0x00000000`.

**Parameters**

| Name | Description | 
|---|---|
| minBwBps | Minimum bandwidth in bps (bits per second). To reset to no minimum bandwidth, set minBwBps = 0x00000000| 
 
**Returns**

Zero if successful, otherwise non-zero if there was an error.
 
**See Also**
 
NexABRController::changeMinBandWidth()
 
#### int changeMinMaxBandWidth (int iMinBandWidth, int iMaxBandWidth)

This method sets the minimum and maximum bandwidth for streaming playback dynamically during playback.

> **Warning** It is recommended that the method `NexABRController::changeMinMaxBandWidth()` be used to
set minimum and maximum bandwidths allowed instead of using this method. To dynamically change the minimum and maximum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the minimum, and maximum bandwith can also be set before play begins by setting the NexProperty `MAX_BW`, with `NexPlayer.setProperty(MAX_BW)`. `MIN_BW`, with `NexPlayer.setProperty(MIN_BW)`.
 
This applies in cases where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum, and over the maximum bandwidth when determining whether a track change is appropriate, even if it detects less, and more bandwidth available.

If this method returns success, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED` Then, if the method `onStatusReport()` returns success, the minimum and maximum bandwidth will be changed.

Note that to remove a minimum and maximum that has been set with this method (so that NexPlayer™ will
again consider all tracks regardless of bandwidth), set both of iMinBandWidth, and iMaxBandWidthto
0x00000000.

**Parameters**

| Name | Description | 
|---|---|
| iMinBandWidth | Minimum bandwidth in kbps (kilobits per second). To reset to no minimum bandwidth, iMinBandWidth= 0x00000000|
| iMaxBandWidth | Maximum bandwidth in kbps (kilobits per second). To reset to no maximum bandwidth, iMaxBandWidth= 0x00000000| 
 
**Returns**
 
Zero if successful, otherwise non-zero if there was an error.
 
**See Also**
 
NexABRController::changeMinMaxBandWidth()
 
#### native int changeMinMaxBandWidthBps (int minBwBps, int maxBwBps)

This method sets the minimum and maximum bandwidth for streaming playback dynamically during playback.

> **Warning** It is recommended that the method `NexABRController::changeMinMaxBandWidth()` be used to
set minimum and maximum bandwidth values instead of using this method.
 
> **Note** To dynamically change the minimum and maximum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the minimum, and maximum bandwith can also be set before play begins by setting the NexProperty, `MAX_BW`, with `NexPlayer.setProperty(MAX_BW)`. `MIN_BW`, with `NexPlayer.setProperty(MIN_BW)`.
 
This applies in cases where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum, and over the maximum bandwidth when determining whether a track change is appropriate, even if it detects less, and more bandwidth available.

If this method returns success, the method onStatusReport() will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED` Then, if the method `onStatusReport()` returns success, the minimum and maximum bandwidth will be changed.

Note that to remove a minimum and maximum that has been set with this method (so that NexPlayer™ will again
consider all tracks regardless of bandwidth), set both of `minBwBps`, and `maxBwBps` to `0x00000000`.

**Parameters**

| Name | Description | 
|---|---|
| minBwBps | Minimum bandwidth in bps (bits per second). To reset to no minimum bandwidth, minBwBps = 0x00000000|
| maxBwBps | Maximum bandwidth in bps (bits per second). To reset to no maximum bandwidth, maxBwBps= 0x00000000| 
 
**Returns**

Zero if successful, otherwise non-zero if there was an error.
 
**See Also**

NexABRController::changeMinMaxBandWidth()
 
#### int changeSubtitleFD (AssetFileDescriptor afd)

Open the caption resource file which is attached in "res/raw" or "assets" folder.

Access should be provided by AssetFileDescriptor. Length and Offset will be calculated internally.

**Parameters**

| Name | Description | 
|---|---|
| afd | Asset file descriptor|
 
**Returns**

The status of the operation: this is zero in the case of success, or a non-zero NexPlayer™ error code in the
case of failure.
 
> **Warning** When building the APK, most of resources will be compressed. This makes it difficult to extract FileDescriptor. To avoid compressing, you MUST change your file’s extension. These extensions are allowed: ".jpg", ".jpeg", ".png", ".gif", ".wav", ".mp2", ".mp3", ".ogg", ".aac", ".mpg", ".mpeg", ".mid", ".midi", ".smf", ".jet", ".rtttl", ".imy", ".xmf", ".mp4", ".m4a", ".m4v", ".3gp", ".3gpp", ".3g2", ".3gpp2", ".amr", ".awb", ".wma", ".wmv"
 
#### int changeSubtitleFD (FileDescriptor fd, long offset, long length)

Open the caption resource file which is attached in "res/raw" or "assets" folder.

Length and Offset can be acquired from the UI. This API should be called after START() is completed.

**Parameters**

| Name | Description | 
|---|---|
| fd | file descriptor|
| offset | Offset |
| length | length | 
 
**Returns**
 
The status of the operation: this is zero in the case of success, or a non-zero NexPlayer™ error code in the
case of failure.
 
> **Warning** When building the APK, most of resources will be compressed. This makes it difficult to extract FileDescriptor. To avoid compressing, you MUST change your file’s extension. These extensions are allowed: ".jpg", ".jpeg", ".png", ".gif", ".wav", ".mp2", ".mp3", ".ogg", ".aac", ".mpg", ".mpeg", ".mid", ".midi", ".smf", ".jet", ".rtttl", ".imy", ".xmf", ".mp4", ".m4a", ".m4v", ".3gp", ".3gpp", ".3g2", ".3gpp2", ".amr", ".awb", ".wma", ".wmv"
 
#### int changeSubtitlePath (String path)

This method allows the subtitle file for particular content to be changed during playback.

A new subtitle file can be loaded from the device’s storage or from a given URL as passed in the parameter path. For example, the user can change the subtitles to a different language while playing the particular content.

**Parameters**

| Name | Description | 
|---|---|
| path | The path to the new subtitle file to use or the URL to load the new subtitle file from. |
 
**Returns**

Zero if successful or a non-zero error code.
  
#### int close ()

This method ends all the work on the content currently open and closes content data.

The content must be stopped before calling this method.

The correct way to finish playing content is to either wait for the end of content, or to call stop and wait for the stop operation to complete, then call close.

> **Warning** However, do not call close in IListener’s event handlers as this may give rise to a deadlock. A safe way to call close is to use the Android UI main thread’s message handler.
 
**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### native int disableDynamicThumbnail ()

This method disables the Dynamic Thumbnail feature, if enabled.

> **Warning** The Dynamic Thumbnail feature must be disabled by calling this method before calling `NexPlayer.close` when a player is being closed.
 
**Returns**

Zero if successful, or an error code in the event of failure.
 
#### void disableUnsupportedResolutions ()

This method removes the unsupported video resolutions based on the native MediaCodec video capability information.

If the track has lower resolution than the one reported by the MediaCodecInfo API, then that track will be ignored and won’t be played.

This feature only works for API Level 21 and above

#### native int DownloaderClose()

This method is called to close a Downloader event.

Note that this method cannot be called until after initializing NexPlayer™ by calling init(). Anytime DownloaderOpen() is called, this method must also be called properly close the Downloader module. If a call is also made to DownloaderStart(), then DownloaderStop() must be called BEFORE calling DownloaderClose() to properly end the event.

**Returns**

Zero if successful, or an error code in the event of failure.
 
#### native int DownloaderGetInfo(Object info)

This method is called to get information about a Downloader event.

Note that this method cannot be called until after initializing NexPlayer™ by calling init().


**Parameters**

| Name | Description | 
|---|---|
| info | The Downloader object to get information about. |

#### native int DownloaderOpen(String strUrl, String strStorePath, String proxyPath, int proxyPort, int eType)

This method is called to open a new event in the Downloader module.

The Downloader module allows users to download and save streaming progressive download (PD) content in MP4
containers so that it can be viewed at a later time. It must be opened before opening the content to be downloaded and calling `NexPlayer.open()`.

Note that this method cannot be called until after initializing NexPlayer™ by calling init().

**Parameters**

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>strUrl</th>
  <td>This is a string passing the URL to the content to be downloaded.</td>
</tr>
<tr>
  <th>strStorePath</th>
  <td>This is a string indicating the path to where the downloaded file is saved.</td>
</tr>
<tr>
  <th>proxyPath</th>
  <td>This is a string indicating the path to the proxy server.</td>
</tr>
<tr>
  <th>proxyPort</th>
  <td>This is an integer indicating the port to use on the proxy server.</td>
</tr>
<tr>
  <th rowspan="3">Key</th>
</tr>
  <tr><td><b>NEXDOWNLOADER\_OPEN\_TYPE\_CREATE = 0</b> : This creates a new Downloader event.</td></tr>
  <tr><td><b>NEXDOWNLOADER\_OPEN\_TYPE\_APPEND = 1</b> : This appends newly downloaded information to an existing file already begun. Note that not every server will support APPEND events so this should only be used conditional on the content server.</td></tr>
</table>

**Returns**
 
Zero if successful, or an error code in the event of failure.
 
#### native int DownloaderStart ( )

This method is called to start downloading and saving content in a Downloader event.

Note that this method cannot be called until after both initializing NexPlayer™ by calling init() and opening an event in the Downloader module with DownloaderOpen().

**Returns**
 
Zero if successful, or an error code in the event of failure.
 
#### native int DownloaderStop()

This method is called to stop downloading and saving content in a Downloader event.

Note that this method cannot be called until after initializing NexPlayer™ by calling init(). Anytime a call is made to `DownloaderStart()`, it must be matched by a call to this method to properly stop and finish a Downloader event.

**Returns**

Zero if successful, or an error code in the event of failure.
 
#### native int dummyAPI(int apiidx, String p1, String p2, String p3, String p4, String p5, String p6, String p7, String p8)

For internal use only. Please do not use.

#### native int enableDynamicThumbnail()

This method is used to enable and apply the Dynamic Thumbnail feature for Smooth Streaming content.

Refer to the following steps to use this method accurately:

1. The `enableDynamicThumbnail()` method should be called before `NexPlayer.open`.
2. When open completes, use the `getContentInfo()` method to get the total playtime of the content. By dividing the extracted total playtime value by the number of the thumbnail buffer array from the UI (the number of available thumbnails), the interval time is determined. The interval time can then be used with the `setOptionDynamicThumbnail()` method to get thumbnail information.
3. If the setting above works normally, NexPlayer™ will use the `onDynamicThumbnailData()` method to send thumbnail data to the UI.
4. The `disableDynamicThumbnail()` method should be called before `NexPlayer.close` when closing content.
5. If a video track is changed while content is playing, these methods should be called in the following order:
    - FIRST, `disableDynamicThumbnail()`
    - SECOND, `enableDynamicThumbnail()` to enable Dynamic Thumbnails for the new content, and
    - LASTLY, `setOptionDynamicThumbnail(OPTION_DYNAMIC_THUMBNAIL_INTERVAL, interval_time, 0)` to set the appropriate interval for the new thumbnails.

**Returns**
 
Zero if successful, or an error code in the event of failure.
 
#### native int enableTrack (int enableoption)

This method enables the disabled tracks due to temporary content and performance issues. It enables the disabled tracks due to temporary content issues (download fail (ex. 404, 502 error), playlist or response data from the server parsing failing ) and performance issues (decoding & rendering performances).

> **Warning** This is only supported in HLS and DASH contents.
 
**Parameters**
<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="3">enableoption</th>
</tr>
  <tr><td><b>NEXPLAYER_TRACK_ENABLE_OPTION_DISABLED_TEMPORARY</b></td></tr>
  <tr><td><b>NEXPLAYER_TRACK_ENABLE_OPTION_DISABLED_PERFORMANCE</b></td></tr>
</table>

**Returns**

Zero if successful or a non-zero error code.
 
#### native int fastPlaySetPlaybackRate(float rate)

This function sets the video playback rate for thefastPlayfeature.

HLS video content will be played at the speed set by the playback rate when the fastPlay feature is activated
by calling fastPlayStart. This rate can be set to any float value (excluding zero), where positive values
will play content back at a faster speed and negative values will rewind content at the set rate faster than normal playback speed.

If rate is set to zero, this method will return an error.

**Parameters**
 
 
| Name | Description | 
|---|---|
| rate | The speed at which video will play in `fastPlay` mode. This speed is indicated by any float value (but NOT zero), where negative values rewind the video at faster than normal playback speed and positive values play the video faster than normal (like fast forward). For example:<br><br>- rate = 3.0 (fastPlay plays video at 3x normal speed)<br>- rate = - 2.0 (fastPlay rewinds video at 2x normal speed)| 

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
  
#### native int fastPlayStart (int msec, float rate)

This method activates thefastPlayfeature in HLS content.

> **Warning**  This method can be used in HLS content only.
 
The `fastPlay` feature allows NexPlayer™ to play HLS content at a speed other than normal playback speed.
WhenfastPlayis activated, content is played more quickly than normal and there is no audio (similar to a fast forward feature).

The player can also rewind quickly through HLS content using the fastPlay feature by setting the `rate` parameter to a negative value.

To change the speed or direction of thefastPlayfeature, simply call the fastPlaySetPlaybackRate method and
change therateparameter to the desired value.

**Parameters**
 
| Name | Description | 
|---|---|
| msec |The time in the content at which to startfastPlay(inmsec(milliseconds)). |
| rate | The speed at which video will play in `fastPlay` mode. This speed is indicated by any float value (but NOT zero), where negative values rewind the video at faster than normal playback speed and positive values play the video faster than normal (like fast forward). For example:<br><br>- rate = 3.0 (fastPlay plays video at 3x normal speed)<br>- rate = - 2.0 (fastPlay rewinds video at 2x normal speed)| 

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### int fastPlayStop (boolean bResume)

This function turns off thefastPlayfeature in HLS content.

Once the `fastPlay` feature has been activated by calling fastPlayStart, this method must be called in order to stop fastPlay.

In order to reactivate the fastPlay feature after calling fastPlayStop, simply call the fastPlayStart method again. If fastPlayStop is called when fastPlay is not activated, an error will be returned.

**Parameters**

| Name | Description | 
|---|---|
| bResume | This boolean value sets whether to resume playback after fastPlay or not. If bResume = 1, video will automatically resume playback when fastPlay stops. If bResume= 0, when fastPlay stops, the content in NexPlayer™ will be paused.|
 
**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### native int forceCallDRMCallback (int index)

For internal use only. Please do not use.

#### native int getAudioSessionId()

This method gets an audio session ID in order to use Android’s audio effects with NexPlayer™.

> **Warning** This API is only supported on devices running Android OS version 2.3 (Gingerbread) and above.
 
This API allows NexPlayer™ to support use of the Android audio effects like the Android Audio Equalizer. This method should be called before using any audio effect.

**Returns**

An audio session ID as an integer.
  
#### native int getBufferInfo(int iMediaStreamType, int iBufferInfoIdx)

Retrieves the specified buffer information item.

This method provides the ability to monitor the buffer conditions and returns the specified buffer information that has been requested.

**Buffer Info Indexes:** The following integer constants identify different buffer information items that are available; they are passed in the info\_index argument to specify which buffer information item the caller is interested in.

Note that CTS stands for "Current Time Stamp".

**Parameters**

| Name | Description | 
|---|---|
| iMediaStreamType| The type of media stream being received and buffered. This will be one of: MEDIA\_STREAM\_TYPE\_AUDIO, or MEDIA\_STREAM\_TYPE\_VIDEO.|
|iBufferInfoIdx | The integer index of the buffer information item to return. This is one of the NEXPLAYER\_BUFINFO\_INDEX\_ constants, namely one of:|
 
- **NEXPLAYER\_BUFINFO\_INDEX\_BUFSIZE (0)** : Buffer size.
- **NEXPLAYER\_BUFINFO\_INDEX\_INITBUFSIZE (1)** : Initial buffering size.
- **NEXPLAYER\_BUFINFO\_INDEX\_INITBUFTIME (2)** : Initial buffering time.
- **NEXPLAYER\_BUFINFO\_INDEX\_BUFFEREDSIZE (3)** : Buffered size.
- **NEXPLAYER\_BUFINFO\_INDEX\_BUFRATE (4)** : (Buffered size)∗100/(Total Buffer
    size), or the percentage full that the buffer is.
- **NEXPLAYER\_BUFINFO\_INDEX\_FIRSTCTS (5)** : CTS of the first frame in buffer. (If
    there is no frame: 0xFFFFFFFF)
- **NEXPLAYER\_BUFINFO\_INDEX\_LASTCTS (6)** : CTS of the last frame in buffer. (If
    there is no frame: 0xFFFFFFFF)
- **NEXPLAYER\_BUFINFO\_INDEX\_DURATION (7)** : The total duration of frames in
    buffer.
- **NEXPLAYER\_BUFINFO\_INDEX\_FRAMECOUNT (8)** : The total count of the frames
    in buffer.
- **NEXPLAYER\_BUFINFO\_INDEX\_STATE (9)** : Buffering state (0: paused, 1: re-
    sumed).

**Returns**

 
The integer value of the requested buffer information item.
  
#### native int getBufferStatus()

This method determines the amount of currently buffered data. It returns the amount of data that has been buffered ahead of the current playing position. This is useful to know in cases when it is possible to seek in (for example) a progressive download without needing to buffer.

**Returns**
 
The number of milliseconds (1/1000 sec) of media that has been buffered ahead.
 
> **Deprecated** This method is deprecated from version 6.0.5, and using it is not recommended. Please use getBufferInfo instead.

#### int getClientStatus ( int id)

This method gets the current status of a client module integrated into the NexPlayer™ SDK.

> **Warning** Note that client modules are optional features of the NexPlayer™ SDK. For more information on how to integrate and use a client module available in the SDK (as well as sample code), please see the relevant NexXXXClient class.
 
**Parameters**

| Name | Description | 
|---|---|
|id | The client ID as an integer.|
 
**Returns**

0 if the status of the client is normal, -1 if the client has an error, and 1 if the client module has not been initialized.
 
**See Also**
 
- addNexClient
- removeNexClient
 
#### NexContentInformation getContentInfo()

This function retrieves information from the current content.

> **Note** The `getContentInfoInt` function also returns information on the current content. In some cases, the same information is available through both functions. However, some items are available only through one of the functions.
 
**PERFORMANCE NOTE:** This allocates a new instance of NexContentInformation every time it is called,
which may place a burden on the garbage collector in some cases. If you need to access multiple fields, save the returned object in a variable. For cases that are particularly sensitive to performance, selected content information is available through getContentInfoInt, which doesn’t allocate any objects.

**Returns**
 
A NexContentInformation object containing information on the currently open content.
 
**See Also**

getContentInfoInt

#### native int getContentInfoInt(int info\_index)

Retrieves the specified content information item.

In most cases, this is equivalent to calling getContentInfo and accessing an individual field in the return value.

However, there are a few items that are only available through this method, and for items available through both methods, this one may be more efficient in certain cases. SeegetContentInfofor more information.

Certain fields (such as the list of tracks) are only available through the full structure, and certain fields (such as frames displayed per second) are only available here.

**Content Info Indexes:** The following integer constants identify different content information items that are available; they are passed in the info\_index argument to specify which content information item the caller is interested in.

**Also available in `getContentInfo`:**

- **CONTENT\_INFO\_INDEX\_MEDIA\_TYPE (0)** Same as the mMediaType member ofNexContentInfo
- **CONTENT\_INFO\_INDEX\_MEDIA\_DURATION (1)** Same as the mMediaDuration member ofNexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC (2)** Same as the mVideoCodec member ofNexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_WIDTH (3)** Same as the mVideoWidth member ofNexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_HEIGHT (4)** Same as the mVideoHeight member ofNexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_FRAMERATE (5)** Same as the mVideoFrameRate member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_BITRATE (6)** Same as the mVideoBitRate member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_AUDIO\_CODEC (7)** Same as the mAudioCodec member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_AUDIO\_SAMPLINGRATE (8)** Same as the mAudioSamplingRate member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_AUDIO\_NUMOFCHANNEL (9)** Same as the mAudioNumOfChannel member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_AUDIO\_BITRATE (10)** Same as the mAudioBitRate member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_MEDIA\_ISSEEKABLE (11)** Same as the mIsSeekable member ofNexContentInfo
- **CONTENT\_INFO\_INDEX\_MEDIA\_ISPAUSABLE (12)** Same as the mIsPausable member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_FOURCC (13)** Same as the mVideoFourCC member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_CLASS (14)** Same as the mVideoCodecClass member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_PROFILE (15)** Same as the mVideoProfile member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_LEVEL (16)** Same as the mIsVideoLevel member of NexContentInfo
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_ERROR (17)** Same as the VideoCodecErrormember of NexContentInfo

**Video Performance Information (Available only via `getContentInfoInt`):** The NexPlayer™ engine reads
frames from the content, then decodes and displays each frame. If the device is not powerful enough for the
resolution or bitrate being played, the decoding or display of some frames may be skipped in order to maintain synchronization with the audio track.

The values of the parameters in this section provide information about the number of frames actually being displayed. Per-second averages are calculated every two seconds (although this interval may change in future releases). Frame counts reset at the same interval, so the ratio is generally more meaningful than the actual numbers (since the interval may change). Running totals are also provided, and are updated at the same interval.

If you wish to perform your own calculations or average over other intervals, you can periodically sample the running totals. Running totals are reset when new content is opened.

- **CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_AVE\_FPS (1000)** Average number of video frames per second decoded. This number was multiplied by 10, so you should divide by 10.
- **CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_AVE\_DSP (1001)** Average number of video frames per second actually displayed. This number was multiplied by 10, so you should divide by 10.
- **CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_COUNT (1002)** Number of video frames displayed.
- **CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_TOTAL\_COUNT (1003)** Total number of video frames displayed.
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_DECODING\_COUNT (1004)** Number of video frames decoded during the last interval.
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_DECODING\_TOTAL\_COUNT (1005)** Total number of video frames decoded.
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_AVG\_DECODE\_TIME (1006)** Average time to decode video frames.
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_AVG\_RENDER\_TIME (1007)** Average time to render video frames.
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_DECODE\_TIME (1008)** Time taken to decode one video frame.
- **CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_RENDER\_TIME (1009)** Time taken to render one video frame.
- **CONTENT\_INFO\_INDEX\_VIDEO\_AVG\_BITRATE (1010)** Average bitrate of video currently playing.
- **CONTENT\_INFO\_INDEX\_VIDEO\_FRAMEBYTES (1011)** Total size of video frames, in bytes.
- **CONTENT\_INFO\_INDEX\_AUDIO\_AVG\_BITRATE (1012)** Average bitrate of audio currently playing.
- **CONTENT\_INFO\_INDEX\_AUDIO\_FRAMEBYTES (1013)** Total size of audio frames, in bytes.
- **CONTENT\_INFO\_INDEX\_VIDEO\_FRAME\_COUNT (1014)** Number of video frames available to be decoded during the last interval.
- **CONTENT\_INFO\_INDEX\_VIDEO\_TOTAL\_FRAME\_COUNT (1015)** Total number of video frames to decode.

For example, to determine the number of B-frames skipped in the previous interval simply calculate CONTENT\_INFO\_INDEX\_VIDEO\_FRAME\_COUNT - CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_DECODING\_COUNT.

Also note that CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_DECODING\_COUNT - CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_COUNT can be used to determine how many frames were decoded but were not rendered due to performance limitations.

**Parameters**

| Name | Description | 
|---|---|
| info\_index |The integer index of the content information item to return. This is one of the CONTENT\_INFO\_INDEX\_ constants described above.|
 
**Returns**
 
The integer value of the requested content information item.
 
**See Also**
 
- CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_AVE\_FPS
- CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_AVE\_DSP
- getContentInfo
- NexContentInformation
 
#### native int getCurrentPosition()

This method gets the current play time position of NexPlayer™ in the given content.

This method can be called at any time to check the current position.

**Returns**
 
The current play time position inmsec(milliseconds).
 
#### int getCurrentSoundEffect()

For internal use only. Please do not use.

#### String getDetailedError()

This method provides a string of information when a network or protocol error occurs, such as a timeout due to a connection delay.

If the category of the NexErrorCode is Network or Protocol, or a timeout such as SOURCE\_OPEN\_TIMEOUT /
DATA\_INACTIVITY\_TIMEOUT by NEXPLAYER\_EVENT\_DATA\_INACTIVITY\_TIMEOUT, the string will be filled.

> **Warning** NexProperty.ENABLE\_DETAIL\_ERROR should be enabled to get this information
 
**Returns**
 
Returns a string of information for Network or Protocol errors, an empty string if none.
 
#### native int GetNearestIFramePos ( int targetTS)

This method returns the nearest I-Frame timestamp in front of the target position when seeking.

It can get the nearest timestamp of I-Frame in front of target position to use highlight function.

**Parameters**

| Name | Description | 
|---|---| 
|targetTS | A pointer to the timestamp of the target position.|
 
**Returns**
 
Zero or a positive number if successful, a negative number if there was an error.
 
#### int getProgramTime(PROGRAM\_TIME time)

This method gets the date and time information in HLS content when the HLS tag, #EXT-X-PROGRAM-DATE-TIME,
is included.

The same information is also returned approximately once a second by the IListener event, onProgramTime. It can be used to determine the current time of the frame and help when syncing content and text or when determining when to play text.

**Parameters**

| Name | Description | 
|---|---|
|time| The program time information of the current decoding frame as a PROGRAM\_TIME object.|
 
**Returns**
 
Always zero.
 
**See Also**

- PROGRAM\_TIME for more details
- IListener.onProgramTime
  
#### native int getProperties(int property)

Gets the value of an individual NexPlayer™ property based on the numerical ID of the property.

Normally, getProperty should be used instead of this method. Use this methodonlyif you have a numeric property code.

For a full list of properties, see the NexProperty enum. To get the numeric code for a property, call the getPropertyCode method on the enum member.

For example:

```java
int supportRTSP = getProperties(NexProperty.SUPPORT\_RTSP.getPropertyCode());
```

**Parameters**

| Name | Description | 
|---|---| 
|property| The numeric property code identifying the property to get.|
 
**Returns**

The value of the property.
 
#### int getProperty (NexProperty property)

Gets the value of an individual NexPlayer™ integer property. Properties control the behavior of NexPlayer™ and the features that are enabled. This gets integer properties; for string properties, use getStringProperty instead.

**See Also**
 
- NexProperty for details.
 
**Parameters**

| Name | Description | 
|---|---|
|property| The property to get.|
 
**Returns**

The value of the property.
 
#### native int GetRenderMode ()

Returns the type of renderer in use by the NexPlayer™ engine.

You must check the render mode using this method and adjust the application behavior appropriately. For details see Java Renderer or OpenGL Renderer.

When using the Java renderer (NEX\_USE\_RENDER\_JAVA), the application must NOT callsetOutputPosor
setDisplay. Doing so may cause the application to crash if running under Honeycomb.

When using the OpenGL renderer (NEX\_USE\_RENDER\_OPENGL), the application must NOT callsetDisplay.

**Returns**
 
Render mode; one of:
 
- **NEX\_USE\_RENDER\_AND** Using only standard Android API bitmaps to display frames.
- **NEX\_USE\_RENDER\_JAVA** Don’t render to the display. Instead, each frame is decoded and converted
    to the appropriate color space, and then sent to the application to display.
- **NEX\_USE\_RENDER\_OPENGL** Using OpenGL ES 2.0 to display frames.
- **NEX\_USE\_RENDER\_IOMX** Using the hardware video renderer to display frames. Note that this ren-
    derer is used with Ice Cream Sandwich and higher versions of OS and only on supported hardware.

#### native String getSARInfo()

This method retrieves the SAR (Sample Aspect Ratio) of H.264 content when specified.

The sample aspect ratio (SAR) returned by this method is expressed as a ratio of the width of the sample size to the height of the sample size. It can be used to appropriately display content to the user.

This sample aspect ratio will be one of the following ratios:

1:1, 4:3, 3:2, 2:1, 12:11, 10:11, 40:33, 24:11, 20:11, 32:11, 80:33, 18:11, 15:11, 64:33, or 160:99.

Note that if SAR information is not specified for given H.264 content, the returned ratio will also be 1:1.

To retrieve the SAR information as integers, the method `getSARInfo(int[] info)` should be called instead.

For more information about the SAR information included in H.264 content, please consult Table E-1 - Meaning of Sample Aspect Ratio Indicator on page 374 of the H.264 specifications (Rec. ITU-T H.264 (03/2010).

**Returns**

 
The sample aspect ratio of the content as a string, for example "1:1".
 
**See Also**
 
getSARInfo(int[])
 
#### void getSARInfo(int[] info)

This method can be used to retrieve the SAR (Sample Aspect Ratio) information of H.264 content as separate
integers.

To receive the SAR as a string, the method getSARInfo() should be called instead. The first element of the
getSARInfo integer array will be the aspect width of the sample and the second element will be the aspect height of
the sample.

**Parameters**

| Name | Description | 
|---|---| 
|info| An integer array of 2 elements where the first is the aspect width of the sample and the
second is the height.|
 
**See Also**
 
getSARInfo()
 
5.91.3.49 native String getSDKName()

This method returns the name of the NexPlayer™ SDK in use. It can be used for confirmation and for debugging purposes but should generally be ignored.

**Returns**
 
The name of the NexPlayer™ SDK as a string.
 
#### long[] getSeekableRangeInfo()

This method returns the range of the current content that is seekable.

This method is used to allow NexPlayer™ to support timeshifting playback within HLS Live and Smooth Streaming content. Based on the amount of content available from the server at a particular time, it determines the seekable range within the playing content which also indicates the range where playback may be timeshifted. This range will be constantly shifting as the live streaming content available from the server changes in real time, so this method will need to be repeatedly called to ensure accurate shifting of playback.

For local content this method will always return the same two values, and the second value indicating the end of the seekable range will continuously change in progressive download (PD) content, but this method is most relevant when playing live streaming content, as with HLS and Smooth Streaming.

For more information about how this method may be used to timeshift playback in live content, please also refer to the introductory section on time shift support.

**Returns**

An array of twolongs, the firstlongbeing the timestamp indicating the start of the seekable range and the
second being the timestamp indicating the end of the seekable range.
 
#### native int getState()

This method retrieves the current state of NexPlayer™.

Calling methods such as open and start does not immediately change the state. The state changes asynchronously, and the new state goes into effect at the same time onAsyncCmdComplete is called to notify the application.

**Returns**
 
A constant indicating the current state. This is one of the following values:
 
- NEXPLAYER\_STATE\_CLOSED
- NEXPLAYER\_STATE\_NONE
- NEXPLAYER\_STATE\_PAUSE
- NEXPLAYER\_STATE\_PLAY
- NEXPLAYER\_STATE\_STOP

#### native String getStringProperties(int property)

Gets the string value of an individual NexPlayer™ property based on the numerical ID of the property.

Normally, getStringProperty should be used instead of this method. Use this methodonlyif you have a numeric
property code.

For a full list of properties, see the NexProperty enum. To get the numeric code for a property, call the `getPropertyCode` method on the enum member.

For example:

```java
String userAgent = getProperties(NexProperty.USERAGENT\_STRING.getPropertyCode());
```

**Parameters**

| Name | Description | 
|---|---|
|property| The numeric property code identifying the property to get.|
 
**Returns**
 
The string value of the property.
 
#### String getStringProperty (NexProperty property)

Gets the string value of an individual NexPlayer™ property.

Properties control the behavior of NexPlayer™ and the features that are enabled.

This gets string properties; for integer properties, use getProperty instead.

**See Also**

NexProperty for details.
 
**Parameters**

| Name | Description | 
|---|---| 
|property| The property to get.|
 
**Returns**

The string value of the property.
 
#### native int getVersion(int mode)

Gets NexPlayer™ SDK version information.

The return value is an integer; the meaning is based on themodeargument passed.

Generally, the components of the version are assembled as follows:

```java
String versionString = nexPlayer.getVersion(0) + "." +
nexPlayer.getVersion(1) + "." +
nexPlayer.getVersion(2) + "." +
nexPlayer.getVersion(3);
```

**Parameters**

| Name | Description | 
|---|---|
|mode| Version information to return. This must be one of the following values (other values are reserved and should not be used): <br>- 0 : Major version<br>- 1 : Minor version<br>- 2 : Patch version<br>- 3 : Build version|

**Returns**

Requested version information (seemodeabove).
 
#### native int GLDraw (int mode)

Draws in the current OpenGL context.

> **Deprecated** This method supports legacy code but should not be called by new code. Instead use the GLRenderer class.

This remains public to support legacy code that implemented aGLSurfaceViewsubclass directly. However, new
code should not call this method. Instead, simply use the GLRenderer class provided with the NexPlayer™ SDK.
That class automatically calls GLDraw when needed.

> **Warning** This must be called from the OpenGL renderer thread (the thread where GLSurfaceView.Renderer.onDrawFrameis called). Calling this from anywhere else will result in undefined behavior and possibly cause the application to crash.
 
**Parameters**

| Name | Description | 
|---|---|
|mode| The type of drawing operation to perform.<br> - **0:** Draw the most recent video frame.<br>- **1:** Erase the surface to black.|

**Returns**
 
Always zero, but may change in future versions. The return value should be ignored.

#### native int GLInit ( int width,int height)

Informs NexPlayer™ of the current size of the GLSurfaceView subclass instance.

This should be called whenever the size of theGLSurfaceViewsubclass instance changes, as well as when the
instance is initially created. This is because internally, OpenGL APIs use a different coordinate system, and NexPlayer™ must know the pixel dimensions in order to map the OpenGL coordinate system to per-pixel coordinates.

**Parameters**

| Name | Description | 
|---|---| 
|width| Width ofGLSurfaceViewsubclass instance, in pixels.|
|height| Height ofGLSurfaceViewsubclass instance, in pixels.|
 
**Returns**

Always 0, but may change in future versions. The return value should be ignored.
 
#### int gotoCurrentLivePosition()

This method moves to the current live position after the actual playback position.

Normally, when playing live content, previously recorded data (for example, a few seconds earlier than the actual live position) is played to avoid buffering. This method however ignores this concept and moves directly to the latest loaded playback position (where the server is currently being encoded).

This method behaves in the same way as the method gotoCurrentLivePosition(boolean exact) with the parameter,
exact, set totrue. In other words, NexPlayer™ will seek exactly to the time specified bymsec(milliseconds).

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### native int gotoCurrentLivePosition(boolean exact)

This method moves to the current live position after the actual playback position.

Normally, when playing live content, previously recorded data (for example, a few seconds earlier than the actual live position) to avoid buffering. This method however ignores this concept and moves directly to the latest loaded playback position (where the server is currently being encoded).

**Parameters**

| Name | Description | 
|---|---| 
|exact| If exact is true, the player will seek exactly to the time specified bymsec(milliseconds). Otherwise, the playhead will seek to the nearest approximate position for faster seeking performance. |
 
**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### NexErrorCode init (Context context)

This method initializes NexPlayer™.

This must be called **after** NexPlayer.setNexALFactory has been called. This can be done for example by using:

```java
mNexALFactory.init(this, strModel, strRenderMode, 0, colorDepth);
mNexPlayer.setNexALFactory(mNexALFactory);
mNexPlayer.init(this);
```

**Parameters**

| Name | Description | 
|---|---| 
|context| The current context; from Activity subclasses, you can just pass this.|
 
**Returns**
 
NexPlayer™ error code for the generated error.
 
#### NexErrorCode init (Context context, int logLevel)

This method initializes NexPlayer™.

This must be called **after** NexPlayer.setNexALFactory has been called. This can be done for example by using:

```java
mNexALFactory.init(this, strModel, strRenderMode, 0, colorDepth);
mNexPlayer.setNexALFactory(mNexALFactory);
mNexPlayer.init(this, 0)
```

**Parameters**

| Name | Description | 
|---|---| 
|context| The current context; fromActivitysubclasses, you can just pass this.|
|logLevel| NexPlayer™ SDK logging level. This affects the messages that the SDK writes to the Android log.<br>**-1** : Do not output any log messages.<br>**0** : Output basic log messages only (recommended).<br>**1** ∼ **4** : Output detailed log messages; higher numbers result in more verbose log entries, but may cause performance issues in some cases and are not recommended for general release code.|

**Returns**

NexErrorCode.NONE if initialization succeeded; NexPlayer™ errorcode for the generated error in
the case of a failure (in the case of failure, check the log for details).
 
 
#### boolean isInitialized ( )

Determines if NexPlayer™ is currently initialized.

To initialize NexPlayer™, NexPlayer.init must be called. If that method returnstrue, then this method will also return true if called on the same instance of NexPlayer™.

In some cases, it is necessary to call NexPlayer™ functions from event handlers in subclasses ofActivity(such as `onPause` or `onStop`). In such event handlers, it is possible for them to be called before code that initializes NexPlayer™, or for them to be called after a failed initialization. Therefore, any calls to NexPlayer™ methods made from onPause or similar event handlers must be protected as follows:

```java
if( nexPlayer.isInitialized()) {
// Calls to other methods are safe here
}
```
**Returns**
 
true if NexPlayer™ is currently initialized.
 
#### native int notifyHeadsetState(int uiOnOff)

This method notifies the NexPlayer™ engine whether a wired headset has been plugged in or unplugged.

When the ENHANCED\_SOUND\_AVAILABILITY property is set equal to 1 and more, this method must be called
(1) before calling NexPlayer.start() and (2) every time the state of the headset changes.

For example:

```java
if (intent.getAction().equals(Intent.ACTION\_HEADSET\_PLUG))
{
int headSetState = intent.getExtras().getInt("state");
// 0 : unplugged 1 : plug in
mNexPlayer.notifyHeadsetState(headSetState);
}
```

**Parameters**

| Name | Description | 
|---|---|
|uiOnOff| An integer indicating whether enhanced sound ison(a headset is plugged in) or off(the headset is unplugged) when enhanced sound is available in the NexPlayer™ SDK. Possible Values:<br>- on = 1<br>- off = 0|

**Returns**
 
Zero is successful or a non-zero error code.
 
5.91.3.63 void onOfflineExpiredKeyFetchMode(bool eansetMode)

This method switch using either KEYEXPIRE\_RETRIEVE\_STORE mode or RETRIEVE mode when only using
Offline Playback on media DRM.

> **Warning** This must be called beforeNexPlayer.open.
 
**Parameters**
 
| Name | Description | 
|---|---|
|setMode| TRUE to setting KEYEXPIRE\_RETRIEVE\_STORE mode, FALSE to setting RETRIEVE mode. when Offline Playback |
 
#### int open (String path, String smiPath, String externalPDPath, int type, int transportType)

This method begins opening the media at the specified path or URL.

This supports both local content and streaming content.

When the stored info file is created by using NexOfflineStoreController and then passed to the path parameter, this method opens content for offline playback.

This is an asynchronous operation that will run in the background (even for local content).

When this operation completes, `onAsyncCmdComplete` is called with one of the following command constants
(depending on thetypespecified in the open call):

- NEXPLAYER\_ASYNC\_CMD\_OPEN\_LOCAL
- NEXPLAYER\_ASYNC\_CMD\_OPEN\_STREAMING
- NEXPLAYER\_ASYNC\_CMD\_OPEN\_STORE\_STREAM

Success or failure of the operation can be determined by checking theresultargument passed toonAsync-
CmdComplete. If the result is 0, the media was successfully opened; if it is any other value, the operation failed.

Calls to open must be matched with calls to NexPlayer.close.

**Parameters**

| Name | Description | 
|---|---|
|path| The location of the content: a path (for local content) or URL (for remote content).|
|smiPath| The path to a local subtitle file, the URL to load a subtitle file, or null for no subtitles. For streaming content that already includes subtitles, this should benull(using both types of subtitles at the same time will cause undefined behavior).|
|externalPDPath | When not null, the external path used to play PD content downloaded by the Downloader module. This is only available for content in MP4 containers. |
|type | This determines how the path argument is interpreted. This will be one of: <br>`NEXPLAYER_SOURCE_TYPE_LOCAL_NORMAL` to play local media (the path is a local file system path)<br>`NEXPLAYER_SOURCE_TYPE_STREAMING` to play remote media sources (including RTSP streaming, progressive download and HTTP Live streaming). The path is interpreted as a URL.<br>`NEXPLAYER_SOURCE_TYPE_STORE_STREAM` to store remote media content (only currently available with HTTP Live streaming (HLS) content and not supported for live content) for later offline playback.    Other NEXPLAYER\_SOURCE\_∗values are not supported in this version and should not be used.|
| transportType | The network transport type to use on the connection. This should be one of:<br>`NEXPLAYER_TRANSPORT_TYPE_TCP`<br>`NEXPLAYER_TRANSPORT_TYPE_UDP`|

**Returns**

The status of the operation: this is zero in the case of success, or a non-zero NexPlayer™ error code in the
case of failure.
 
> **Note** This only indicates the success or failure ofstartingthe operation. Even if this reports success, the operation may still fail later, asynchronously, in which case the application is notified in onAsyncCmdComplete.
 
#### int open (String path, String smiPath, String externalPDPath,int type, int transportType, int bufferingTime)

> **Deprecated** This API is deprecated. Please use NexPlayer.open(String, String, String, int, int) instead. Use `INITIAL_BUFFERING_DURATION` and `RE_BUFFERING_DURATION` of NexProperty instead
of the parameter `bufferingTime`.

#### int openFD (AssetFileDescriptor afd)

Open the media resource file which is attached in "res/raw" or "assets" folder Access should be provided by AssetFileDescriptor.

Length and Offset will be calculated internally.

**Parameters**

| Name | Description | 
|---|---| 
|afd| Asset file descriptor.|
 
**Returns**
 
The status of the operation: this is zero in the case of success, or a non-zero NexPlayer™ error code in the
case of failure.
 
> **Warning** When building the APK, most of resources will be compressed. This makes it difficult to extract FileDescriptor. To avoid compressing, you MUST change your file’s extension. Below extensions are allowed: ".jpg", ".jpeg", ".png", ".gif", ".wav", ".mp2", ".mp3", ".ogg", ".aac", ".mpg", ".mpeg", ".mid", ".midi", ".smf", ".jet", ".rtttl", ".imy", ".xmf", ".mp4", ".m4a", ".m4v", ".3gp", ".3gpp", ".3g2", ".3gpp2", ".amr", ".awb", ".wma", ".wmv"
 
#### int openFD ( FileDescriptor fd,long offset,long length)

Open the resource files which are attached in "res/raw" or "assets" folder.

Length and Offset can be acquired from the UI.

When the stored info file is created by using NexOfflineStoreController and then passed to the path parameter, this method opens content for offline playback.

**Parameters**

| Name | Description | 
|---|---|
|fd |File descriptor.|
|offset| Offset.|
|length| Length.|
 
**Returns**

The status of the operation: this is zero in the case of success, or a non-zero NexPlayer™ error code in the
case of failure.
 
> **Warning** When building the APK, most of resources will be compressed. This makes it difficult to extract FileDescriptor. To avoid compressing, you MUST change your file’s extension. Below extensions are allowed: ".jpg", ".jpeg", ".png", ".gif", ".wav", ".mp2", ".mp3", ".ogg", ".aac", ".mpg", ".mpeg", ".mid", ".midi", ".smf", ".jet", ".rtttl", ".imy", ".xmf", ".mp4", ".m4a", ".m4v", ".3gp", ".3gpp", ".3g2", ".3gpp2", ".amr", ".awb", ".wma", ".wmv"

#### int pause()

This method pauses the current playback.

Please note that when the hardware codec is in use, if the application is sent to the background by pressing the home button, pausing and resuming playback may return an error because of resource limitations. To avoid this potential issue, stopping and starting playback is recommended in algorithm handling this specific case of the application being sent to the background because the home button was pressed.

**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### native int playspeedcontrol(float fPlaySeed)

This method controls the playback speed of content by the given percent.

> **Note** Speed Control is an optional feature. This method makes it possible to allow users to adjust the playback speed of content, from a quarter of the original speed to double speed, by changing the value of the parameter fPlaySeed. For example, to play content at half-speed,fPlaySeedshould be set to 0.5
 
This method doesn’t work if it is called when NexPlayer™ is stopped.

**Parameters**

| Name | Description | 
|---|---| 
|fPlaySeed| This float represents the percentage by which to change the playback speed. It must be in
the range of 0.25 to 2.0, which adjusts the playback speed from 0.25x to 2x the original speed
of the content.|
 
> **Warning** When using this method with HLS or Smooth Streaming content, playing multitrack content may cause unstable performance. Therefore, playing content as a single track is encouraged.
 
#### native int reconnectNetwork()

This method allows NexPlayer™ to reconnect to the media server in the case of streaming content.

It allows NexPlayer™ to reconnect to a media server when network conditions may have closed a connection.

> **Warning** This is only supported in HLS, DASH, SmoothStreaming and PD streaming content.
 
**Returns**

Zero if successful or a non-zero error code.
 
#### native int recPause()

Recording interface; not available in current version. Do not use.

> **Deprecated** Not available in current version; do not use.

#### native int recResume()

Recording interface; not available in current version. Do not use.

> **Deprecated** Not available in current version; do not use.

#### native int recStart (String path,int maxsize)

Recording interface; not available in current version. Do not use.

> **Deprecated** Not available in current version; do not use.

#### native int recStop()

Recording interface; not available in current version. Do not use.

> **Deprecated** Not available in current version; do not use.

#### void release()

This method releases resources used by the NexPlayer™ instance.

This should be called when the instance is no longer needed. After calling this method, the instance can no longer be used, and methods on it should not be called, except for getState which will return `NEXPLAYER_STATE_NONE.`

#### boolean removeEventReceiver(NexEventReceiver receiver)

This removes a receiver which was added withaddEventReceiver.

**Parameters**

| Name | Description | 
|---|---|
|receiver| The object to which methods will be called when events occur.|
 
**See Also**

- NexEventReceiver
- NexPlayer.addReleaseListener
 
#### NexClient removeNexClient ( int client\_id)

This method removes a client module integrated into the NexPlayer™ SDK.

Note that client modules are optional features of the NexPlayer™ SDK. For more information on how to integrate and use a client module available in the SDK (as well as sample code), please see the relevant NexXXXClient class.

> **Warning** When NexPlayer™ is released, the client will be removed automatically.
 
**Parameters**

| Name | Description | 
|---|---|
|client\_id| The ID of the client module as an integer. This is the return value ofaddNexClient().|
 
**Returns**
 
The removed client module as aNexClientobject.
 
**See Also**
 
- addNexClient
- getClientStatus
 
#### void removeReleaseListener (IReleaseListener listener)

Removes a callback listener which was added withaddReleaseListener.

**Parameters**

| Name | Description | 
|---|---|
|listener| The object on which methods will be called when the instance of NexPlayer™ is released.|
 
**See Also**

- NexPlayer.IReleaseListener
- NexPlayer.addReleaseListener
 
#### int resume ()

This method resumes playback beginning at the point at which the player was last paused.

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### native int seek ( int msec,boolean exact)

This method seeks the playback position to the specified time.

This doesn’t work if NexPlayer™ is stopped or if the stream doesn’t support seeking, but does work if NexPlayer™ is playing or paused.

Note that even if the parameterexactisTRUE, it is possible to minimize seek time by adjusting the NexProperty SEEK\_RANGE\_FROM\_RA\_POINT.

Note that NexPlayer’s state will be changed to pause and resume automatically if this method is called during playback. Therefore, if getState is calling while NexPlayer is seeking, the UI can get NEXPLAYER\_STATE\_PAUSE.

**Parameters**

| Name | Description | 
|---|---|
|msec| The offset inmsec(milliseconds) from the beginning of the media to which the playback position should seek.|
|exact| If exact is true, the player will seek exactly to the time specified bymsec(milliseconds). Otherwise, the playhead will seek to the nearest approximate position for faster seeking performance.
 
**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
**See Also**
 
NexProperty.SEEK\_RANGE\_FROM\_RA\_POINT
 
#### int seek (int msec)

This function seeks the playback position exactly to a specific time.

This doesn’t work if NexPlayer™ is stopped or if the stream doesn’t support seeking, but does work if NexPlayer™ is playing or paused.

This method behaves in the same way as the method seek(int msec, boolean exact) with the second parameter,
exact, set totrue. In other words, NexPlayer™ will seek exactly to the time specified bymsec(milliseconds).

**Parameters**

| Name | Description | 
|---|---|
|msec| The offset in milliseconds from the beginning of the media to which the playback position should seek.|
 
**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
**See Also**
 
NexPlayer.seek(int msec, boolean exact)
 
#### native int setAudioPitch ( int iPitchIndex)

This method sets the pitch control settings for audio in content.

> **Note** Audio pitch control is an optional feature in the NexPlayer™ SDK.
 
The pitch of audio in content is adjusted compared to the original pitch of the audio. SettingiPitchIndex= 0
will not change the pitch, but with each integer step, the pitch will be adjusted by another semitone.

For example, if the original audio has a pitch of C, then withiPitchIndex= 1, the new pitch set will be a semitone higher than the original, or C sharp (D flat). Similarly, if the pitch is to be lower than the original,iPitchIndex should be set to a negative value (in particular, for original audio with a pitch of C,iPitchIndex= -2 will change the pitch to A sharp (B flat)).

**Parameters**

| Name | Description | 
|---|---| 
|iPitchIndex| The index of the pitch to apply to the content, where 0 is no change in pitch, and each other
integer value indicates an additional semitone change in pitch away from the original audio.
Range of pitch control (index): {-12, -11, -10, ... -1, 0, 1, ... 10, 11, 12} |
 
**Returns**

Zero if successful, or an error code in the case of failure.
 
#### native int setAutoVolume ( int uiOnOff)

This method turns the Auto Volume featureonoroff, but this feature is only available in some product categories.

> **Note** Auto Volume is an optional feature.
 
When Auto Volume is turnedon, NexPlayer™ automatically adjusts the volume level of different content so that
it is played at a consistent and optimal volume level, allowing the user to play different content without having to constantly adjust the volume when new content starts.

By default, Auto Volume is turnedoff(identical to the behavior of the player in product categories that do not support this feature).

**Parameters**

| Name | Description | 
|---|---| 
|uiOnOff| This turns the Auto Volume featureonand. By default, this feature isoff= 0.<br>Possible Values: <br>- on= 1<br>- off= 0|

**Returns**
 
The new value of Auto Volume. If Auto Volume was turnedoff, this will be 0.
If Auto Volume was turnedon, it will return 1.
If Auto Volume is not supported in this version of the NexPlayer™, this will return the error, NOT\_SUPPORT
(0x8000000FL).
 
#### native int SetBitmap (Object mFrameBitmap)

Sets a bitmap to be used to receive rendered frames for display, when using the Java-based renderer.

For more information on this method, please also refer to theJava Renderersection of the NexPlayer™ Engine
documentation.

**Parameters**

| Name | Description | 
|---|---| 
|mFrameBitmap| The bitmap to receive rendered frames (when using Java-based renderer).|
 
**Returns**

Always 0, but may change in future versions. The return value should be ignored.
 
#### native int setCaptionLanguage (int indexOfCaptionLanguage)

This method selects a caption (subtitle) track that will be used.

Subtitles for the selected track will be passed to onTextRenderRender for display.

This is used for file-based captions only. For streaming media with included captions,setMediaStream()
should be used instead, and local captions should be turned off since running both types of captions at the same time has undefined results.

**Parameters**

| Name                   | Description                                                                                                                                                                                          |
|----|----------------------------------|
| indexOfCaptionLanguage | An index into the mCaptionLanguages array specifying which language to use. If there are n entries in the caption array, then you may pass 0 ...n-1 to specify the language, n to turn off captions. |
 
**Returns**
 
Zero if successful, non-zero if there was an error.
 
#### native int setCEA608CaptionChannel ( int nChannel)

Sets the input channel for CEA 608 closed captions.

This method will be one of four available channels. Setting the input channel to zero will also disable or turn off CEA 608 closed captions if they are present.

When viewing content including CEA 608 closed captions, it is important to choose whether to have the application support them in BASIC or FULL mode with the property SET\_CEA608\_TYPE. In order to meet CEA 608 closed caption specifications completely, the closed captions should be displayed in the FULL mode. If BASIC mode is selected, the closed captions will be treated similar to other subtitles and may not always be accurately displayed (or may be difficult for a user to read) depending on the display attributes used in the closed captions.

When supporting CEA 608 closed captions in BASIC mode, setting the input channel to any number between 1 and
4 merely enables and displays the captions.

Since CEA 608 closed captions may include different information on the available input channels, the desired input channel may be selected in FULL mode by choosing the relevant channel number (1, 2, 3, or 4).

**Parameters**

| Name | Description | 
|---|---|
|nChannel| This will be an integer from 0 to 4. If it is zero, the closed captions will be disabled. When using CEA 608 captions in BASIC mode, 1 to 4 simply enable the captions. When using CEA 608 captions in FULL mode, 1 to 4 chooses the input channel to be displayed as closed captions.|
 
**Returns**
 
Zero if successful or a non-zero error code.
 
#### int setClientTimeShift (boolean bEnable, String strFileBufferPath, int uiTimeShiftBufferSize,int uiTimeShiftDuration)

This method enables the client time shift feature in the NexPlayer™ SDK.

Time shifting is a feature to store realtime data as it is received so that the user can watch past data while playing live content. When this feature is enabled, NexPlayer™ prepares for the time shift and only afterpauseis called, it stores received data from a live stream in local file storage with the specified buffer size and duration set with this API. As a result, the user can seek and pause even when the content playing is live. This method will be stopped when the methodgotoCurrentLivePositionis called.

> **Note** This method should be called between calls toinit()andopen(). Furthermore, onceopen()is called,
the parameter values cannot be changed unless the application is closed by callingclose()and then
initialized withinit()again.
 
> **Warning** Values for the uiTimeShiftBufferSize and uiTimeShiftDuration parameter should be set
carefully because each device has different capabilities and the NexPlayer™ SDK can’t guarantee that the
device has enough free space to store data as the user specifies. If storage becomes full and there is no
available space to save the new data, NexPlayer™ will force the content to resume to use up saved data and
make more storage space available. When the player resumes, onAsyncCmdComplete is called.
 
**Parameters**

| Name | Description | 
|---|---| 
|bEnable| Sets whether to enable or disable the time shift feature.| 
|strFileBufferPath| The folder name where temporary data for time shifting will be stored when there is no more storage available in the memory buffer. If there is enough memory and no folder is needed, this parameter will be NULL.|
|uiTimeShiftBufferSize|Size of the memory buffer for the time shift feature in megabytes (MB). If the size set to this parameter is bigger than the actual memory available, extra realtime data will be saved in the folder set by the parameterstrFileBufferPath.|
|uiTimeShiftDuration|Maximum duration for the time shift feature, or how much time a user can shift back in live content in minutes.| 
|uiMaxBackwardDuration|Maximum duration for the streaming data backup feature, or how much time (of streamed data files preceding the currenttsfile) can be stored. Normally, streamed data files preceding the latest ts file will be deleted to maintain the allowed memory buffer size. However this parameter allows the streamed data files preceding the latesttsfile to be kept and stored if there is free space available. For example when the available memory buffer is larger than the value set for the parameters `uiTimeShiftBufferSize` or `uiTimeShiftDuration`, this parameter allows users to seek backwards in live content during playback for the specified amount of time. If this parameter is set to the default value 1, streamed data files for the 1 minute preceding the latesttsfile will be kept. If this parameter is set to 0, all
remaining storage space will be available to keep previously streamed data files. When this parameter is set to 0 and the parameterstrFileBufferPathis set to save streamed data in another storage folder, this parameter will be automatically set to 1.
 
**Returns**

Zero if successful, or an error code in the event of failure.
 
**See Also**

gotoCurrentLivePosition
 
#### native int SetConfigFilePath(String strConfPath)

Specifies the path to the renderer configuration file.

The renderer configuration file defines which combinations of codec and device should make use of which available renderer. The configuration file is provided with the SDK, but it is the responsibility of the app developer to include the file with the application, and specify the path using this method.

The path must be specified before opening any content, otherwise the renderer configuration file will not be used, and the player will choose the renderer based on the version of Android OS alone without regard to the device model.

**Parameters**

| Name | Description | 
|---|---|
|strConfPath| The path to the configuration file.|
 
**Returns**
 
Always zero, but may change in future versions. The return value should be ignored.
 
> **Deprecated** Do not use.

#### native int SetContrastBrightness (int Contrast, int Brightness)

This method allows NexPlayer™ to adjust the contrast and brightness of the displayed content.

These values can be adjusted either from within the code itself or can be set by the user interface. If setting the values within code, it is important to stay **within** the given range of each parameter. Values outside of these ranges will be ignored and the existing value will be retained, but unexpected results could also be potentially produced.

These settings can be continuously adjusted by calling the method multiple times.

> **Warning** This feature is not supported on devices using the HW decoder. To check whether or not the HW decoder is used, check the value of mVideoCodecClass inNexContentInformation. If mVideoCodecClass =
0, this method can be used to adjust contrast and brightness of displayed content.
 
**Parameters**

| Name | Description | 
|---|---|
|Contrast| This adjusts the contrast of the display. It is an integer from 0 to 255. By default, this value is set to 128.|
|Brightness |This adjusts the brightness of the display. It is an integer from -127 to +128. By default, this value is set to 0.|
 
**Returns**

Always zero, but may change in future versions. The return value should be ignored.
 
#### native int setDebugLogs (int codecLog,int RendererLog,int protocol\_Log)

This method sets the debugging log levels related to codecs, rendering, and protocols in NexPlayer™.

> **Warning** Calls to this method should be made after callinginitbut before callingopen.
 
By default, the parameters codecLog and RendererLog are set to -1 so that they are hidden and protocol\_Log is set to 0 so basic logs are produced. However when debugging applications, they can be set to a higher
integer value so that more logs are generated.

**Parameters**

| Name | Description | 
|---|---|
|codecLog| The level of logs to be generated related to codecs, as an integer.|
|RendererLog| The level of logs to be generated related to rendering, as an integer.|
|protocol\_Log| The level of logs to be generated related to protocols, as an integer.|
 
**Returns**

Zero if successful or a non-zero error code.
 
#### void setDisplay ( SurfaceHolder sh)

This method sets the surface on which video will be displayed.

> **Warning** This is NOT supported with the Java or OpenGL renderers, and should not be called if one of those renderers is in use.
 
This function actually takes theandroid.view.SurfaceHolderassociated with the surface on which the
video will be displayed.

This function should be called from onVideoRenderPrepared after the surface has been created. In addition, if the surface object changes (for example, if theSurfaceHolder’ssurfaceCreatedcallback is after the initial
setup), this function should be called again to provide the new surface.

If the surface object is destroyed (for example, if theSurfaceHolder’ssurfaceDestroyedcallback is after
the initial setup), this function should be called again to notify that the surface was destroyed.

The surface should match the pixel format of the screen, if possible, or should bet set toPixelFormat.RGB\_-
565.

In general, the surface should be created as follows:

```java
Display display = ((WindowManager) getSystemService(Context.WINDOW_SERVICE)).getDefaultDisplay(); 
int displayPixelFormat = display.getPixelFormat();
SurfaceView surfaceView = new SurfaceView(this); 
SurfaceHolder surfaceHolder = mVideoSurfaceView.getHolder();

if( displayPixelFormat == PixelFormat.RGBA_8888 || 
	displayPixelFormat == PixelFormat.RGBX_8888 ||
	displayPixelFormat == PixelFormat.RGB_888 || 
	displayPixelFormat == 5 ) {
	surfaceHolder.setFormat(PixelFormat.RGBA_8888);
} else {
	surfaceHolder.setFormat(PixelFormat.RGB_565);
}

surfaceHolder.addCallback(new SurfaceHolder.Callback() {

	@Override
	public void surfaceDestroyed(SurfaceHolder holder) {
		mSurfaceExists = false; 
			if( mPlaybackStarted ) {
				mNexPlayer.setDisplay(null); 
		}
	}
	
	@Override
	public void surfaceCreated(SurfaceHolder holder) {
		mSurfaceExists = true;
		if( mPlaybackStarted ) {
			mNexPlayer.setDisplay(holder); }
	   }
	    
	@Override
	public void surfaceChanged(SurfaceHolder holder, int format, int width, int height) {
		// do nothing
	} 
});
```

In `onVideoRenderCreate`, the code should ensure that the surface has already been created before passing the surface holder tosetDisplay. BecauseonViewRenderCreatecan run asynchronously, it may need to wait until the surface is created by sleeping and polling.

For example, if using the example code above,onVideoRenderCreatewould wait untilmSurfaceExists becomes true, using something like:

```java
while(!mSurfaceExists)
	Thread.sleep(10);

nexPlayer.setDisplay(surfaceHolder);
```

It is strongly recommended to use `NexVideoRenderer` instead of using this method directly.


**Parameters**
| Name | Description | 
|---|---|
|sh| Theandroid.view.SurfaceHolderholding the surface on which to display video.|
 
#### int setDisplay (SurfaceHolder sh,int surfaceNumber)

This method sets the surface on which video will be displayed.

This is the same as setDisplay(SurfaceHolder), except that it takes an additional surface number parameter. Currently, only one surface at a time is supported, so this additional parameter must always be zero.

In general, it’s better to use setDisplay(SurfaceHolder).

It is strongly recommended to useNexVideoRendererinstead of using this method directly.

**Parameters**
| Name | Description | 
|---|---|
|sh| Theandroid.view.SurfaceHolderholding the surface on which to display video.|
|surfaceNumber| This integer sets the number of additional surfaces (currently must be zero).|
 
**Returns**

Zero if successful, non-zero if there was an error.
 
#### void setDynamicThumbnailListener(IDynamicThumbnailListener listener)

This method sets and registers aIDynamicThumbnailListenerlistener.

**Parameters**

| Name | Description | 
|---|---|
|listener| IDynamicThumbnailListener|
 
**See Also**

NexPlayer.IDynamicThumbnailListener
  
#### native int SetExternalPDFileDownloadSize(long ReceivedSize,long TotalSize)

This method sets the size of the file being downloaded in the Downloader module.

**Parameters**
 
ReceivedSize The size of portion of the file received so far, in bytes (B). TotalSize The total size of the file being downloaded, in bytes (B).
 
**Returns**

Zero if successful, another value in the case of failure.
 
#### void setHTTPABRTrackChangeListener(IHTTPABRTrackChangeListener listener)

This method sets and registers aIHTTPABRTrackChangeListenerlistener.

**Parameters**

| Name | Description | 
|---|---| 
|listener| IHTTPABRTrackChangeListener|
 
**See Also**
 
NexPlayer.IHTTPABRTrackChangeListener
 
#### native int setLicenseBuffer(String strBuffer)

This method inputs the license file information into a NexPlayer™ buffer. This should be called after calls toNexAlFactory::initand before calling `NexPlayer::setNexAlFactory`. The location of the license file included with the NexPlayer™ SDK Java files can be set using the method `setLicenseFile`.

**Parameters**

| Name | Description | 
|---|---|
|strBuffer| Information in the license file, as a string.|
 
**See Also**

 
setLicenseFile(String strPath) for more information.
  
#### native int setLicenseFile (String strPath)

This method sets the path to the specific license file included with the NexPlayer™ SDK.

This should be called after NexAlFactory::init and before NexPlayer::setNexAlFactory. The license file will be included with the NexPlayer™ SDK Java files and when called with this API, an application will be able to input the license file information to run NexPlayer™.

> **Warning** The license file will be updated regularly, so please always check for updates and be sure to replace and use the latest license file in applications built with the NexPlayer™ SDK.
 
**Parameters**

| Name | Description | 
|---|---|
|strPath| Path to the license file, as a string.|
 
**See Also**

setLicenseBuffer(String strBuffer)
 
#####  5.91.3.98 void setLicenseRequestListener (INexDRMLicenseListener listener)

Registers a callback that will be invoked when new events occur.

**Parameters**

| Name | Description | 
|---|---| 
|listener| INexDRMLicenseListener: the object on which methods will be called when new events occur. This must implement the INexDRMLicenseListenerinterface.|
 
#### void setListener (IListener listener)

Registers a callback that will be invoked when new events occur.

The events dispatched to this callback interface serve three functions:

- to provide new video and audio data to the application, for the application to present to the user.
- to notify the application when a command has completed, so that the application can issue any follow-up commands. For example, issuing start when open has completed.
- to notify the application when there are state changes that the application may wish to reflect in the interface.

All applicationsmustimplement this callback and provide certain minimal functionality. See the IListener documentation for a list of events and information on implementing them.

In an Android application, there are two common idioms for implementing this. The most typical is to have the Activity subclass implement the IListenerinterface.

The other approach is to define an anonymous class in-line:

```java
mNexPlayer.setListener(new NexPlayer.IListener() {
	@Override
	public void onVideoRenderRender(NexPlayer mp) {
	// ...event implementation goes here...
	}
	// ...other methods defined by the interface go here...
});
```
**Parameters**

| Name | Description | 
|---|---| 
|listener| The object on which methods will be called when new events occur. This must implement the IListenerinterface.|
 
#### native int setMediaStream (int iAudioStreamId, int iTextStreamId,int iVideoStreamId, int iVideoCustomAttrId)

For media with multiple streams, this method selects the streams that will be presented to the user.

This method should be called to set a specific media stream (video, audio, or text) while NexPlayer™ is playing content with multiple streams. To have NexPlayer™ prefer text streams in a particular language beforeplaying content, the property `PREFER_LANGUAGE` should be set instead.

The full list of available streams (if any) can be found in the mArrStreamInformation array in NexContentInformation. Each stream is either an audio stream or a video stream, and one of each may be selected for presentation to the user. Please see Multi-Audio and Multi-Video Stream Playback for more explanation.

Some streams, for example in Smooth Streaming, may in turn have associated custom attributes. Custom attributes limit playback to a subset of tracks within the stream. Custom attributes are key/value pairs. Each possible pairing (from all the tracks in a stream) is listed in mArrCustomAttribInformation along with an associated integer ID. Specifying that particular integer ID causes only tracks with that particular key/value pairing to beused. Only one ID may be specified at any given time.

**Turning Video On/Off** This method may also be used to turn video off, for example if it is desirable that content continue to play when an application using NexPlayer™ moves into the background.

Setting any of the streams to -2 will disable it or turn it off. There are some restrictions though when using this setting:

- The content must include both audio and video. This means it is not possible to set all of the parameters (iAudioStreamId, iTextStreamId, iVideoStreamId, iVideoCustomAttrId) equal to -2 at once.
- If the player goes into the background, the UImustcall video off (set iVideoStreamId= -2) immediately to provide the audio only stream while the player is in the background.

> **Note** To make it possible for an application to switch content tracks while in the background, it is necessary to make the Application Activity a service and it is recommended that the service be registered with the Android operating system to help ensure it won’t be closed when device resources are managed.
 
Please also see the sample code for more details on how to turn video on and off.

**Parameters**

| Name | Description | 
|---|---| 
|iAudioStreamId| The ID of the stream to use for audio. If this is MEDIA\_STREAM\_DEFAULT\_ID, the initial audio stream played will continue to be used.|
|iTextStreamId| The ID of the stream to use for text (subtitles, captions, and so on). If this is MEDIA\_STREAM\_DEFAULT\_ID, the initial text stream played will continue to be used.|
|iVideoStreamId| The ID of the stream to use for video. If this is MEDIA\_STREAM\_DEFAULT\_ID , the initial video stream played will continue to be used.|
|iVideoCustomAttrId|The ID of the custom attribute to use. If this is MEDIA\_STREAM\_DEFAULT\_ID , the default custom attribute will be used. If no custom attributes are associated with a stream, this will be undefined.|
 
**Returns**

Zero if successful, non-zero if there was an error.
 
#### native int setMediaStreamTrack ( int iAudioStreamId,int iTextStreamId,int iVideoStreamId,int iVideoCustomAttrId, int iMediaType,int iAudioTrackId)

For media with multiple streams, this method selects the streams that will be presented to the user.

This method should be called to set a specific media stream (video, audio, or text) while NexPlayer™ is playing content with multiple streams. To have NexPlayer™ prefer text streams in a particular language beforeplaying content, the property `PREFER_LANGUAGE` should be set instead.

The full list of available streams (if any) can be found in the mArrStreamInformation array in NexContentInformation. Each stream is either an audio stream or a video stream, and one of each may be selected for presentation to the user. Please see Multi-Audio and Multi-Video Stream Playback for more explanation.

In case of DASH streamming service, user can set the audioTrackID in the corresponding audioStreamID. This API is the same as setMediaStream(), but it supports the setting of audioTrackID at the same time when using DASH streamming service.

Some streams, for example in Smooth Streaming, may in turn have associated custom attributes. Custom attributes limit playback to a subset of tracks within the stream. Custom attributes are key/value pairs. Each possible pairing (from all the tracks in a stream) is listed in mArrCustomAttribInformation along with an associated integer ID. Specifying that particular integer ID causes only tracks with that particular key/value pairing to beused. Only one ID may be specified at any given time.

**Turning Video On/Off** This method may also be used to turn video off, for example if it is desirable that content continue to play when an application using NexPlayer™ moves into the background.

Setting any of the streams to -2 will disable it or turn it off. There are some restrictions though when using this setting:

- The content must include both audio and video. This means it is not possible to set all of the parameters (iAudioStreamId,iTextStreamId,iVideoStreamId,iVideoCustomAttrId) equal to -2 at once. 
- If the player goes into the background, the UImustcall video off (setiVideoStreamId= -2) immediately to provide the audio only stream while the player is in the background.

> **Note** To make it possible for an application to switch content tracks while in the background, it is necessary to make the Application Activity a service and it is recommended that the service be registered with the Android operating system to help ensure it won’t be closed when device resources are managed.
 
Please also see the sample code for more details on how to turn video on and off.

**Parameters**

| Name | Description | 
|---|---| 
|iAudioStreamId| The ID of the stream to use for audio. If this is MEDIA\_STREAM\_DEFAULT\_ID , the initial audio stream played will continue to be used.| 
| iTextStreamId| The ID of the stream to use for text (subtitles, captions, and so on). If this is MEDIA\_STREAM\_DEFAULT\_ID , the initial text s|tream played will continue to be used.
|iVideoStreamId| The ID of the stream to use for video. If this is MEDIA\_STREAM\_DEFAULT\_ID , the initial video stream played will continue to be used.|
|iVideoCustomAttrId|The ID of the custom attribute to use. If this is MEDIA\_STREAM\_DEFAULT\_ID , the default custom attribute will be used. If no custom attributes are associated with a stream, this will be undefined.|
| iMediaType | The type of media stream to change the track. ( now only support MEDIA\_STREAM\_TYPE-_AUDIO )
| iAudioTrackId | The ID of the audio track.|
 
**Returns**

 
Zero if successful, non-zero if there was an error.
 
#### native int setMediaTrack (int iMediaType, int iTrackId)

For a stream with multiple tracks, this method selects the track that will be presented to the user.

This method should be called to set a specific media track (audio only) while NexPlayer is playing content with multiple tracks.

**Parameters**

| Name | Description | 
|---|---|
|iMediaType| The type of media stream to change the track (it supports MEDIA\_STREAM\_TYPE\_AUDIO).|
|iTrackId| The ID of the track.. `mTrackID`.|
 
**Returns**
 
Zero if successful, non-zero if there was an error.
 
5.91.3.103 int setNetAddrTable(NexNetAddrTable table,int nNetAddrTableType)

This method sets a table and table type to be used by the NexPlayer™ to retrieve host information when custom IP addresses should be used.

**Parameters**

| Name | Description | 
|---|---|
|table| The table to use, containing the hostname and its corresponding custom IP address.|
|nNetAddrTableType| The type of table to be used, setting different options of how to retrieve an IP address with the given host information. This should be one of:|
 
- NETADDR\_TABLE\_OVERRIDE: The table will override existing host database information.
- NETADDR\_TABLE\_FALLBACK: The table will be used as a fallback option to retrieve host information.

**Returns**
 
0 if successfully set; non-zero if there was an error.
 
#### void setNexALFactory (NexALFactoryalFactory)

Sets the NexALFactory in order to inform what type of codec NexPlayer™ will use.

> **Warning** This must be called before NexPlayer.init methods. For more information, see the NexPlayer.init.

**Parameters**

| Name | Description | 
|---|---|
| alFactory| The NexALFactory instance.|
 
#### void setNexMediaDrmKeyServerUri ( String keyUri)

This sets the Key Server’s URL to obtain keys to decrypt encrypted content.

> **Warning** This must be called before NexPlayer.open.
 
**Parameters**

| Name | Description | 
|---|---| 
|keyUri| the Key Server’s URL|
 
#### void setNexMediaDrmOptionalHeaderFields (HashMap<String, String> optionalHeaderFields)

This method sets optionalParameters when sending requests to the Key Server of MediaDrm.

> **Warning** This must be called before `NexPlayer.open`.
 
**Parameters**

| Name | Description | 
|---|---|
|optionalHeaderFields| HashMap: are included in the key request message to allow a client application to provide additional message parameters to the server.
 
#### void setOfflineKeyListener (IOfflineKeyListener OfflineKeyListener)

This method registers an Offline Key listener for managing offline keys.

> **Warning** This must be called before `NexPlayer.open`.
 
**Parameters**

| Name | Description | 
|---|---| 
|OfflineKeyListener| IOfflineKeyListener|

**See Also**
 
- NexPlayer.IDynamicThumbnailListener
 
#### native int setOptionDynamicThumbnail ( int option,int param1,int param2)

This method sets option parameters related to the Dynamic Thumbnail feature in Smooth Streaming when handling thumbnail data.

**Parameters**

| Name | Description | 
|---|---| 
|option| The option property to set thumbnail data.|
|param1 | The first parameter of the option property.|
|param2 | The second parameter of theoptionproperty. If the option being set only needs one parameter, param2 will be NULL.|
 
**Returns**

Zero if successful, or an error code in the event of failure.
 
#### native int setOutputPos ( int iX,int iY,int iWidth,int iHeight)

This method sets the output video’s position and size.

The position is relative to and within the surface specified in setDisplay or relative to and within the application’s OpenGL surface, if the OpenGL renderer is being used.

X and Y are the distances from the upper-left corner. All units are in pixels and are resolution-dependent.

If the video is larger than the surface, or part of it is outside the surface, it will be cropped appropriately. Negative values are therefore acceptable for iX and iY.

> **Warning** setOutputPos is not supported when the render mode is NEX\_USE\_RENDER\_IOMX.
 
**Parameters**

| Name | Description | 
|---|---| 
|iX| The video display’s horizontal (X) position.|
|iY| The video display’s vertical (Y) position.|
|iWidth| The width of the video display.|
|iHeight| The height of the video display.|
 
**Returns**
 
Always zero, but may change in future versions; the return value should be ignored.
 
#### native int setProperties(int property,int value)

Sets the value of an individual NexPlayer™ integer property based on the numerical ID of the property.

Normally, setProperty should be used instead of this method. Use this methodonlyif you have a numeric property code.

For a full list of properties, see the NexProperty enum. To get the numeric code for a property, call the getPropertyCode method on the enum member.

For example:

```java
// enable RTSP support
setProperties(NexProperty.SUPPORT_RTSP.getPropertyCode(), 1);
```

**Parameters**

| Name | Description | 
|---|---| 
|property| The numeric property code identifying the property to set.|
|value| The new value for the property.|
 
**Returns**

Zero if the property was set successfully; non-zero if there was an error.
 
#### native int setProperties (int property,String value)

Sets the value of an individual NexPlayer™ string property based on the numerical ID of the property.

This is a string version of setProperties(int, int).

Normally, setProperty should be used instead of this method. Use this methodonlyif you have a numeric property code.

**Parameters**
|---|---| 
|property| The numeric property code identifying the property to set.|
|value| The new string  value for the property.|
 
**Returns**

 
Zero if the property was set successfully; non-zero if there was an error.
 
#### native int setProperties(int property, byte[] value)

> **Note** For internal NexStreaming use only. Please do not use.
 
#### int setProperty(NexProperty property,int value)

Sets the value of an individual NexPlayer™ property.

Properties control the behavior of NexPlayer™ and the features that are enabled.

This sets integer properties; use the setProperty(NexProperty, String) version of this method for string properties. If any properties need to be set before the player is opened, it is possible to call this method before calling open.

**See Also**
 
NexProperty for more details on specific properties.
 
**Parameters**

| Name | Description | 
|---|---|  
|property| The property to set.|
|value| The new value for the property.|
 
**Returns**

Zero if the property was succesfully set; non-zero if there was an error.
 
#### int setProperty(NexProperty property, String value)

Sets the value of an individual NexPlayer™ property.

Properties control the behavior of NexPlayer™ and the features that are enabled.

This sets string properties; use the setProperty(NexProperty, int) version of this method for integer properties. If any properties need to be set before the player is opened, it is possible to call this method before calling open.

**See Also**

NexProperty for details.
 
**Parameters**

| Name | Description | 
|---|---|  
|property| The property to set.|
|value| The new string value for the property.|
 
**Returns**
 
Zero if the property was succesfully set; non-zero if there was an error.
 
#### void setProxyInfo(String proxyAddress,int proxyPort)

This method sets the proxy setting for the requests, **only if the actual network configuration of the device has it.**

**Parameters**

| Name | Description | 
|---|---|  
|proxyAddress| The proxy server address to use.|
|proxyPort| The proxy server port number to use.|
 
The default value of proxyAddress is null. The default value of proxyPort is -1.

> **Deprecated** This API will be deprecated. Instead of this API, please use setProperties with NexProperty.PROXY\_ADDRESS and NexProperty.PROXY\_PORT values.
 
#### native int setRenderOption(int iFlag)

This function configures the paint flags used with the Android bitmap rendering module.

There are multiple rendering modules that can be used for displaying video and NexPlayer™ automatically selects the best one for the given content and device.

**See Also**
 
NexPlayer.init for more details on possible rendering modules.
 
In the case where the rendering module uses bitmaps provided through the Android API, the rendering options
specified here are used to set up the flags on theandroid.os.Paintobject that is used to display the bitmap.

For all other rendering modules, the values set here are ignored.

**Parameters**

| Name | Description | 
|---|---|  
|iFlag| This is an integer representing options for video rendering. This can be zero or more of the following values, combined together using a bitwiseOR. Each value corresponds to an Android API flag available on a Paint object.|
 
- **RENDER\_MODE\_VIDEO\_NONE (0x00000000)** No special paint flags are set.
- **RENDER\_MODE\_VIDEO\_FILTERBITMAP (0x00000001)** Corresponds to
    android.os.Paint.FILTER\_BITMAP\_FLAG.
- **RENDER\_MODE\_VIDEO\_ANTIALIAS (0x00000002)** Corresponds toandroid.-
    os.Paint.ANTI\_ALIAS\_FLAG.
- **RENDER\_MODE\_VIDEO\_DITHERING (0x00000004)** Corresponds toandroid.-
    os.Paint.DITHER\_FLAG.
- **RENDER\_MODE\_VIDEO\_ALLFLAG (0xFFFFFFFF)** Enables all options.

**Returns**

Always zero, but may change in future versions; the return value should be ignored.
 
#### native int setUserCookie(String strCookie)

This method sets a user cookie to be used while playing content.

In prior versions of the NexPlayer™ SDK, it was only possible to set a user cookie before content was opened in the player but this method makes it possible to set a cookie while content is playing. The cookie set with this method may also be different than an initial cookie set.

**Parameters**

| Name | Description | 
|---|---|  
|strCookie| The user cookie to set, as a string. When setting a cookie string, it should start with "Set-Cookie:". For example:<br>`mNexPlayer.setUserCookie("Set-Cookie: [cookie string]");`<br>When setting two or more cookies, it should start with "Cookie:" and each cookies are separated by ";". For example:<br> `mNexPlayer.setUserCookie("Cookie: [cookie string1];[cookie string2];[cookie string3]...");`|
 
**Returns**
 
Zero if successful, non-zero if there was an error.
  
#### int setVideoBitrates(int[] bitrates)

This method allows specific subtracks to be selected and played based on the bitrates of the tracks in HLS content.

Only the tracks with the bitrates passed to this method with the parameterbitrateswill be played by NexPlayer™.

**Parameters**

| Name | Description | 
|---|---|  
|bitrates| The bitrates of the HLS content subtracks to play, as an integer array.|
 
**Returns**

Zero if successful or a non-zero error code.
 
#### int setVideoBitrates (int[] bitrates, int option)

This method allows specific subtracks to be selected and played based on the bitrates of the tracks in HLS content.

Only the tracks with the bitrates passed on this method with the parameterbitrateswill be played by Nex-
Player™. However, choosing a different option with the parameteroptionallows NexPlayer™ to choose and play
the selected subtracks based on the passed bitrates differently.

**Parameters**

| Name | Description | 
|---|---|  
|bitrates| The bitrates of the HLS content subtracks to play, as an integer array.|
|option| How HLS subtracks should be played based on the bitrates selected inbitrates. This will be one of:|
 
- `AVAILBITRATES_NONE` = 0x00000000: Default. No restriction on subtracks other than the bitrates selected inbitrates.
- `AVAILBITRATES_MATCH` = 0x00000001: Only use subtracks which have exact same bitrate as the selected bitrates passed inbitrates.
- `AVAILBITRATES_NEAREST` = 0x00000002: Only use subtracks which have the nearest bitrates to the target bitrates described in the list passed inbitrates. For example, if the target bitrates passed are [300K, 600K] and the HLS playlist includes 100K,200K, 500K, 700K tracks, only the 200K (close to 300K) and 500K (close to 600K) tracks will be used.
- `AVAILBITRATES_HIGH` = 0x00000003: Only use subtracks which have bitrates equal to or higher than the target bitrate. The first bitrate in the list passed in bitrates is  the target bitrate, the rest will be ignored.
- `AVAILBITRATES_LOW` = 0x00000004: Only use subtracks which have bitrates equal to or lower than the target bitrate. The first bitrate in the list passed in bitrates is the target bitrate, the rest will be ignored.
- `AVAILBITRATES_INSIDERANGE` = 0x00000005: Only use subtracks which have bitrates inside the range defined by the bitrates passed inbitrates. The first bitrate in the list is taken as the lower boundary, the second as the upper boundary, and the rest of the list will be ignored. Subtracks with bitrates between the lower and upperboundaries will be used.

**Returns**

Zero if successful or a non-zero error code.
  
#### void setVideoRendererListener (IVideoRendererListener listener)

Registers a callback that will be invoked when new video renderer events occur.

> **Note** All applications **must** implement this callback and provide certain minimal functionality. See the IVideoRendererListener documentation for a list of events and information on implementing them.
 
In an Android application, there are two common idioms for implementing this. The most typical is to have the Activity subclass implement the IVideoRendererListener interface.

The other approach is to define an anonymous class in-line:

```java
mNexPlayer.setVideoRendererListener(new NexPlayer.IVideoRendererListener() {
	@Override
	public void onVideoRenderRender(NexPlayer mp) {
	// ...event implementaton goes here...
	}
	// ...other methods defined by the interface go here...
});
```

**Parameters**

| Name | Description | 
|---|---| 
|listener| The object on which methods will be called when new events occur. This must implement the IVideoRendererListener interface.|
 
**See Also**

- renderers The introductory section on renderers in the NexPlayer™ SDK.
- NexVideoRenderer
- NexPlayer.IVideoRendererListener
 
#### native int setVolume (float fGain)

This sets the player output volume.

This affects the output of the player before it is mixed with other sounds. Normally, this should be left at the default setting of 1.0, and the volume should be adjusted via the device master volume setting (adjustable by the user via the hardware volume buttons on the device). However, if the application contains multiple audio sources (or if there is other audio being played on the device), this property can be used to reduce the NexPlayer™ volume in relation to other sounds.

The valid range for this property is 0.0∼1.0. A value of 0.0 will silence the output of the player, and a value of 1.0 (the default) plays the audio at the original level, affected only by the device master volume setting (controlled by the hardware buttons).

It is not recommended to use this setting for volume controlled by the user; that is best handled by adjusting the device master volume.

**Parameters**

| Name | Description | 
|---|---|  
|fGain| This is afloatbetween 0.0 and 1.0. It is set to 1.0 by default.|
 
#### int start ( int msec)

Starts playing media from the specified timestamp.

The media must have already been successfully opened with open. This only works for media that is in the stopped state; to change the play position of media that is currently playing or paused, call seek instead.

When this operation completes, onAsyncCmdComplete is called with one of the following command constants
(depending on the type specified in the open call):

- NEXPLAYER\_ASYNC\_CMD\_START\_LOCAL
- NEXPLAYER\_ASYNC\_CMD\_START\_STREAMING
- NEXPLAYER\_ASYNC\_CMD\_START\_STORE\_STREAM

Success or failure of the operation can be determined by checking theresultargument passed toonAsync-
CmdComplete. If the result is 0, the media was successfully opened; if it is any other value, the operation failed.

**Parameters**

| Name | Description | 
|---|---|  
|msec| The offset (in milliseconds) from the beginning of the media at which to start playback. This should be zero to start at the beginning. This parameter will be ignored if content is opened with the NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAM parameter since the content will be stored instead of played. This parameter must be set to a valid value within the seekable range. The value of the seekable range can be obtained using the `getSeekableRangeInfo()` API. If the content is a live stream, it is recommended to use the LIVE\_VIEW\_OPTION property.|
 
**Returns**

The status of the operation. This is zero in the case of success, or a non-zero NexPlayer™ error code in the
case of failure.
 
> **Note** This only indicates the success or failure ofstartingthe operation. Even if this reports success, the operation may still fail later, asynchronously, in which case the application is notified in `onAsyncCmdComplete`.
 
#### native int start (int msec,boolean pauseAfterReady)

Starts playing media from the specified timestamp.

The media must have already been successfully opened with open. This only works for media that is in the stopped state; to change the play position of media that is currently playing or paused, call seek instead.

When this operation completes, onAsyncCmdComplete is called with one of the following command constants
(depending on thetypespecified in theopencall):

- NEXPLAYER\_ASYNC\_CMD\_START\_LOCAL
- NEXPLAYER\_ASYNC\_CMD\_START\_STREAMING
- NEXPLAYER\_ASYNC\_CMD\_START\_STORE\_STREAM

Success or failure of the operation can be determined by checking theresultargument passed toonAsync-
CmdComplete. If the result is 0, the media was successfully opened; if it is any other value, the operation failed.

**Parameters**

| Name | Description | 
|---|---|  
|msec| The offset (in milliseconds) from the beginning of the media at which to start playback. This should be zero to start at the beginning. This parameter will be ignored if content is opened with NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAMsince the content will be stored instead of played. This parameter must be set to a valid value within the seekable range. The value of the seekable range can be obtained using the `getSeekableRangeInfo()` API. If the content is a live stream, it is recommended to use the LIVE\_VIEW\_OPTION property.|
|pauseAfterReady| If this value is true, NexPlayer™ will pause just after buffering and before play This parameter will be ignored if content is opened with the NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAM parameter.  
Note that if this value isTRUE, NexPlayer’s state will be changed to NEXPLAYER\_STATE\_PAUSE when initial
buffering is done. This could take some time.|

**Returns**
 
The status of the operation. This is zero in the case of success, or a non-zero NexPlayer™ error code in the
case of failure.
 
> **Note** This only indicates the success or failure ofstartingthe operation. Even if this reports success, the operation may still fail later, asynchronously, in which case the application is notified inonAsyncCmdComplete.
 
#### int stop ()

This function stops the current playback.

**Returns**

Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.

#### native int timeBackward(int skiptime)

Timeshift interface; not available in current version.

> **Deprecated** Not available in current version; do not use.

#### native int timeForward(int skiptime)

Timeshift interface; not available in current version.

> **Deprecated** Not available in current version; do not use.

#### native int timePause()

Timeshift interface; not available in current version.

> **Deprecated** Not available in current version; do not use.

#### native int timeResume()

Timeshift interface; not available in current version.

> **Deprecated** Not available in current version; do not use.

5.91.3.129 native int timeStart(String AudioFile,String VideoFile,int maxtime,int maxfilesize)

Timeshift interface; not available in current version.

> **Deprecated** Not available in current version; do not use.

#### native int timeStop()

Timeshift interface; not available in current version.

> **Deprecated** Not available in current version; do not use.

#### void videoOnOff(boolean bOn)

This method turns video rendering on or off.

If video rendering is turned off, any existing frame will remain on the display. If you wish to clear it, you may directly draw to the surface and fill it with black pixels after turning off video rendering.

> **Warning** This method only turns video rendering on or off. Video decoding is still performed.
 
**Parameters**

| Name | Description | 
|---|---| 
|bOn| TRUE to render video, FALSE to turn off video rendering.|
 
#### native int videoOnOff(int bOn,int bErase)

This method turns video rendering on or off.

> **Warning** This method is deprecated. Use of videoOnOff(boolean) is recommended over of this function.
 
> **Deprecated** Use `videoOnOff(boolean)` instead of this method.

**Parameters**

| Name | Description | 
|---|---| 
|bOn| 1 to turn on video rendering, 0 to turn off video rendering. Other values are reserved and
should not be used.|
|bErase| This parameter is reserved; it must be zero.|
 
**Returns**
 
Always zero, but may change in future versions; the return value should be ignored.
 

#### final int AVAILBITRATES\_HIGH = 0x00000003 [static]

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int AVAILBITRATES\_INSIDERANGE = 0x00000005 [static]

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.

#### final int AVAILBITRATES\_LOW = 0x00000004 [static]

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int AVAILBITRATES\_MATCH = 0x00000001 [static]

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int AVAILBITRATES\_NEAREST = 0x00000002 [static]

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int AVAILBITRATES\_NONE = 0x00000000 [static]

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int MEDIA\_STREAM\_DEFAULT\_ID = 0xFFFFFFFF [static]

Possible value for arguments to NexPlayer.setMediaStream().

#### final int MEDIA\_STREAM\_DISABLE\_ID = 0xFFFFFFFE [static]

Possible value for arguments to NexPlayer.setMediaStream().

#### final int MEDIA\_STREAM\_TYPE\_AUDIO = 0x00 [static]

Possible value for NexStreamInformation.mType; see there for details.

#### final int MEDIA\_STREAM\_TYPE\_TEXT = 0x02 [static]

Possible value for NexStreamInformation.mType; see there for details.

#### final int MEDIA\_STREAM\_TYPE\_VIDEO = 0x01 [static]

Possible value for NexStreamInformation.mType; see there for details.

#### final int MEDIA\_TRACK\_DEFAULT\_ID = 0xFFFFFFFF [static]

Possible value for arguments to NexPlayer.setMediaTrack().

#### final int MEDIA\_TRACK\_DISABLE\_ID = 0xFFFFFFFE [static]

Possible value for arguments to NexPlayer.setMediaTrack().

#### final int MEDIA\_TRACK\_TYPE\_AUDIO = 0x10 [static]

Possible value for NexStreamInformation.mType; see there for details.

#### final int NEX\_AS\_CINEMA\_SOUND = 0x00000006 [static]

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final int NEX\_AS\_EARCOMFORT = 0x00000001 [static]

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final int NEX\_AS\_MUSIC\_ENHANCER = 0x00000004 [static]

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final int NEX\_AS\_REVERB = 0x00000002 [static]

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final int NEX\_AS\_STEREO\_CHORUS = 0x00000003 [static]

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final String NEX\_DEVICE\_USE\_ANDROID\_3D = "Android 3D" [static]

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.

#### final String NEX\_DEVICE\_USE\_AUTO = "Auto" [static]

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.
 
#### final String NEX\_DEVICE\_USE\_JAVA = "JAVA" [static]

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.

#### final String NEX\_DEVICE\_USE\_ONLY\_ANDROID = "Android" [static]

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.

#### final String NEX\_DEVICE\_USE\_OPENGL = "OPENGL" [static]

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.

#### final int NEXDOWNLOADER\_ASYNC\_CMD\_CLOSE = 0x00200002 [static]

Possible value for msg parameter of onDownloaderAsyncCmdComplete.

#### final int NEXDOWNLOADER\_ASYNC\_CMD\_OPEN = 0x00200001 [static]

Possible value for msg parameter of onDownloaderAsyncCmdComplete.

#### final int NEXDOWNLOADER\_ASYNC\_CMD\_START = 0x00200003 [static]

Possible value for msg parameter of onDownloaderAsyncCmdComplete.

#### final int NEXDOWNLOADER\_ASYNC\_CMD\_STOP = 0x00200004 [static]

Possible value for msg parameter of onDownloaderAsyncCmdComplete.

#### final int NEXDOWNLOADER\_OPEN\_TYPE\_APPEND = 1 [static]

This is a possible value for the parameter eType in the method DownloaderOpen().

#### final int NEXDOWNLOADER\_OPEN\_TYPE\_CREATE = 0 [static]

This is a possible value for the parameter eType in the method DownloaderOpen().

#### final int NEXDOWNLOADER\_STATE\_CLOSED = 2 [static]

This is a possible value for the parameter param2 of onDownloaderEventState.

#### final int NEXDOWNLOADER\_STATE\_DOWNLOAD = 4 [static]

This is a possible value for the parameter param2 of onDownloaderEventState.

#### final int NEXDOWNLOADER\_STATE\_NONE = 0 [static]

This is a possible value for the parameter param2 of onDownloaderEventState.

#### final int NEXDOWNLOADER\_STATE\_STOP = 3 [static]

This is a possible value for the parameter param2 of onDownloaderEventState.

#### final int NEXPLAYER\_ASYNC\_CMD\_FASTPLAY\_START = 0x00000027 [static]

Possible value for command parameter of onAsyncCmdComplete.
 
#### final int NEXPLAYER\_ASYNC\_CMD\_FASTPLAY\_STOP = 0x00000028 [static]

Possible value for command parameter of onAsyncCmdComplete.
 
#### final int NEXPLAYER\_ASYNC\_CMD\_NONE = 0x00000000 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_OPEN\_LOCAL = 0x00000001 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_OPEN\_STORE\_STREAM = 0x00000101 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_OPEN\_STREAMING = 0x00000002 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_OPEN\_TV = 0x00000003 [static]

Possible value for command parameter of onAsyncCmdComplete.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_PAUSE = 0x00000009 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_RECORD\_PAUSE = 0x0000001C [static]

Possible value for command parameter of onAsyncCmdComplete.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_RECORD\_RESUME = 0x0000001D [static]

Possible value for command parameter of onAsyncCmdComplete.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_RECORD\_START = 0x0000001A [static]

Possible value for command parameter of onAsyncCmdComplete.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_RECORD\_STOP = 0x0000001B [static]

Possible value forcommandparameter of onAsyncCmdComplete.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_REINITVIDEO = 0x00000013 [static]

Possible value for command parameter of onAsyncCmdComplete.

> **Deprecated** Ignore if the application receives this event.
 
#### final int NEXPLAYER\_ASYNC\_CMD\_RESUME = 0x0000000A [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_SEEK = 0x0000000B [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_SET\_MEDIA\_STREAM = 0x00000031 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_SET\_MEDIA\_STREAM\_TRACK = 0x00000033 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_SET\_MEDIA\_TRACK = 0x00000032 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_START\_LOCAL = 0x00000005 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_START\_STORE\_STREAM = 0x00000102 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_START\_STREAMING = 0x00000006 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_START\_TV = 0x00000007 [static]

Possible value for command parameter of onAsyncCmdComplete.

Deprecated Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_STEP\_SEEK = 0x0000000C [static]

Possible value for command parameter of onAsyncCmdComplete.

Deprecated Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_STOP = 0x00000008 [static]

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_TIMESHIFT\_BACKWARD = 0x00000026 [static]

Possible value for command parameter of onAsyncCmdComplete.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_TIMESHIFT\_CREATE = 0x00000021 [static]

Possible value for command parameter of onAsyncCmdComplete.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_TIMESHIFT\_DESTROY = 0x00000022 [static]

Possible value for command parameter of onAsyncCmdComplete.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_TIMESHIFT\_FORWARD = 0x00000025 [static]

Possible value forcommandparameter of `onAsyncCmdComplete`.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_TIMESHIFT\_PAUSE = 0x00000023 [static]

Possible value for command parameter of `onAsyncCmdComplete`.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_ASYNC\_CMD\_TIMESHIFT\_RESUME = 0x00000024 [static]

Possible value for command parameter of `onAsyncCmdComplete`.

> **Deprecated** Experimental; may or may not be present in future versions.

#### final int NEXPLAYER\_SIGNAL\_STATUS\_NORMAL = 0 [static]

Normal signal status; see `onSignalStatusChanged` for details.

#### final int NEXPLAYER\_SIGNAL\_STATUS\_OUT = 2 [static]

No signal (out of service area); see `onSignalStatusChanged` for details.

#### final int NEXPLAYER\_SIGNAL\_STATUS\_WEAK = 1 [static]

Weak signal status; see `onSignalStatusChanged` for details.

#### final int NEXPLAYER\_SOURCE\_TYPE\_LOCAL\_NORMAL = 0 [static]

Treats path as a local media file; a possible value for the type parameter of NexPlayer.open.

#### final int NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAM = 2 [static]

Treats path as a URL to a streaming media source to be stored for offline playback; a possible value for the type parameter of NexPlayer.open.

#### final int NEXPLAYER\_SOURCE\_TYPE\_STREAMING = 1 [static]

Treats path as a URL to a streaming media source; a possible value for the type parameter of NexPlayer.open.

#### final int NEXPLAYER\_STATUS\_REPORT\_AUDIO\_GET\_CODEC\_FAILED = 0x1 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_AUDIO\_INIT\_FAILED = 0x3 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_AVMODE\_CHANGED = 0xa [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_CONTENT\_INFO\_UPDATED = 0x9 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_DISCONTINUITY\_EXIST = 0x12 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_DOWNLOAD\_PROGRESS = 0x80 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_DSI\_CHANGED = 0x7 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_EXTERNAL\_DOWNLOAD\_CANCELED = 0x20 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_HTTP\_INVALID\_RESPONSE = 0xb [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_MAX = 0xFFFFFFFF [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_MINMAX\_BANDWIDTH\_CHANGED = 0x21 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_NONE = 0x0 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_OBJECT\_CHANGED = 0x8 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_STREAM\_CHANGED = 0x6 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_STREAM\_RECV\_PAUSE = 0x60 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_STREAM\_RECV\_RESUME = 0x61 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_TARGET\_BANDWIDTH\_CHANGED = 0x22 [static] , [protected]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_TRACK\_CHANGED = 0x5 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_VIDEO\_GET\_CODEC\_FAILED = 0x2 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_VIDEO\_INIT\_FAILED = 0x4 [static]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_TRACK\_ENABLE\_OPTION\_DISABLED\_TEMPORARY = 1 [static]

possible value for the NexPlayer.enableTrack method

Enable the track which is disabled by temporary content issues; possible value for the NexPlayer.enableTrack
method

#### final int OPTION\_DYNAMIC\_THUMBNAIL\_INTERVAL = 1 [static]

This is one possible option property for the Dynamic Thumbnail feature in Smooth Streaming content and a possible value of the option parameter of `setOptionDynamicThumbnail`.
 
#### final int RENDER\_MODE\_VIDEO\_ALLFLAG = 0xFFFFFFFF [static]

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### final int RENDER\_MODE\_VIDEO\_ANTIALIAS = 0x00000004 [static]

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### final int RENDER\_MODE\_VIDEO\_DITHERING = 0x00000002 [static]

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### final int RENDER\_MODE\_VIDEO\_FILTERBITMAP = 0x00000001 [static]

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### final int RENDER\_MODE\_VIDEO\_NONE = 0x00000000 [static]

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### int RTSP\_METHOD\_ALL [static]

Initial value:

```
= ( RTSP\_METHOD\_DESCRIBE
| RTSP\_METHOD\_SETUP
| RTSP\_METHOD\_OPTIONS
| RTSP\_METHOD\_PLAY
| RTSP\_METHOD\_PAUSE
| RTSP\_METHOD\_GETPARAMETER
| RTSP\_METHOD\_TEARDOWN )
```

This is a possible value for the methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_DESCRIBE = 0x00000001 [static]

This is a possible value for themethodsparameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_GETPARAMETER = 0x00000020 [static]

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_OPTIONS = 0x00000004 [static]

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_PAUSE = 0x00000010 [static]

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_PLAY = 0x00000008 [static]

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_SETUP = 0x00000002 [static]

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_TEARDOWN = 0x00000040 [static]

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.


### NexPlayer.NexRTStreamInformation Class Reference

> **Note** For internal use only.

**Protected Attributes**

- String **mMasterMpd**
- String **mMasterMpdUrl**
- String **mInitialMpd**
- String **mInitialMpdUrl**
- String **mStartSegUrl**
- long **mCurNetworkBw**
- long **mCurTrackBw**
- long **mNumOfRedirect**
- long **mNumOfSegDownRate**
- long **mNumOfSegFailToParse**
- long **mNumOfSegInBuffer**
- long **mNumOfSegReceived**
- long **mNumOfSegFailToReceive**
- long **mNumOfSegRequest**
- long **mNumOfSegTimeout**
- long **mNumOfTrackSwitchDown**
- long **mNumOfTrackSwitchUp**
- long **mNumOfBytesRecv** 

 
### NexSessionData Class Reference

#### String mValue

It is identified by a string, DATA-ID.

If LANGUAGE is specified, this attribute must be included in a human-readable form in the specified language.

### NexSoundEffect Class Reference

**Static Public Attributes**

- `static final int **SOUND\_EFFECT\_NONE** = 0x00`
- `static final int **SOUND\_EFFECT\_NEXSOUND** = 0x01`
- `static final int **SOUND\_EFFECT\_HEADPHONE\_X** = 0x02`
- `static final int **SOUND\_EFFECT\_HEAD\_TRACKING** = 0x04`
- `static final int **SOUND\_EFFECT\_3DAUDIO\_SOLUTION01** = 0x08`

#### int InstallSoundEffectLicenseFile ( String licenseFilePath )

This method sets the licenseFilePath.

It is only supported with the SOUND\_EFFECT\_HEAD\_TRACKING option.

**Parameters**

| Name            | Description              |
|-----------------|------|
| licenseFilePath | Path to the license file |
 
#### int InstallSoundEffectLicenseKeyData ( byte[ ] licenseKeyData )

This method sets the LicenseKeyData.

It is only supported with the SOUND\_EFFECT\_HEAD\_TRACKING option.

**Parameters**

| Name            | Description              |
|-----------------|------|
| licenseFilePath | Key data in the license file |
 
#### int setSoundEffectEuler ( float fAzimuth, float fElevation )

This method sets the fAzimuth and fElevation euler angles.

It is only supported with the SOUND\_EFFECT\_HEAD\_TRACKING option.

**Parameters**

| Name            | Description              |
|-----------------|------|
| fAzimuth | The fAzimuth is azimuth (float, in degrees). |
| fElevation | The fElevation value is elevation (float, in degrees). |
 
#### int setSoundEffectEuler ( float pitch, float yaw, float roll )

This method sets the pitch, yaw and roll euler angles.

It is only supported with the SOUND\_EFFECT\_3DAUDIO\_SOLUTION01 option.

**Parameters**

| Name            | Description              |
|-----------------|------|
| pitch | The pitch is pitch degrees around the x axis. |
| yaw | The yaw value is yaw degrees around the y axis. |
| roll | The roll value is roll degrees around the z axis. |

 
#### int setSoundEffectOutputChannel ( int numChannels )

This method sets the OutputChannel.

It is only supported with the SOUND\_EFFECT\_HEAD\_TRACKING option.

**Parameters**

| Name            | Description              |
|-----------------|------|
| numChannels | The numChannels is channel number of output. |
 
#### int setSoundEffectPositionAngle ( float x, float y, float z, float angle )

This method sets the Position Vector and Angle.

It is only supported with the SOUND\_EFFECT\_3DAUDIO\_SOLUTION01 option.

**Parameters**

| Name            | Description              |
|-----------------|------|
| x | The z position that represents a vector or point in 3D space. |
| y | The y position that represents a vector or point in 3D space. |
| z | The z position that represents a vector or point in 3D space. |
| angle | The angle rotating degrees about axis(x or y or z). |

 
#### int setSoundEffectQuaternion ( float w, float x, float y, float z )

This method sets the quaternion value.

It is only supported with the SOUND\_EFFECT\_3DAUDIO\_SOLUTION01 or the SOUND\_EFFECT-HEAD\_TRACK-
ING option.

**Parameters**

| Name            | Description              |
|-----------------|------|
| w | The w of quaternion that used to represent a rotation in 3D space. |
| x | The x of quaternion that used to represent a rotation in 3D space. |
| y | The y of quaternion that used to represent a rotation in 3D space. |
| z | The z of quaternion that used to represent a rotation in 3D space. |
 
### NexStatisticsMonitor Class Reference

This class defines a statistics monitoring module to be used during playback of HLS, DASH or SS content with NexPlayer.

Implementing this class in an application makes it easier to monitor different kinds of statistics at regular intervals during playback of HLS, DASH or SS content in order to for example have more details about player performance.

To monitor HLS, DASH or SS playback statistics, after NexPlayer™ is created and initialized but before content is opened, an application must:

1. First, create an instance of this NexStatisticsMonitor class,
2. Next, set a listener to receive the events reporting statistics information with IStatisticsListener,
3. lastly, if desired, the time interval at which statistics are monitored can be changed with calls to setDuration.

Depending on what information about playback is needed, different statistics can be retrieved from NexPlayer™, including general playback statistics (GeneralStatisticsMetric), statistics when initializing content (InitialStatisticsMetric), HTTP statistics(HttpStatisticsMetric), and system statistics dur-
ing playback (SystemStatisticsMetric).

The available statistics are briefly summarized in the table below:

<table>
    <thead>
        <tr>
            <th>Statistics Category</th>
            <th colspan=2>Metric</th>
            <th>Data Type</th>
            <th>Unit</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=16>STATISTICS_GENERAL</td>
            <td colspan=2 rowspan=1 style="text-align: center; vertical-align: middle;">PLAY_TIME_SEC</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">seconds</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;"colspan=2 rowspan=1>BYTES_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">Bytes</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>CUR_NETWORK_BW_BPS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">bps</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>CUR_TRACK_BW_BPS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">bps</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_REQUESTS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_DOWN_RATE</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_FAIL_TO_PARSE</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_IN_BUFFER</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_REQUEST_ERRORS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_REQUEST_TIMEOUT</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_TRACK_SWITCH_UP</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_TRACK_SWITCH_DOWN</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_VIDEO_FRAME_RENDERED</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
         <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_VIDEO_FRAME_DECODED</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
         <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_HTTP_REQUESTS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" rowspan=9>STATISTICS_INITIAL</td>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_TRACK</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_PREBUFFERED_SEGMENTS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_REDIRECTS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>MASTER_PLAYLIST</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>MASTER_PLAYLIST_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>INITIAL_PLAYLIST</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>INITIAL_PLAYLIST_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>START_SEGMENT_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>CONTENT_DURATION</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">msec</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" rowspan=15>STATISTICS_HTTP</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=6>DOWN_START</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>FILE_TYPE</td>
            <td style="text-align: center; vertical-align: middle;">FileType</td>
            <td style="text-align: center; vertical-align: middle;">FileType</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>SEG_NO</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>SEG_DURATION</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">msec</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>TRACK_BW</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">bps</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>MEDIA_COMPOSITION</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">MediaType</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>CONNECT</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>CONNECTED</td>
            <td colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>HEADER_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=3>DATA_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>BYTE_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">Bytes</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>CONTENT_LENGTH</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">Bytes</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=2>DOWN_END</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>BYTE_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">Bytes</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>ERROR</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" rowspan=2>STATISTICS_SYSTEM</td>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>CPU_USAGE</td>
            <td style="text-align: center; vertical-align: middle;">double</td>
            <td style="text-align: center; vertical-align: middle;">percentage (0 - 1)</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>FREE_MEMORY_KB</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">kilobytes</td>
        </tr>
    </tbody>
</table>

Example Code for how to implement and use `NexStatisticsMonitor:

```java
// Create a new NexStatisticsMonitor in the application
NexStatisticMonitor mMonitor = new NexStatisticMonitor(mNexPlayer);

IStatisticsListener listener =
{
	void onUpdated(int statisticsType, HashMap<IStatistic, Object> map) {
		if( statisticsType == STATISTICS_GENERAL ) {
			while ( IStatistics key in map ) {
				GeneralStatisticsMetric key = (GeneralStatisticsMetric)map.getKey();
				Object value = map.getValue();
			}
		}
		else if( statisticsType == STATISTICS_INITIAL ) {
			while ( IStatistics key in map ) {
				InitialStatisticsMetric key = (InitialStatisticsMetric)map.getKey();
				Object value = map.getValue();
			}
		}
		else if( statisticsType == STATISTICS_HTTP ) {
			while ( IStatistics key in map ) {
				HttpStatisticsMetric key;
				HashMap<HttpStatisticsParamKey, Object> subMap;
				key = (HttpStatisticsMetric)map.getKey();
				subMap = (HashMap<HttpStatisticsParamKey,Object>)map.getValue();
				
				while(HttpStatisticsParamKey key in subMap) {
					HttpStatisticsParamKey paramkey = (HttpStatisticsParamKey)subMap.getKey();
					Object value = entry.getValue();
				}
			}
		}
		else if ..
	}
}

// Set a listener for statistics-related events
mMonitor.setListener( listener );

// Set the time interval at which general playback statistics should be requested (ie every 5 seconds)
mMonitor.setDuration(NexStatisticsMonitor.GeneralStatistic, seconds);
// Set the time interval at which system statistics during playback should be requested.
mMonitor.setDuration(NexStatisticsMonitor.SystemStatistic, seconds);
```

**See Also**

- setListener
- setDuration


**Classes**

- `enum FileType`

    An enumeration of the possible types of files being handled by NexPlayer™ during HLS, DASH or SS playback.
- `enum GeneralStatisticsMetric`

    This is an enumeration of the possible general statistics that can be requested during playback of HLS, DASH or SS
    content in NexPlayer™.
- `enum HttpStatisticsMetric`

	This enumeration defines the possible HTTP statistics that can be requested during HLS, DASH or SS playback by
	NexPlayer™.
 
- `enum HttpStatisticsParamKey`

    This enumeration defines the parameter key, for parameters related to HTTP statistics monitored during HLS, DASH
    or SS playback.
- `enum InitialStatisticsMetric`

    This is an enumeration of the possible initial statistics that can be requested when initializing playback of HLS, DASH
    or SS content in NexPlayer™.
- `interface IStatistics`

    This interface defines a set of statistics to be received fromNexPlayer™ aboutHLS, DASH or SS playback.
- `interface IStatisticsListener`

    This interface defines the listener that will be used to receive statistics related to playback.
- `enum MediaType`

    An enumeration defining the possible types of HLS, DASH or SS media can be played by NexPlayer™.
- `enum StatisticsError`

    An enumeration of the statistics-related errors possible when using theNexStatisticsMonitor.
- `enum SystemStatisticsMetric`

    This is an enumeration of the possible system statistics that can be requested during playback of HLS, DASH or SS
    content in NexPlayer™.


#### NexStatisticsMonitor( NexPlayer np )

Defines theNexStatisticsMonitormodule that an application can use to retrieve statistics about playback
of HLS, DASH or SS content in NexPlayer™.

**Parameters**

| Name            | Description              |
|-----------------|------|
| np | TheNexPlayerinstance that the statistics monitor will receive events from. |
 


#### StatisticsErrorsetDuration ( int statisticsType, double seconds )

This method sets the interval of time at which playback statistics will be reported and sent (for HLS, DASH or SS
content only).

After a statistics listener has been set, this method can be called to change the interval at which general playback
and system statistics are monitored at any timebeforestarting playback.

The default interval of time for monitoring general and system statistics during HLS, DASH or SS playback is 5000
ms or 5 seconds.

> **Note** The interval between statistics events can only be set for GeneralStatisticsMetric and SystemStatisticsMetric requests so an error will be returned if any other statisticsType is indicated because initial statistics and HTTP statistics are event-driven statistics.

**Parameters**

| Name            | Description              |
|-----------------|------|
| statisticsType | statisticsType The type of statistics to be retrieved at the interval set here. This should be STATISTICS\_GENERAL for general playback statistics or STATISTICS\_SYSTEM for monitoring system statistics during playback. |
| seconds            | The interval at which statistics will be monitored, in seconds, as a double.              |
 
**Returns**

if successful or the relevant NexStatistics error code (for example, RETURN\_ERROR\_DURATION\_INVALID)
 
**See Also**

 
- GeneralStatistics
- SystemStatistics
- StatisticsErrror
 
#### void setListener ( IStatisticsListener listener )

This method sets a listener to receive statistics events about HLS, DASH or SS playback in NexPlayer™.

A statistics listener should be set after NexPlayer has been created and initialized, but before content playback
begins.

**Parameters**

 Name            | Description              |
|-----------------|------|
| listener | The listener that will receive playback statistics events. |
 
**See Also**

 
- setDuration(int statisticsType, double seconds)
 
#### final int STATISTICS\_GENERAL = 0 [static]

A possible argument value for the parameterstatisticsTypein the onUpdated() and setDuration()
 methods for the type of statistics being requested and received, for general playback statistics.

#### final int STATISTICS\_HTTP = 2 [static]

A possible argument value for the parameter statisticsType in the onUpdated() method for the type of
statistics being requested and received, for HTTP statistics.

#### final int STATISTICS\_INITIAL = 1 [static]

A possible argument value for the parameter statisticsType in the onUpdated() method for the type of
statistics being requested and received, for initial statistics (statistics about when playback is initialized).

#### final int STATISTICS\_SYSTEM = 3 [static]

A possible argument value for the parameter statisticsType in the onUpdated() and setDuration()
 methods for the type of statistics being requested and received, for system statistics.

### NexStoredInfoFileUtils Class Reference

**Static Public Attributes**

- `static final String STORED_INFO_KEY_STORE_URL` = "URL"

    The stored URL as an integer.
- `static final String STORED_INFO_KEY_BW` = "Bandwidth"

    The set bandwidth value as an integer.
- `static final String STORED_INFO_KEY_AUDIO_STREAM_ID `= "Audio\_Stream\_ID"

    The stored audio stream ID as an integer.
- `static final String STORED_INFO_KEY_AUDIO_TRACK_ID` = "Audio\_Track\_ID"

    The stored audio track ID as an integer.
- `static final String STORED_INFO_KEY_VIDEO_STREAM_ID` = "Video\_Stream\_ID"

    The stored video stream ID store as an integer.
- `static final String STORED_INFO_KEY_TEXT_STREAM_ID` = "Text\_Stream\_ID"

    The stored text stream ID as an integer.
- `static final String STORED_INFO_KEY_CUSTOM_ATTR_ID` = "Custom\_Attr\_ID"

    The stored custom attribute stream ID as an integer.
- `static final String STORED_INFO_KEY_AUDIO_PREFER_LANGUAGE` = "Audio\_Prefer\_Language"

    The preferred language of the stored audio as a string.
- `static final String STORED_INFO_KEY_TEXT_PREFER_LANGUAGE` = "Text\_Prefer\_Language"

    The preferred language of the stored text as a string.
- `static final String STORED_INFO_KEY_STORE_PATH` = "Store\_Path"

    The cache directory as a string.
- `static final String STORED_INFO_KEY_STORE_PERCENTAGE` = "Store\_Percentage"

	 The stored percentage as an integer.
- `static final String STORED_INFO_KEY_MEDIA_DRM_KEY_SERVER_URI` = "Media\_DRM\_Key\_Server\_URI"

	The key server’s URL as a string.
- `static final String STORED_INFO_KEY_OFFLINE_KEY_ID` = "Offline\_Key\_ID"

    The key ID issued from NexPlayer.IOfflineKeyListener.onOfflineKeyStoreListener as a string.
- `static final String STORED_INFO_KEY_DRM_TYPE` = "DRM\_Type"

**Static Protected Member Functions**

- `static int makeStoredInfoFile (NexSettingDataForStoring settings)`
- `static int updateStoredInfoFile (FileDescriptor fd, NexSettingDataForStoring settings)`
- `static int deleteOfflineCache (File storedInfoFile)`



#### static JSONObject parseJSONObject ( FileDescriptor storedInfoFD ) [static]

This method parses the store info file as JSONObject.

**Parameters**

| Name            | Description              |
|-----------------|------|
| storedInfoFD | The file descriptor of the info file created from storing. |
 
**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### static JSONObject parseJSONObject ( File storedInfoFile ) [static]

This method parses the store info file as JSONObject.

**Parameters**

| Name            | Description              |
|-----------------|------|
| storedInfoFile | The file descriptor of the info file created from storing. |
 
**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
### NexStreamInformation Class Reference

This class provides information on a content stream.

Content streams are listed in the mArrStreamInformation member of NexContentInformation. See there for details.
 
#### NexStreamInformation( int iID, int iType, int currCustomAttrId, int currTrackId, int isIFrameTrack, int isDisabled, NexID3TagText name, NexID3TagText language, String strInStreamID, int representCodecType)

This is the sole constructor for NexStreamInformation.

The parameters match the members of the class one-to-one. Generally, it is not necessary to call the constructor; rather, objects of this class are created by NexPlayer™ internally and made available through mArrStream-
Information.

**Parameters**

| Name            | Description              |
|-----------------|------|
| iID | Initial value for mID member. |
| iType | Initial value for mType member. |
| currCustomAttrId | Initial value for mCurrCustomAttrId member. |
| currTrackId | Initial value for mCurrTrackId member. |
| isIFrameTrack | Initial value for mIsIframeTrack member. |
| isDisabled | Initial value for mIsDisabled member. |
| name | Initial value for mName member. |
| language | Initial value for mLanguage member. |
| strInStreamID | Initial value for mInStreamID. |
| representCodecType | Initial value for mRepresentCodecType. |
 
#### NexTrackInformation[ ] mArrTrackInformation

For formats such as HLS that support multiple tracks for a given stream, this is an array containing information on
each track associated with the stream.

This may be an empty array for formats that don’t have track information.

#### int mCurrCustomAttrID

The ID of the custom attribute within this stream that is currently active, or -1 if no custom attribute in this stream is
currently active.

This ID matches a value in NexCustomAttribInformation[].mID. If the NexCustomAttrib-
Information array is empty, this value is undefined.

#### int mCurrTrackID

This is the ID of the track within the stream that is currently playing, or -1 if no track in this stream is currently playing.

This ID matches a value in mArrTrackInformation[].mTrackID. If the mArrTrackInformation
 array is empty, this value is undefined.

#### int mID

This is a unique integer used to identify the current stream in API calls.

For example, this is used when calling setMediaStream.

#### String mInStreamID

This is the INSTREAM-ID TAG of the media stream.

This is an arbitrary value set by the author, and is intended for user displaying (to allow users to select among
different alternative streams).

For HLS content, this value is filled when the TYPE attribute is CLOSED-CAPTIONS. In this case, this value must
be one of the following values: "CC1", "CC2", "CC3", "CC4" or "SERVICEn", where n must be an integer between
1 and 63.

#### int mIsDisabled

This indicates whether a track is disabled or not.

Tracks will be disabled if the content requires an unsupported codec (audio or video).
 
> **Note** This value should only be used for verification and should not be changed. This value is only for NexPlayer™’s
internal use.
 
#### int mIsIframeTrack

For HLS content, this indicates whether the track is a normal audio video track or a track of only I-frames.

For an I-frame-only track, this value will be 1, and for other kinds of tracks, it will be 0. Since other kinds of content
do not include any I-frame-only tracks, this value will always be 0 for content other than HLS.
 
#### NexID3TagTextmLanguage

This is the language of the media stream, for streaming formats that include language data.

This is an arbitrary value set by the author, and is intended for user display (to allow users to select among different
alternative streams). Applications should NOT rely on this being any particular format; it is most likely to be the
display name of the language, but may be any string.

#### NexID3TagTextmName

The name of the media stream, for streaming formats that have named streams.

This is an arbitrary value set by the author, and is generally intended for user display (to allow the user to select
among different alternative streams).

#### int mRepresentCodecType

The type of codec available in the stream.

It will be set to 0 until the stream is downloaded. If this is for CEA 608/708 captions embedded in the content, it will
be represented as NexContentInformation.NEX\_TEXT\_CEA.

#### int mTrackCount

This is the number of tracks associated with this stream.

This is the same as the length ofmArrTrackInformation, and may be zero.

#### int mType

This indicates the stream type (audio or video).

This is one of:

- `(0x00)` MEDIA\_STREAM\_TYPE\_AUDIO
- `(0x01)` MEDIA\_STREAM\_TYPE\_VIDEO
- `(0x02)` MEDIA\_STREAM\_TYPE\_TEXT
- `(0x00)` MEDIA\_TRACK\_TYPE\_AUDIO

### NexSystemInfo Class Reference

This class provides NexPlayer™ with information about the system and device.

**Static Public Attributes**

- `static final int NEX_SUPPORT_PLATFORM_NOTHING` = 0x0

    Return value of getPlatformInfo() for checking Android Version, for a not supported platform.
- `static final int NEX_SUPPORT_PLATFORM_CUPCAKE` = 0x15

    Return value of getPlatformInfo() for checking Android Version, for Cupcake.
- `static final int NEX_SUPPORT_PLATFORM_DONUT` = 0x16

    Return value of getPlatformInfo() for checking Android Version, for Donut.
- `static final int NEX_SUPPORT_PLATFORM_ECLAIR` = 0x21

    Return value of getPlatformInfo() for checking Android Version, for Eclair.
- `static final int NEX_SUPPORT_PLATFORM_FROYO` = 0x22

    Return value of getPlatformInfo() for checking Android Version, for Froyo.
- `static final int NEX_SUPPORT_PLATFORM_GINGERBREAD` = 0x30

    Return value of getPlatformInfo() for checking Android Version, for Gingerbread.
- `static final int NEX_SUPPORT_PLATFORM_HONEYCOMB` = 0x31

    Return value of getPlatformInfo() for checking Android Version, for Honeycomb.
- `static final int NEX_SUPPORT_PLATFORM_ICECREAM_SANDWICH` = 0x40

    Return value of getPlatformInfo() for checking Android Version, for Ice Cream Sandwich.
- `static final int NEX_SUPPORT_PLATFORM_JELLYBEAN` = 0x41

    Return value of getPlatformInfo() for checking Android Version, for Jelly Bean.
- `static final int NEX_SUPPORT_PLATFORM_JELLYBEAN3` = 0x43

    Return value of getPlatformInfo() for checking Android Version, for Jelly Bean.
- `static final int NEX_SUPPORT_PLATFORM_KITKAT` = 0x44

    Return value of getPlatformInfo() for checking Android Version, for KitKat.
- `static final int NEX_SUPPORT_PLATFORM_LOLLIPOP` = 0x50

	Return value of getPlatformInfo() for checking Android Version, for Lollipop.
- `static final int NEX_SUPPORT_PLATFORM_MARSHMALLOW` = 0x60

    Return value of getPlatformInfo() for checking Android Version, for Marshmallow.
- `static final int NEX_SUPPORT_PLATFORM_NOUGAT` = 0x70

    Return value of getPlatformInfo() for checking Android Version, for Nougat.
- `static final int NEX_SUPPORT_PLATFORM_OREO` = 0x80

    Return value of getPlatformInfo() for checking Android Version, for OREO.
- `static final int NEX_SUPPORT_CPU_ARM64_V8A` = 0x8

    Return value of getCPUInfo() for ARMV8.
- `static final int NEX_SUPPORT_CPU_ARMV7` = 0x7
    Return value of getCPUInfo() for ARMV7.
- `static final int NEX_SUPPORT_CPU_ARMV6` = 0x6

    Return value of getCPUInfo() for ARMV6.
- `static final int NEX_SUPPORT_CPU_ARMV5` = 0x5

    Return value of getCPUInfo() for ARMV5.
- `static final int NEX_SUPPORT_CPU_X86` = 0x86

    Return value of getCPUInfo() for Intel x86 chipsets.
- `static final int NEX_SUPPORT_CPU_X86_64` = 0x64
- `static boolean x86Disabled` = false

    Allows the CPU architecture (whether it should be viewed as x86 or ARM) to be set externally.

#### static int getCPUInfo ( ) [static]

This method returns the CPU architecture information.

**Returns**

CPU architecture information; one of:
 
- `NEX_SUPPORT_CPU_ARMV5`
- `NEX_SUPPORT_CPU_ARMV6`
- `NEX_SUPPORT_CPU_ARMV7`
- `NEX_SUPPORT_CPU_ARM64_V8A`
- `NEX_SUPPORT_CPU_X86`
- `NEX_SUPPORT_CPU_X86_64`

#### static int getPlatformInfo ( ) [static]

This method returns the Android Version of the device platform.

**Returns**

Android Version; one of:
 
- `NEX_SUPPORT_PLATFORM_CUPCAKE`
- `NEX_SUPPORT_PLATFORM_DONUT`
- `NEX_SUPPORT_PLATFORM_ECLAIR`
- `NEX_SUPPORT_PLATFORM_FROYO`
- `NEX_SUPPORT_PLATFORM_GINGERBREAD`
- `NEX_SUPPORT_PLATFORM_HONEYCOMB`
- `NEX_SUPPORT_PLATFORM_ICECREAM_SANDWICH`
- `NEX_SUPPORT_PLATFORM_JELLYBEAN`
- `NEX_SUPPORT_PLATFORM_MARSHMALLOW`
- `NEX_SUPPORT_PLATFORM_NOUGAT`
- `NEX_SUPPORT_PLATFORM_OREO`
- `NEX_SUPPORT_PLATFORM_NOTHING`

#### final int NEX\_SUPPORT\_CPU\_X86 = 0x86 [static]

Return value of getCPUInfo() for Intel x86 chipsets.
 
#### boolean x86Disabled = false [static]

Allows the CPU architecture (whether it should be viewed as x86 or ARM) to be set externally.

Set this to TRUE to ignore internal settings and force set the CPU architecture to ARM, or FALSE to check whether
the internal setting is set to ARM or x86.
 
### NexTextureView Class Reference
 
**Classes**

- `class EGLManager`
- `class Renderer`

**Protected Attributes**

- `final String LOG_TAG = "NexTextureView"`
- `final String GLT_LOG_TAG = "NexGLThread"`

**Static Protected Attributes**

- `static final boolean LOG_ATTACH_DETACH` = true
- `static final boolean LOG_THREADS` = true
- `static final boolean LOG_PAUSE_RESUME` = true
- `static final boolean LOG_SURFACE` = false
- `static final boolean LOG_RENDERER` = true
- `static final boolean LOG_RENDERER_DRAW_FRAME` = false
- `static final boolean LOG_EGL` = true



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
 
#### void setScreenPixelFormat ( int screenPixelFormatToSet )

This method sets the current screen pixel format.

If the model is "Milestone", the screen pixel format will be forced to RGB\_565.

**Parameters**

| Name            | Description              |
|-----------------|------|
| screenPixelFormatToSet | One of the constants specified in android.graphics.PixelFormat. |
 
> **Deprecated** This is no longer supported;
 
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
 
### NexThumbnail Class Reference

The primary interface to the NexThumbnail class.

This class allows NexPlayer™ to handle thumbnail information in content.

Follow the steps below in order to use the NexThumbnail class:

1. Init() : Initializes the thumbnail instance.
2. getInfo() : Gets the content information (original width, hight, pitch, rotation info).
3. getData() : Gets the thumbnail output data, where choice of output image type (RGB565, RGB888...) should
    be made.
4. Deinit() : Releases the thumbnail instance.

> **Author** NexStreaming Corporation
 
> **Deprecated** For internal use only. Please do not use.
**Classes**

- `class ThumbnailInformation`

**Public Attributes**

- `int mNativeNexThumbnailClient` = 0

**Static Public Attributes**

- `static final int OUTPUT\_TYPE\_RGB565` = 4
- `static final int OUTPUT\_TYPE\_RGB888` = 6



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
 
### NexTrackInformation Class Reference

Stores and provides information about an individual content track, for formats that use multiple tracks (such as HLS).

See NexContentInformation for details.

**Static Public Attributes**

- `static final int REASON_TRACK_NOT_SUPPORT_VIDEO_CODEC` = 0x0000001

    Possible value for NexTrackInformation.mReason.
- `static final int REASON_TRACK_NOT_SUPPORT_AUDIO_CODEC` = 0x0000002

    Possible value for NexTrackInformation.mReason.
- `static final int REASON_TRACK_NOT_SUPPORT_VIDEO_RESOLUTION` = 0x0000003

    Possible value for NexTrackInformation.mReason.
- `static final int REASON_TRACK_NOT_SUPPORT_VIDEO_RENDER` = 0x0000004

    Possible value for NexTrackInformation.mReason.
 
#### int mCodecType

This indicates the codec used for the given track.

> **Warning** Do not trust this value in HLS and MS Smooth Streaming mode, as invalid values are sometimes provided.
 
If this track type is video, this value will be one of:

- NEXOTI\_MPEG4V
- NEXOTI\_H263
- NEXOTI\_H264
- NEXOTI\_WMV
- NEXOTI\_RV

If this track type is audio, this value will be one of:

- NEXOTI\_AAC
- NEXOTI\_AAC\_GENERIC
- NEXOTI\_AAC\_PLUS
- NEXOTI\_MPEG2AAC
- NEXOTI\_MP3inMP4
- NEXOTI\_MP2
- NEXOTI\_MP3
- NEXOTI\_BSAC
- NEXOTI\_WMA
- NEXOTI\_RA
- NEXOTI\_AC3
- NEXOTI\_EC3
- NEXOTI\_AC4
- NEXOTI\_DRA

or (in future versions) one of the following speech codec constants:

- NEXOTI\_AMR
- NEXOTI\_EVRC
- NEXOTI\_QCELP
- NEXOTI\_QCELP\_ALT
- NEXOTI\_SMV
- NEXOTI\_AMRWB
- NEXOTI\_G711
- NEXOTI\_G723

 
#### int mCustomAttribID

The Custom Attribute ID of the track.

In some cases, a stream may have multiple equivalent tracks. Setting a custom attribute ID in setMediaStream
causes only tracks with a matching custom attribute ID to be selected. A custom attribute ID represents a particular
key/value attribute pair. The full list of available pairs and their associated ID values can be found in mArrCustomAttribInformation.

Please keep in mind that this is an arbitrary value, not an index into the custom attribute array.

#### boolean mIFrameTrack

Indicates if the track is a track of IFrames for the video content or not.

Possible Values:

- `0` : FALSE. Not a track of IFrames.
- `1` : TRUE. A track of IFrames.

#### int mReason

For invalid tracks, this variable indicates the reason they are not currently valid.

This may be any of the following values:

- `REASON_TRACK_NOT_SUPPORT_VIDEO_CODEC` if the player doesn’t support the video codec used for
    this content.
- `REASON_TRACK_NOT_SUPPORT_AUDIO_CODEC `if the player doesn’t support the audio video codec
    used for this content.
- `REASON_TRACK_NOT_SUPPORT_VIDEO_RESOLUTION` if the track is locked out because the video resolution is too high to play, as determined by the settings of the MAX\_HEIGHT and MAX\_WIDTH properties.
- `REASON_TRACK_NOT_SUPPORT_VIDEO_RENDER` if the track was locked out because the video renderer wasn’t capable of playing it smoothly (the resolution and/or bit rate too high).

#### int mTrackID

The ID of the track.

This is an arbitrary value, not an index, but can be matched to the currently playing track as indicated by mCurrTrackID. Second parameter of the setMediaTrack.

#### int mType

This indicates the type of track:

- `1` : Audio Only
- `2` : Video Only
- `3` : AV For local playback, the type will be Audio(1) or Video(2). For streaming playback, the type can be
    Audio(1) ,Video(2), or AV(3).

#### int mValid

Indicates if this track is valid (that is, if the codecs, bitrates, and so on are supported by NexPlayer™).

- `0` : Unsupported or invalid track
- `1` : Valid and supported track

### NexVideoRenderer Class Reference

A prebuilt FrameLayout containing the video view associated with a NexPlayer™ instance.

NexVideoRenderer can be used to simplify the video rendering tasks in an application integrating with the NexPlayer™ SDK. It handles the different renderer types that can be used by NexPlayer ™ but depend on the device.

To use it:

1. Pass in a Context to the constructor.
2. Set up listeners (IListener and IVideoRendererListener).
3. Create an instance of NexPlayer.
4. Perform the necessary setup for NexPlayer™ (such as NexPlayer.setNexALFactory and NexPlayer.init).
5. Call init with the NexPlayer instance.
6. Add the NexVideoRenderer instance as a view to your layout.

For additional details on how to use this video renderer, please refer to the sample code provided with the SDK.

 
**Classes**

- `interface IListener`

    The application must implement this interface in order to receive events from NexVideoRenderer.
 
#### NexVideoRenderer( Context context ) 

Constructor for NexVideoRenderer.

After creating an instance, you may call getColorDepth to pass to NexALFactory.init.

**Parameters**

| Name            | Description              |
|-----------------|------|
| context | The Context instance associated with the activity that will contain this view. |
 
#### NexVideoRenderer( Context context, AttributeSet attrs )

Constructor for NexVideoRenderer.

**See Also**

 
- NexVideoRenderer.NexVideoRenderer(android.content.Context)
 
#### NexVideoRenderer( Context context, AttributeSet attrs, int defStyle )

Constructor for NexVideoRenderer.

**See Also**
 
- NexVideoRenderer.NexVideoRenderer(android.content.Context)


#### void clearCanvas ( )

This method requests that the NexVideoRenderer view display a blank canvas (black).

> **Deprecated** For internal use only. Please do not use.
 
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
 
**Since**

 
version 6.1
 
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
 
#### void requestClear ( )

This method requests that the canvas be cleared.

> **Deprecated** This is no longer supported; use clearCanvas instead.

#### void resetSurface ( )

This method resets the surfaceView or GLSurfaceView of NexVideoRenderer.

This method informs the NexVideoRenderer that the holder of NexVideoRenderer has changed. After this
method is called, onSizeChanged() may be called.
 
#### void setActivityPaused ( boolean bPaused )

This method notifies NexVideoRenderer of an onPause callback.

This is to prevent NexVideoRenderer from performing unnecessary operations that could potentially lead to a crash
after the activity or fragment is in the background.

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

Within the NexVideoRenderer layout, these parameters will be used to set the output position and size of the media
content.

Any time the size of the layout is changed, a rotation occurs, or the size of the content changes, the application
should call this method to reset the display boundaries.

The parameters left and top define the top left-hand corner of the rectangle where video contents will be
displayed, whilewidthandheightdefine the size of this display rectangle.

**Parameters**

| Name   | Description                                                                                                                                                     |
|--------|-----------------|
| left   | The horizontal position in pixels of the top left-hand corner of the desired rectangle within the NexVideoRenderer layout to start rendering the media content. |
| top    | The vertical position in pixels of the top left-hand corner of the desired rectangle within the NexVideoRenderer layout to start rendering the media content.   |
| width  | The width in pixels of the desired rectangle within the NexVideoRenderer layout to render the media content.                                                    |
| height | The height in pixels of the desired rectangle within the NexVideoRenderer layout to render the media content.                                                   |
 
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
| postSurfaceHolderCallback   | An instance of SurfaceHolder.Callback that requests the callbacks from the Surface to handle them after NexVideoRenderer has finished performing its operations.                                                                                                                                                            |
 
#### void setPreGLRendererListener ( GLRenderer.IListener preGLRendererListener )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering process.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| preGLRendererListener   | An instance of GLRenderer.IListener that requests the callbacks from GLRenderer to handle them before NexVideoRenderer has started performing its operations.                                                                                                                                                            |
 
#### void setPreNexPlayerVideoRendererListener ( NexPlayer.IVideoRendererListener preNexPlayerVideoRendererListener ) 

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering process.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| preNexPlayerVideoRendererListener   | An instance of NexPlayer.IVideoRendererListener that requests the callbacks from NexPlayer to handle them before NexVideoRenderer has started performing its operations.                                                                                                                                                            |
 
#### void setPreSurfaceHolderCallback ( SurfaceHolder.Callback preSurfaceHolderCallback )

This method sets a listener for handling the finer details of the video renderer.

Setting this listener is absolutely optional and intended for the experts who want finer control of the rendering process.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| preSurfaceHolderCallback   | An instance of SurfaceHolder.Callback that requests the callbacks from the Surface to handle them before NexVideoRenderer has started performing its operations.                                                                                                                                                            |
 
#### void setScreenPixelFormat ( int screenPixelFormatToSet)

This method sets the current screen pixel format.

If the model is "Milestone", the screen pixel format will be forced to RGB\_565.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| screenPixelFormatToSet   | One of the constants specified in android.graphics.PixelFormat.                                                                                                                                                            |
 
#### void setShouldFilterBitmap ( boolean shouldFilterBitmap )

This method sets whether or not the bitmap should be filtered when the Java renderer is used.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| shouldFilterBitmap   | TRUE if the bitmap should be filtered, and otherwise FALSE.                                                                                                                                                            |
 
#### void setSurfaceSecure ( Boolean usesecure )

This method prevents the user from recording the screen on devices running the Android KitKat (4.4) OS and above.

Call this API right afterinitif screen recording should be prevented.

**Parameters**

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

 
> **Note** Call this API right before init.
 
#### void setVisibility ( int visibility )

This method sets the visibility of the NexVideoRenderer layout.

**Parameters**


| Name   | Description                                                                                                                                                   |
|--------|---------------|
| visibility   | A constant from android.view.View.                                                                                                                                                            |
 
### NexVideoView Class Reference

This class allows to use NexPlayer™SDK easily on the application.

NexVideoView class containsVideoRenderer, CaptionRenderer, NexPlayer, NexAlFactory
classes so that the developer can play the media content by only using a NexVideoView object.
 
**Classes**

- `interface OnBufferingUpdateListener`

    The application must implement this interface in order to receive buffering events from NexVideoView.
- `interface OnCompletionListener`

    The application must implement this interface in order to receiveNexVideoViewevents when playback is successful up to the end of the content.
- `interface OnConfigurationListener`

    The application must implement this interface in order to receiveNexVideoViewevents before NexPlayer™ is
    opened.
- `interface OnDynamicThumbnailListener`

    The application must implement this interface in order to receive Dynamic Thumbnail related events fromNexVideoView.
- `interface OnErrorListener`

    The application must implement this interface in order to receive error events fromNexVideoView.
- `interface OnExternalSubtitleChangedListener`

    The application must implement this interface in order to receive onExternalSubtitleChanged events from
    NexVideoView.
- `interface OnFastPlayListener`

    The application must implement this interface in order to receive fast Play related events from NexVideoView.
- `interface OnInfoListener`

    This interface transfer updated NexContentInformation to the application.
    
- `interface OnMediaStreamChangedListener`

    The application must implement this interface in order to receive onMediaStreamChanged events from NexVideoView.
- `interface OnPauseCompleteListener`

    The application must implement this interface in order to receive onPauseComplete events from NexVideoView.
- `interface OnPreparedListener`

    The application must implement this interface in order to receive NexVideoView events when NexPlayer™ is ready
    for the playback.
- `interface OnResumeCompleteListener`

    The application must implement this interface in order to receive onResumeComplete events from NexVideoView.
- `interface OnSeekCompleteListener`

    The application must implement this interface in order to receive events from NexVideoView when seek is successful.
- `interface OnStartCompleteListener`

    The application must implement this interface in order to receive onstartComplete events from NexVideoView.
- `interface OnStopCompleteListener`

    The application must implement this interface in order to receive onStopComplete events from NexVideoView.
- `interface OnTimedMetaRenderRenderListener`

    The application must implement this interface in order to receive TimedMeta events from NexVideoView.
- `interface OnTimeUpdateListener`
- `enum ScalingMode`

    This enumeration defines the possible scaling mode for output video and captions.
- `class Settings`

    This class manages the setting values needed for initializing Video Renderer, Caption Renderer and NexPlayer™
    internally.
    
**Static Public Attributes**

- `static final int STREAM_TYPE_VIDEO` = 2
- `static final int STREAM_TYPE_AUDIO` = 1
- `static final int STREAM_TYPE_TEXT` = 0
 
#### NexVideoView( Context context )

Constructor for NexVideoView.

**Parameters**


| Name   | Description                                                                                                                                                   |
|--------|---------------|
| context   | The Context instance associated with the activity that will contain this view.                                                                                                                                                            |
 
#### NexVideoView( Context context, AttributeSet attrs )

Constructor for NexVideoView.

**See Also** 

- NexVideoView.NexVideoView(android.content.Context)
 


#### void addSubtitleSource ( String subtitlePath )

This method allows the subtitle file for a particular content to be changed during playback.

This method operates asynchronously. When addSubtitleSource has completed and if OnExternalSubtitleChangedListener is registered on the NexVideoView, a onExternalSubtitleChanged
 event will be called.
 
**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| subtitlePath   | The path to the new subtitle file or the URL to load the new subtitle file.                                                                                                                                                            |
 
#### boolean canPause ( )

This method determines whether the current media content can be paused.

**Returns**

 
true if the content can be paused, otherwise false.
 
#### boolean canSeekBackward ( )

This method determines whether the media content allows to seek backward.

**Returns**

 
true if the content allows to seek backward, otherwise false.

#### boolean canSeekForward ( )

This method determines whether the media content allows to seek forward.

**Returns**

 
true if the content allows to seek forward, otherwise false.
 
#### int fastPlaySetPlaybackRate ( float rate )

This method sets the video playback rate for the fastPlay feature.

**Parameters**


| Name   | Description                                                                                                                                                   |
|--------|---------------|
| rate   | This boolean value sets whether to resume playback after fastPlay or not. Set to 1 to automatically resume playback when fastPlay stops. Set to 0 to pause content when fastPlay stops.                                                                                                                                                            | 
 
**Returns**

 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
**See Also**

 
- NexPlayer.fastPlaySetPlaybackRate
 
#### int fastPlayStart ( int msec, float rate )

This method activates the fastPlay feature in HLS content.

This method operates asynchronously, and when fastPlayStart has successfully completed, and if OnFastPlayListener is registered onNexVideoView, an onFastPlayStart event will be called.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
|msec | The time in the content at which to start fastPlay, in milliseconds. | 
|rate | The speed at which the video will play in fastPlay mode. This speed is indicated by any
float value (but NOT zero), where negative values rewind the video at faster than normal
playback speed and positive values play the video faster than normal (like fast forward). For
example: - rate = 3.0 (fastPlay plays video at 3x normal speed) - rate = - 2.0 (fastPlay rewinds
video at 2x normal speed)|
 
**Returns**

 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
**See Also**

 
- NexPlayer.fastPlaystart

#### int fastPlayStop ( boolean bResume )

This method turns off the fastPlay feature in HLS content.

Once the fastPlay feature has been activated by calling fastPlay Start, this method must be called in order
to stop fastPlay.

This method operates asynchronously, and when fastPlay Stop has successfully completed, and if OnFastPlayListener is registered on NexVideoView, an onFastPlayStop event will be called.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------| 
|bResume | This boolean value sets whether to resume playback afterfastPlayor not. Set to 1 to automatically resume playback when fastPlay stops. Set to 0 to pause content when fastPlay stops.|
 
**Returns**

 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### NexABRControllergetABRController ( )

This method gets an object of the NexABRController.

To use any specific feature provided by the NexABRController, use this method to call desired API to the
NexABRController object.

**Returns**

 
A NexABRController object.
 
#### int getAudioSessionId ( )

This method gets an audio session ID in order to use Android’s audio effects with the NexPlayer™.

**See Also**

 
- NexPlayer.getAudioSessionId

#### int getBufferPercentage ( )

This method determines the amount of currently buffered data, in percentage.

It calculates the percentage of data that has been buffered with the cts of the last frame in buffer. Note that CTS
stands for "Current Time Stamp".

**Returns**

 
The percentage of buffered data.

 
#### NexCaptionPaintergetCaptionPainter ( )

This method gets an object of the  NexCaptionPainter.

To use any specific feature provided by the NexCaptionPainter, use this method to call desired API to the NexCaptionPainter object.

**Returns**

A NexCaptionPainter object.

 
#### NexCaptionRenderViewgetCaptionRenderView ( )

This method gets an object of the NexCaptionRenderView.

To use any specific feature provided by the NexCaptionRenderView, use this method to call desired API to the NexCaptionRenderView object.

**Returns**

 
A NexCaptionRenderView object.
 
This method is deprecated and not supported in the current API version. Do not use it.

> **Deprecated** Not supported in current API version; do use getCaptionPainter instead of this method for captions.

#### int getCaptionType ( )

This method gets the type of the current caption in use.

**Returns**

 
The type of the current caption. The return value will be one from the following values :
 
- TEXT\_TYPE\_UNKNOWN
- TEXT\_TYPE\_GENERAL
- TEXT\_TYPE\_EXTERNAL\_TTML
- TEXT\_TYPE\_ATSCMH\_CC
- TEXT\_TYPE\_ATSCMH\_BAR
- TEXT\_TYPE\_ATSCMH\_AFD
- TEXT\_TYPE\_NTSC\_CC\_CH1
- TEXT\_TYPE\_NTSC\_CC\_CH2
- TEXT\_TYPE\_3GPP\_TIMEDTEXT
- TEXT\_TYPE\_TTML\_TIMEDTEXT
- TEXT\_TYPE\_WEBVTT
- TEXT\_TYPE\_SMI
- TEXT\_TYPE\_SRT
 
#### int getCurrentPosition ( )

This method gets the current play time position of NexPlayer™ in the given content.

This method can be called at any time to check the current position.

**Returns**

 
The current play time position in milliseconds (msec).
 
#### int getDuration ( )

This method gets the total duration of a media content.

For live contents, the seekable range will be returned.

**Returns**

 
The total duration of a media content, in milliseconds (msec).

#### NexPlayer getNexPlayer ( )

This method gets an object of the NexPlayer™.

To use a specific feature provided by the NexPlayer™ SDK, use this method to call desired API to the NexPlayer™ object.

**Returns**

 
A NexPlayer™ object.
 
#### Object getProperty ( NexPlayer.NexProperty property )

This method gets the value of an individual properties of the NexPlayer™.

The properties control the behavior of NexPlayer™ and the features that are enabled.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| property   | The property to get.                                                                                                                                                            |
 
**Returns**

 
The value of the property.

 
#### ScalingMode getScalingMode ( )

This method returns the scaling mode set to video and caption currently displayed on the output screen.

**Returns**

 
The scaling mode set to current video and caption.
 
**See Also**

 
- ScalingMode

#### Settings getSettings ( )

This method gets the current settings of the NexVideoView.

**Returns**

 
A settings object currently set to NexVideoView.
 
**See Also**

 
- NexVideoView.Settings
 
#### boolean isPlaying ( )

This method determines whether the media content is currently being played.

**Returns**

 
true if NexPlayer’s state returns NexPlayer.NEXPLAYER\_STATE\_PLAY, otherwise false.
 
#### void onPause ( )

This method informs the view that the activity is paused.

The owner of this view must call this method when the activity is paused. Calling this method will pause the rendering
thread.

> **Warning** This method will be called automatically on devices running the Android ICS (4.0) or higher. Otherwise, this method must be called when the activity is paused.
 
#### void onResume ( )

This method informs the view that the activity has resumed.

The owner of this view must call this method when the activity is being resumed. Calling this method will recreate
the OpenGL display and resume the rendering thread.

> **Warning** This method will be called automatically on devices running the Android ICS (4.0) or higher. Otherwise, this
method must be called when the activity is paused.

#### boolean onTouchEvent ( MotionEvent event )

The application must implement this method to handle touch screen motion events.

To use this method for detecting tap actions, it is recommended to operate the tapping action with performClick(). This will ensure the consistent system behavior, including: dispatching OnClickListener calls
handling ACTION\_CLICK when accessibility features are enabled.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| event   | The motion event.                                                                                                                                                            |
 
**Returns**

 
true if the event was handled, otherwise false.
 
#### void pause ( )

This method pauses the current playback.

Please note that when the hardware codec is in use, if the application is sent to the background by pressing the home button, pausing and resuming the playback may return an error because of resource limitations. To avoid this potential issue, stopping and starting playback is recommended in algorithm handling this specific case of the application being sent to the background because the home button was pressed.
 
#### void release ( )

This method clears the resources of NexVideoView including NexPlayer™ and NexALFactory.

This method must be called when the activity is destroyed.
 
#### void resume ( )

This method resumes the playback, beginning at the point at which the player was last paused.

#### void seekTo ( int msec )

This method seeks the playback position to the specified time.

This method will operate when the NexPlayer™ is playing or paused but will not operate when NexPlayer™ has
stopped or if the live steam doesn’t support seeking. This method operates asynchronously and when seekTo()
 is successful, and if OnSeekCompleteListener is registered on NexVideoView, a onSeekComplete
event will be called.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| msec   | The offset inmillisecondsfrom the beginning of the media to which the playback position should seek.                                                                                                                                                            |
 
#### void setCaptionLanguage ( int indexOfCaptionLanguage )

Selects the caption (subtitle) track that will be used.

Subtitles for the selected track will be passed to onTextRenderRender for display. This is used for file-based
captions only. For streaming media with included captions, setMediaStream() should be used instead, and
local captions should be turned off since running both types of captions at the same time has undefined results.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| indexOfCaptionLanguage   |An index into the mCaptionLanguages array specifying which language to use. If there are n entries in the caption array, then you may pass 0 ...n-1 to specify a single language, n to specify all languages, and n+1 to turn off captions.                                                                                                                                                            |

#### void setMediaController ( MediaController controller )

This method sets MediaController to NexVideoView to control the NexPlayer™.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| controller   | A MediaController object to connect to NexPlayer™.                                                                                                                                                            |
 
#### int setMediaStream ( int streamType, int streamID, int customAttrID)

For media with multiple streams, this method selects the streams that will be presented to the user.

This method is also used when changing CEA 608 channel index.

This method operates asynchronously, and when setMediaStream has successfully completed, and if OnMediaStreamChangedListener is registered on NexVideoView, an onMediaStreamChanged event will be called.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| streamType   | The type of the stream to change. This will be one of the following values :                                                                                                                                                            |
| streamID   | The ID of the stream to change. If the streamType value is set to STREAM\_TYPE\_TEXT and the current caption type is CEA 608, this value will be used as CEA 608 channel index instead of stream ID.                                                                                                                                                           |
| customAttrID   | This parameter is used when thestreamTypevalue is set to STREAM\_TYPE\_VIDEO. Otherwise any value set to this parameter will be ignored.                                                                                                                                                            |

``` 
- STREAM\_TYPE\_VIDEO = 2
- STREAM\_TYPE\_AUDIO = 1
- STREAM\_TYPE\_TEXT = 0
```

**Returns**
 
Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.
 
#### void setOnBufferingUpdateListener ( OnBufferingUpdateListener l )

This method registers a callback to be invoked when buffering event occurs during the playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            
 
#### void setOnCompletionListener ( OnCompletionListener l )

This method registers a callback to be invoked when the end of a media file has been reached during playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnDynamicThumbnailListener ( OnDynamicThumbnailListener l )

This method registers a callback to be invoked when a dynamic thumbnail event occurs during the playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnErrorListener (OnErrorListener l)

This method registers a callback to be invoked when an error occurs during the playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnExternalSubtitleChangedListener (OnExternalSubtitleChangedListener l)

This method registers a callback to be invoked when the external subtitle changes during playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnFastPlayListener ( OnFastPlayListener l )

This method registers a callback to be invoked when aFastPlayevent occurs during playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnInfoListener ( OnInfoListener l )

This method registers a callback to be invoked when an informational event occurs during the playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnMediaStreamChangedListener ( OnMediaStreamChangedListener l )

This method registers a callback to be invoked when the media stream changes during the playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnPauseCompleteListener ( OnPauseCompleteListener l )

This method registers a callback to be invoked when pause() is complete.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnPreparedListener ( OnPreparedListener l )

This method registers a callback to be invoked when the media file is loaded and ready to go.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnResumeCompleteListener ( OnResumeCompleteListener l )

This method registers a callback to be invoked when resume() is complete.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnSeekCompleteListener ( OnSeekCompleteListener l )

This method registers a callback to be invoked when seek() has successfully completed.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnStartCompleteListener ( OnStartCompleteListener l )

This method registers a callback to be invoked when start() has successfully completed.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnStopCompleteListener ( OnStopCompleteListener l )

This method registers a callback to be invoked when stopPlayback() has successfully completed.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setOnTimedMetaRenderRenderListener ( OnTimedMetaRenderRenderListener l )

This method registers a callback to be invoked when new timed metadata is ready for display in HLS.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| l   | The callback to be invoked.                                                                                                                                                            |
 
#### void setProperty ( NexPlayer.NexProperty property, Object value )

This method sets the value of an individual properties of the NexPlayer™.

It’s recommended to call this method after getting the OnConfigurationcallback by registering OnConfigurationListener on NexVideoView. We can not guarantee what result the NexPlayer™ will
return if this method is called at different state.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| property   | The property to set.                                                                                                                                                            |
| value   | The new value for the property.                                                                                                                                                   |
 
#### void setScalingMode ( ScalingMode mode )

This method sets the scaling mode for both output video and caption.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mode   | The scaling mode of current video and caption. One of the following scaling mode :                                                                                                                                                            |

```
- ScalingMode.SCALE_ASPECT_FIT
- ScalingMode.SCALE_TO_FILL
The default scaling mode isScalingMode.SCALE_ASPECT_FIT
```
 
#### void setSettings ( Settings settings )

This method sets the settings for NexPlayer, NexALFactory and Video and Caption renderer.

This method should be called before setVideoPath or setVideoURI to be able to set the setting successfully.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| settings   | The object with the setting values.                                                                                                                                                            |
 
#### void setVideoPath ( String path )

This method begins opening the media at the specified path or URL.

This method operates asynchronously, and when setVideoPath has successfully completed, and if OnPreparedListener is registered on NexVideoView, an onPrepared event will be called. Otherwise, when error occurs, and if OnErrorListener is registered on NexVideoView, an onError event will be
called.

> **Note** To change the setting value of NexvideoView, setSettings should be called before calling this method.
 
**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| path   | The location of the content: a path (for local content) or URL (for remote content).                                                                                                                                                      |
 
#### void setVideoURI ( Uri uri )

This method begins opening the media at a given URI.

This method operates asynchronously, and when setVideoPath has successfully completed, and if OnPreparedListener is registered on NexVideoView, an onPrepared event will be called. Otherwise,
when error occurs, and if OnErrorListener is registered on NexVideoView, an onError event will be
called.

> **Note** To change the setting value of NexvideoView, setSettings should be called before calling this method.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| uri   | The URI of the video.                                                                                                                                                      |
 
#### void setVideoURI ( Uri uri, Map<String, String> headers )

This method sets the video URI using specific headers and begins opening the media at a given URI.

This method operates asynchronously, and when setVideoPath has successfully completed, and if OnPreparedListener is registered on NexVideoView, an onPrepared event will be called. Otherwise,
when error occurs, and if OnErrorListener is registered on NexVideoView, an onError event will be
called.

> **Note** To change the setting value of NexvideoView, setSettings should be called before calling this method.
 
**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|-------------------|
| uri   | The URI of the video.                                                                                                                                                      |
| headers   | The headers for requesting the URI. The header formats are specified on addHTTPHeaderFields.                                                                                                                                                   |
 
#### void start ( )

Starts playing media from the specified timestamp.

This method must be called after onPrepared() method has been successfully called by setVideoPath or setVideoURI.

This method operates asynchronously therefore, when start() is successful, and if OnStartCompleteListener is registered onNexVideoView, a onStartComplete event will be called. Otherwise, when error occurs, and if OnErrorListener is registered on NexVideoView, an onError event will be called.

#### void start ( int msec )

Starts playing media from the specified timestamp.

This method must be called after onPrepared() method has been successfully called by setVideoPath or setVideoURI.

This method operates asynchronously and when start() is successful, and if OnStartCompleteListener is registered on NexVideoView, a onStartComplete event will be called. Otherwise, when error occurs, and if OnErrorListener is registered on NexVideoView, an onError event will be called.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| msec   | The offset (in milliseconds) from the beginning of the media at which to start playback. This should be zero to start at the beginning. |
 
#### void stopPlayback ( )

This method stops the current playback.

This method operates asynchronously, and when stop has successfully completed, and if OnStopCompleteListener is registered on NexVideoView, an onStopComplete event will be called.
 
### NexWVDRMSession Class Reference

This class allows NexPlayer™ to handle and descramble WideVine HLS content.

**Classes**

- `class _CdmRequestMsg`
- `interface IWVDRMSessionListener`

#### void setOptionalHeaderFields ( HashMap<String, String> optionalHeaderFields )

This method sets optional Parameters when sending requests to the Key Server of NexWVDRM.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| optionalHeaderFields   | HashMap is included in the key request message to allow a client application to provide additional message parameters to the server.                                                                                                                                                            |
 
### NexPlayer.OfflineMode Enum Reference

**Public Attributes**

- `NONE = (0)`
- `STORE = (1)`
- `RETRIEVE = (2)`
- `RETRIEVE_STORE = (3)`
- `KEYEXPIRE_RETRIEVE_STORE = (4)`

### NexVideoView.OnBufferingUpdateListener Interface Reference

The application must implement this interface in order to receive buffering events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.

#### void onBuffering ( NexPlayer mp, int progressInPercent )

reports the current buffering status.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer™ object to which this event applies.                                                                                                                                                            |
| progressInPercent   | The current buffering percentage.                                                                                                                                                   |
 
#### void onBufferingBegin ( NexPlayer mp )

the start of buffering.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer™ object to which this event applies.                                                                                                                                                            |
 
#### void onBufferingEnd ( NexPlayer mp )

This reports the end of buffering.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer™ object to which this event applies.                                                                                                                                                            |
 
### NexVideoView.OnCompletionListener Interface Reference

The application must implement this interface in order to receive NexVideoView events when playback is successful up to the end of the content.

When the playback has completed and onCompletion is returned, setVideoPath or setVideoURI should
be called only after when the player has stopped successfully and onStopComplete is returned by calling stopPlayback.

It is suggested to call stopPlayback at onCompletion. However there are two cases with exceptions :

1. When destroying activity after playback has completed. In this case, request Activity.finish at onCompletion, then call release when activity is destroyed.
2. When seek back to the beginning of content when playback has completed. In this case, seek to a desired position by using seekTo at onCompletion, then call resume.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may
not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is
to use android.os.Handler to post an event back to the main application thread.

#### void onCompletion ( NexPlayer mp )

This method indicates when playback is successful up to the end of the content.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlaye™ object generating the event.                                                                                                                                                            |
 
### NexVideoView.OnConfigurationListener Interface Reference

The application must implement this interface in order to receive NexVideoView events before NexPlayer™ is opened.

The application must implement settings for the NexPlayer™ before the NexPlayer.open() such assetProperty.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may
not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is
to use android.os.Handler to post an event back to the main application thread.
 
### NexVideoView.OnDynamicThumbnailListener Interface Reference

The application must implement this interface in order to receive Dynamic Thumbnail related events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may
not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 

#### void onDynamicThumbnailData ( int cts, Bitmap bitmap )

This method will be called by the NexPlayer™ engine when thumbnail data is created.

**Parameters**

| Name   | Description                                                                                                                                                  
|--------|---------------|
| cts   | The current timestamp of the thumbnail image.  |
| bitmap   | RGB buffer pointer(RGB565) of the thumbnail image.                                                                                                                                                   
 
### NexVideoView.OnErrorListener Interface Reference

The application must implement this interface in order to receive error events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
#### void onError (NexPlayer mp, NexPlayer.NexErrorCode errorCode )

An error has occurred during playback.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer™ object generating the event.                                                                                                                                                            |
| errorCode   | The error code for the generated error.                                                                                                                                                   |
 
### NexVideoView.OnExternalSubtitleChangedListener Interface Reference

The application must implement this interface in order to receive onExternalSubtitleChanged events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
#### void onExternalSubtitleChanged ( NexPlayer mp, int result )

An event will occur when addSubtitleSource is successful.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer™ object to which this event applies.                                                                                                                                                            |
| result   | Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.                                                                                                                                                   |
 
### NexVideoView.OnFastPlayListener Interface Reference

The application must implement this interface in order to receive fastPlay related events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
#### void onFastPlayStart ( NexPlayer mp, int result )

An event will occur when fastPlayStart is successful.

**Parameters**

| Name   | Description                                                                                                                                                   
|--------|-----------------|
| mp   | The NexPlayer™ object to which this event applies. |
| result   | Zero for success, or a non-zero NexPlayer™ error code in the event of a failure. |
 
#### void onFastPlayStop ( NexPlayer mp, int result )

An event will occur when fastPlayStop is successful.

**Parameters**

**Parameters**

| Name   | Description                                                                                                                                                   
|--------|-----------------|
| mp   | The NexPlayer™ object to which this event applies.|
| result   | Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.|
 
### NexVideoView.OnInfoListener Interface Reference

This interface transfer updated NexContentInformation to the application.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
#### void onInfo ( NexPlayer mp, NexContentInformation info )

An event will occur when NexContentInformation is being updated.

**Parameters**

| Name   | Description|
--------|-------------------|
| mp   | The NexPlayer™ object to which this event applies.  |
| info   | The information of the current content.|

### NexVideoView.OnMediaStreamChangedListener Interface Reference

The application must implement this interface in order to receive onMediaStreamChanged events from Nex-
VideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
  
#### void onMediaStreamChanged (NexPlayermp,intresult,intstreamType,intstreamID)

An event will occur when setMediaStream is successful.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer™ object to which this event applies.|
|result| Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.|
|streamType| The type of changed stream. This will be one of the supported stream types ofsetMediaStream.|
|streamID| The ID of changed stream.|
 
### NexVideoView.OnPauseCompleteListener Interface Reference

The application must implement this interface in order to receive onPauseComplete events fromNexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
  
#### void onPauseComplete (NexPlayermp)

An event will occur whenpauseis successful.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer™ object to which this event applies.|

 
### NexVideoView.OnPreparedListener Interface Reference

The application must implement this interface in order to receiveNexVideoViewevents when NexPlayer™ is ready for the playback.

This callback must be registered to operateNexVideoViewsuccessfully.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
  
#### void onPrepared (NexPlayermp)

This method is called when setVideoPath or setVideoURI is successful.

In case of an error, an onError event will occur instead of anonPreparedevent.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer™ object to which this event applies.|
 
### NexVideoView.OnResumeCompleteListener Interface Reference

The application must implement this interface in order to receiveonResumeCompleteevents fromNexVideo-
View.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
 
#

#### void onResumeComplete (NexPlayermp)

An event will occur whenresumeis successful.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer™ object to which this event applies.|
 
### NexVideoView.OnSeekCompleteListener Interface Reference

The application must implement this interface in order to receive events fromNexVideoViewwhenseekis
successful.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
#### void onSeekComplete (NexPlayer mp, int result, int position)

An event will occur when seekTo is successful.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer object to which this event applies.|
|result| Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.|
|position| The actual position at which the seek command completed. Depending on the media format, this maybe different than the position that was requested for the seek operation.|
  
### NexVideoView.OnStartCompleteListener Interface Reference

The application must implement this interface in order to receiveonstartCompleteevents fromNexVideo-
View.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.

#### void onStartComplete (NexPlayer mp)

An event will occur when start() is successful.

In case of an error,onErrorwill occur instead of anonStartCompleteevent.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer™ object to which this event applies.|
  
### NexVideoView.OnStopCompleteListener Interface Reference

The application must implement this interface in order to receiveonStopCompleteevents fromNexVideo-
View.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
  
#### void onStopComplete (NexPlayer mp,int result)

An event will occur whenstopPlaybackis successful.


**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer™ object to which this event applies.|
|result| Zero for success, or a non-zero NexPlayer™ error code in the event of a failure.|
 
### NexVideoView.OnTimedMetaRenderRenderListener Interface Reference

The application must implement this interface in order to receiveTimedMetaevents fromNexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread. 

**See Also**
 
NexPlayer.IListener onTimedMetaRenderRender
 
#### void onTimedMetaRenderRender (NexPlayer mp, NexID3TagInformation timedMeta)

This method is called when new timed metadata is ready for display in HLS.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer™ object to which this event applies.|
| timedMeta| An NexID3TagInformation object that contains the timed metadata associated with the content to be displayed.|
 
### NexVideoView.OnTimeUpdateListener Interface Reference

**Public Member Functions**

- `void onTime (NexPlayer mp, int currTime)`

### PiffPlayReadyDRMManager Class Reference

This class allows NexPlayer™ to support and handle PIFF PlayReady encrypted content.

NexPlayer™ implements this when it receives any PIFF PlayReady content so that it may be decrypted if required.

> **Deprecated** For internal use only. Please do not use.

#### static native int initDRMManager ( String strEngineLibName) [static]

Initializes and registers the PiffPlayReadyDRMManager.

**Parameters**

| Name  | Description  | 
|---|---|
|strEngineLibName|The relevant engine library name as a string.|
 
#### static native int initDRMManagerMulti (Object nexPlayerHandle,String strEngineLibName) [static]

internal use only. Please do not use.

### NexPlayer.PROGRAM_TIME Class Reference

This class handles the date and time information included in the #EXT-X-PROGRAM-DATE-TIME tag in HLS content.

It can be used with the method to determine when an HLS segment should be played or to help sync content and associated text streams.

#### PROGRAM_TIME( )

This is the `PROGRAM_TIME` constructor.

#### long getOffset ( )

This method gets the time offset of the currently decoded frame’s timestamp with respect to time information in the #EXT-X-PROGRAM-DATE-TIME tag.

#### String getTAG ( )

This method gets the HLS tag, #EXT-X-PROGRAM-DATE-TIME, if included in HLS content.

#### void setOffset ( long offset)

This method sets the time offset from the most recent #EXT-X-PROGRAM-DATE-TIME tag in HLS content.

**Parameters**

| Name   | Description                                                                                                   |
|--------|-----------|
| offset | The time offset of the current frame from the most recent #EXT-X-PROGRAM-DATE-TIME tag time, in milliseconds. |

#### void setTAG (String tag)

This method sets the #EXT-X-PROGRAM-DATE-TIME tag for the current HLS content.

### NexMediaDrmSession.ProvisioningManager Interface Reference

**Public Member Functions**

- `void provisionRequired` (NexMediaDrmSession session)
- `void onProvisionError` (Exception error)
- `void onProvisionCompleted ()`

### RegisterDLAPIExManager Class Reference

> **Deprecated** For internal use only. Please do not use.

#### static native int initDLAPIExManagerMulti (Object nexPlayerHandle,String strEngineLibName) *[static]*

Internal use only. Please do not use.

### remoteFileIOManager Class Reference

**Static Public Member Functions**

- `static native int registerRemoteFileIO (String strEngineLibName)`
- `static native int registerRemoteFileIOMulti (Object nexPlayerHandle, String strEngineLibName)`
    
    internal use only.


#### static native int registerRemoteFileIOMulti (Object nexPlayerHandle,String strEngineLibName) *[static]*

internal use only.

Please do not use.

### NexTextureView.Renderer Class Reference

**Public Member Functions**

- `void onDrawFrame (GL10 gl)`
- `void onSurfaceChanged (GL10 gl, int width, int height)`
- `void onSurfaceCreated (GL10 gl, EGLConfig config)`
- `void onSurfaceDestroyed (GL10 gl)`

### NexCaptionRenderView.RenderingArea Class Reference

### NexVideoView.ScalingMode Enum Reference

This enumeration defines the possible scaling mode for output video and captions.

- `SCALE_ASPECT_FIT` : The size of the output video and caption will be adjusted according to the size of the
    video view, keeping its original aspect ratio.
- `SCALE_TO_FILL` : The output video and caption will fill the video view, ignoring its original aspect ratio.

**Public Member Functions**

- `ScalingMode (int mode)`
- `int getInteger ()`

**Public Attributes**

- `SCALE_ASPECT_FIT = (0)`
- `SCALE_TO_FILL = (1)`
- `SCALE_ASPECT_FILL = (2)`
- `int mMode`

### NexABRController.SegmentOption Enum Reference

This enum defines the options possible for how `NexPlayer`™ should handle existing buffered content as a track changes (due to a set target bandwidth).

While `NexPlayer`™ will by default change to a new target bandwidth as optimally as possible, there may be instances when it is preferable either for an application to preferentially change to the target bandwidth track more quickly (regardless of buffered content segments) or to first play buffered segments before changing tracks.

These segment options can be used to set the parameter *segOption* when calling *setTargetBandwidth* to one of the following:

- `DEFAULT` : Default (`NexPlayer`™ will decide between *QUICKMIX* (changing tracks quickly) and *LATEMIX*
    (playing buffered content and changing tracks more slowly)).
- `QUICKMIX` : NexPlayer™ will clear the buffer as much as possible and will start to download new track so
    user can see a new track faster.
- `LATEMIX` : NexPlayer™ will preserve and play the content segments already buffered and will download a
    new track.


**Public Member Functions**

- `SegmentOption (int code)`

**Public Attributes**

- `DEFAULT = (0x00000000)`
    
    Default. `NexPlayer`™ will decide betweenQUICKMIXandLATEMIXoptions automatically.
- `QUICKMIX = (0x00000001)`
    
    `NexPlayer`™ will clear the buffer quickly and will start downloading new track segments more quickly.
- `LATEMIX = (0x00000002)`
    
    `NexPlayer`™ will preserve buffered segments and will download new track.
- `int mCode`

**See Also**

- setTargetBandwidth


### NexVideoView.Settings Class Reference

This class manages the setting values needed for initializing Video Renderer, Caption Renderer and `NexPlayer`™ internally.

To initialize successfully,*setSettings* must be called before *setVideoPath* or *setVideoURI* is called, after changing the setting value by using *setValue*. Note that *setSettings* is not guaranteed to work properly when called at any other time.

**Classes**

- `enum CEARenderMode`
    
    This enumeration defines the possible modes for CEA rendering.

**Static Public Attributes**

- `static final int INT_LOG_LEVEL = 0`
    
    Possible key value for *key* parameter of `setValue`.
- `static final int CEA_RENDER_MODE = 1`
    
    Possible key value for *key* parameter of `setValue`.
- `static final int PIXELFORMAT_FORMAT = 2`
    
    Possible key value for *key* parameter of `setValue`.
- `static final int BOOL_USE_UDP = 3`
    
    Possible key value for *key* parameter of `setValue`.

**Protected Attributes**

- `int mLogLevel = 0`
- `int mPixelFormat = PixelFormat.RGBA_8888`
- `CEARenderMode mCEARenderMode = CEARenderMode.CEA_608`
- `boolean mCEA608Standard = true`
- `boolean mUseUDP = false`

#### Object getValue (int key)

This method gets the setting value correspondent to a specific key.

**Parameters**

| Name | Description                        |
|------|----------------|
| key  | The key to retrieve setting value. |

**Returns**

The value correspondent to the key.

#### boolean setValue (int key,int value)

This method sets the setting values for the properties of `NexPlayer`™.

**Parameters**

| Name  | Description                                                                                                                                         |
|-------|---------------------------|
| key   | The key to set new settings value, as an *integer*. This will be one of the following values : - **0 : INT_LOG_LEVEL** - **2 : PIXELFORMAT_FORMAT** |
| value | The new value for the property, as an *integer*.                                                                                                |
**Returns**

The value of the property.

#### boolean setValue (int key,boolean value)

This method sets the setting values for the properties of `NexPlayer`™.

**Parameters**


| Name  | Description                                                                                    |
|-------|-------------------------|
| key   | The key to set new settings value, as an integer. Supported key value : 3: BOOL\_USE\_UDP |
| value | The new value for the property, in boolean.|

**Returns**

The value of the property.

#### boolean setValue (int key, CEARenderMode value)

This method sets the setting values for the properties of `NexPlayer`™.


**Parameters**

| Name  | Description                                                                                         |
|-------|-------------|
| key   | The key to set new settings value, as an *integer*. Supported key value : 1: CEA\_RENDE\R_MODE |
| value | The new value for the property.|

**Returns**

The value of the property.

#### final int CEA_RENDER_MODE = 1 *[static]*

Possible key value forkeyparameter of `setValue`.

This will be one of the following values :

- `Settings.CEARenderMode.CEA_608`: Print CEA 608 in the case where there are both CEA 708 and CEA
    608 closed captions available.
- `Settings.CEARenderMode.CEA_708`: Print CEA 708 in the case where there are both CEA 708 and CEA
    608 closed captions available.

#### final int INT_LOG_LEVEL = 0 *[static]*

Possible key value forkeyparameter of setValue.

Possible value range : -1 to 5

#### final int PIXELFORMAT_FORMAT = 2 *[static]*

Possible key value for *key* parameter of `setValue`.

This will be one of the following values :

- `PixelFormat.RGBA_8888`
- `PixelFormat.RGB_565`

### SmoothStreamFragmentDRMManager Class Reference

This class allows `NexPlayer`™ to support and handle Smooth Streaming fragment encrypted content.

`NexPlayer`™ implements this when it receives any Smooth Streaming fragment content so that it may be decrypted if required.

**Deprecated** For internal use only. Please do not use.

#### static native int initDRMManager (String strEngineLibName) [static]

Initializes and registers the `SmoothStreamFragmentDRMManager`.

**Parameters**

| Name             | Description                                   |
|------------------|---------------------------|
| strEngineLibName | The relevant engine library name as a string. |

#### static native int initDRMManagerMulti (Object nexPlayerHandle,String strEngineLibName) [static]

Internal use only. Please do not use.

### SmoothStreamPiffDRMManager Class Reference

This class allows `NexPlayer`™ to support and handle Smooth Streaming Piff encrypted content.

`NexPlayer`™ implements this when it receives any Smooth Streaming Piff content so that it may be decrypted if required.

**Deprecated** For internal use only. Please do not use.

#### static native int initDRMManager (String strEngineLibName) *[static]*

Initializes and registers the `SmoothStreamPiffDRMManager`.

**Parameters**

| Name             | Description                                   |
|------------------|---------------------------|
| strEngineLibName | The relevant engine library name as a string. |

#### static native int initDRMManagerMulti (Object nexPlayerHandle,String strEngineLibName) *[static]*

Internal use only. Please do not use.

### SmoothStreamPlayReadyDRMManager Class Reference

This class allows `NexPlayer`™ to support and handle Smooth Streaming PlayReady encrypted content.

`NexPlayer`™ implements this when it receives any Smooth Streaming PlayReady content so that it may be decrypted if required.

> **Deprecated** For internal use only. Please do not use.

#### static native int initDRMManager (String strEngineLibName) *[static]*

Initializes and registers the `SmoothStreamPlayReadyDRMManager`.

**Parameters**

| Name             | Description                                   |
|------------------|---------------------------|
| strEngineLibName | The relevant engine library name as a string. |

#### static native int initDRMManagerMulti (Object nexPlayerHandle,String strEngineLibName) *[static]*

internal use only.

Please do not use.

### NexStatisticsMonitor.StatisticsError Enum Reference

An enumeration of the statistics-related errors possible when using `theNexStatisticsMonitor`.

#### ERROR_DURATION_INVALID

The duration set is invalid or cannot be applied to the statistics being requested.

#### ERROR_NONE

Playback statistics were successfully retrieved without error.

#### ERROR_TYPE_INVALID

The type of statistics being requested is invalid.

### NexCaptionSetting.StringStyle Enum Reference

This enumeration defines the behavior for caption string style.

These are available caption string styles :

- `NONE` : None.
- `DEFAULT` : Apply a string style by provider.
- `APPLY` : Apply a string style by user.
- `REMOVE` : Remove a string style whatever it is provided by a user or a content to be applied.

### NexStatisticsMonitor.SystemStatisticsMetric Enum Reference

This is an enumeration of the possible system statistics that can be requested during playback of HLS, DASH or SS content in `NexPlayer`™.

These statistics are only related to the system performance during playback. For other statistics specifically about the HLS, DASH or SS content playback or HTTP statistics, monitor *GeneralStatisticsMetric* or *HttpStatisticsMetricinstead*.

**See Also**

- GeneralStatisticsMetric
- HttpStatisticsMetric
- setDuration

#### SystemStatisticsMetric (int code)

Sets the system statistics metric.

#### int getCode ()

Gets the system statistics code, as an integer.

**Returns**

The system statistics code requested, as an integer.

Implements `NexStatisticsMonitor.IStatistics`.

#### CPU_USAGE = ( 0x00010000 )

The current CPU usage, as a percentage, represented as a value between 0 and 1, where zero is 0 percent and 1 is 100 percent.

#### FREE_MEMORY_KB = ( 0x00020000 )

The current amount of memory free, in kilobytes, as a *long*.

### NexABRController.TargetOption Enum Reference

This enumeration defines the possible options for how an application should use a target bandwidth set. 

The options defined by this enumeration are possible values used to set the *targetOption* parameter when calling *setTargetBandwidth* to set a new target bandwidth for streaming content with multiple tracks at different bandwidths such as HLS.

By default, when a target bandwidth is set, `NexPlayer`™ will choose the closest track available at a bandwidth below the target. For example, if there is content with five tracks at bandwidths of 500k, 900k, 1200k, 1500k, and 2000k, and the target bandwidth is chosen as 1200k with the option set to *DEFAULT* or *BELOW*, the targe t bandwidth will be set to 900k. If instead the target option is set to *ABOVE* in the same example, `NexPlayer`™ will set the target bandwidth to 1500k.

If a target bandwidth is to be set exactly, using the target option *MATCH*, then the target value will ONLY be changed if exactly a track with a bandwidth exactly the same as the value set is available.

The target option should be set to one of the following:

- `DEFAULT` : Default target option (*BELOW*)
- `BELOW*` : Select a track with a bandwidth below the target bandwidth.
- `ABOVE` : Select a track with a bandwidth above the target bandwidth.
- `MATCH` : Select the track that has a bandwidth that matches the target set; otherwise send an error and no new target bandwidth is selected.

**See Also**

- `setTargetBandWidth`

### NexClosedCaption.TextBlink Class Reference

This property requests blinking text for the indicated character range.

#### short getEndOffset ( )

This property specifies the ending position of the character.

**Returns**

The character number position, not the bytes.

#### short getStartOffset ( )

This property specifies the starting position of the character.

**Returns**

The character number position, not the bytes.

### NexClosedCaption.TextHighlight Class Reference

This property specifies the position of the highlighted text.

#### short getEndChar ( )

This property specifies the ending position of the character.

**Returns**

The character number position, not the bytes.

#### short getStartChar ( )

This property specifies the starting position of the character.

**Returns**

The character number position, not the bytes.

### NexClosedCaption.TextHighlightColor Class Reference

This property specifies the color of the highlighted text.

#### int getHighlightColor ( )

This property specifies the color of the highlighted character.

**Returns**

The color of highlighted character.

### NexClosedCaption.TextHyperText Class Reference

This property specifies the hyperlink of text that describes the hypertext information.

#### String getAlt ( )

An ’alt’ string for user display.

The altString is a tool-tip or other visual clue.

**Returns**

alt String of this class.

#### short getEndOffset ( )

This property specifies the ending position of the character.

**Returns**

The character number position, not the bytes.

#### short getStartOffset ( )

This property specifies the starting position of the character.

**Returns**

The character number position, not the bytes.

#### String getURL ( )

The link to URL.

**Returns**

URL link of this class.


### NexClosedCaption.TextKaraoke Class Reference

This property specifies the number of highlighted text.

#### int getCount ( )

This property specifies the number of the TextKaraokeEntry.

**Returns**

The total number of the TexKaraokeEntry.

#### int getCurrentCount ( )

This property specifies the current number of the TextKaraokeEntry.

**Returns**

The current TextKaraokeEntry index.

#### TextKaraokeEntrygetKaraokeEntry (int index)

This property gets specific `TextKaraokeEntry`.


**Parameters**

| Name  | Description                                   |
|-------|---------------------------|
| index | The index of the specific *TextKaraokeEntry*. |

**Returns**

The specific TextKaraokeEntry.

#### int getStartTime ( )

This property specifies the starting time of the whole KaraokeEntry.

**Returns**

The start time of the whole KaraokeEntry.

#### void setKaraokeEntry (TextKaraokeEntry entry)

Adds the `TextKaraokeEntry` to this specific class.

**Parameters**

| Name  | Description                                     |
|-------|---------|
| entry | The *TextKaraokeEntry* for *TextKaraoke* class. |

### NexClosedCaption.TextKaraokeEntry Class Reference

This property specifies the karaoke type highlighted text.

#### short getEndCharOffset ( )

This property specifies the ending position of the character.

**Returns**

The character number position, not the bytes.

#### short getStartCharOffset ( )

This property specifies the starting position of the character.

**Returns**

The character number position, not the bytes.

### NexClosedCaption.TextScrollDelay Class Reference

This property specifies the delaying time of the scrolling text.

#### int getScrollDelay ( )

This method returns the delaying time of this class.

**Returns**

ScrollDelay time.

### NexClosedCaption.TextStyle Class Reference

This property specifies the style of the text and sets the `TextStyleEntry`.

#### int getCount ( )

This property specifies the number of the `TextStyleEntry`.

**Returns**

The total number of the TextStyleEntry.

#### int getCurrentCount ( )

This property specifies the current number of the `TextStyleEntry`.

**Returns**


The current `TextStyleEntry` index.

#### TextStyleEntrygetStyleEntry (int index)

This property gets specific `TextStyleEntry`.

**Parameters**

| Name  | Description                               |
|-------|-----------------------|
| index | The index of the specific `TextStyleEntry`. |

**Returns**

The specific `TextStyleEntry`.

#### void setTextStyleEntry (TextStyleEntry entry)**

Adds the `TextStyleEntry` to this specific class.

**Parameters**

| Name  | Description                               |
|-------|-----------------------|
| entry | `The TextStyleEntry` for TextStyle class. |


### NexClosedCaption.TextStyleEntry Class Reference

Both the sample format and the sample description contain style records, so it is define here for compactness.

3GPP timed text

#### boolean getBold ( )

This property specifies the Bold font type that will be used for this style.

**Returns**

TRUE if *bold* , FALSE if not.

#### short getEndChar ( )

This property specifies the ending position of the character.

**Returns**

The character number position, not the bytes.

#### int getFontColor ( )

This property specifies the font color that will be used for this style.

**Returns**

The color of the font.

#### short getFontID ( )

This property specifies the font type that will be used for this style.

**Returns**

The font table index.

#### short getFontSize ( )

This property specifies the font size that will be used for this style.

**Returns**

The pixel of the font.

#### boolean getItalic ( )

This property specifies the Italic font type that will be used for this style.

**Returns**

`TRUE` if italic, `FALSE` if not.

#### short getStartChar ( )

This property specifies the starting position of the character.

**Returns**

The character number position, not the bytes.

#### boolean getUnderline ( )

This property specifies the Underline font type that will be used for this style.

**Returns**

`TRUE` if *underline* , `FALSE` if not.

### NexClosedCaption.TextWrap Enum Reference

This property specifies the text wrap behavior.

**Public Member Functions**

- `int getValue ()`

**Static Public Member Functions**

- `static TextWrap fromValue*(int value)`

**Public Attributes**

- `NO_WRAP = (0)`

- `AUTOMATIC_SOFT_WRAP = (1)`


### NexThumbnail.ThumbnailInformation Class Reference

**Public Member Functions**

- `int getThumbnailInfoWidth ()`
- `int getThumbnailInfoHeight ()`
- `int getThumbnailInfoPitch ()`
- `int getThumbnailInfoRatate ()`

### NexClosedCaption.TTML_DisplayAlign Enum Reference

This enumeration determines the display alignment of CFF timed text (TTML) in content.

It corresponds to the *tts:displayAlign* attribute, and indicates how timed text should be aligned vertically in blocks on the screen when they are displayed.

**Public Member Functions**

- `TTML_DisplayAlign** (int value)`
- `int getValue ()`

**Static Public Member Functions**

- `static TTML_DisplayAlign fromValue (int value)`


#### After = (3)

The block of timed text (TTML) should be aligned vertically "after" the center of the display block.

#### Before = (1)

The timed text (TTML) should be aligned vertically "before" the center of the display block.

#### Center = (2)

The timed text (TTML) should be centered vertically in the display block.

#### Default = (0)

The timed text (TTML) should be aligned in the default alignment.

### NexClosedCaption.TTML_Fontstyle Enum Reference

This enumeration determines the font style of CFF timed text (TTML) in content.

It corresponds to the *tts:fontStyle* attribute, and indicates how timed text font should be displayed.

**Public Member Functions**

- `int getValue ()`

**Static Public Member Functions**

- `static TTML_Fontstyle fromValue (int value)`

#### Default = (0)

The timed text (TTML) font should be displayed as default.

#### Italic = (2)

The timed text (TTML) font should be displayed initalics.

#### Normal = (1)

The timed text (TTML) font should be displayed normally.

#### Oblique = (3)

The timed text (TTML) font should be displayed with a shear transformation at an oblique angle.

### NexClosedCaption.TTML_LengthType Enum Reference

This enumeration specifies which type of length is being used in the style properties of a content’s timed text (TTML).

It corresponds to the units in the<length>expression for timed text TTML style property values.

**Public Member Functions**

- `int getValue ()`

**Static Public Member Functions**

- `static TTML_LengthType fromValue (int value)`
 
#### c = (4)

The length is expressed in cells.

#### Default = (0)

No unit of length is specified, which is an error.

#### em = (3)

The length is expressed in pixels, but is the font dimension length in the direction specified when relative to a font
with a size expressed as two unequal length measures.

#### percent = (1)

The length is expressed as a percent.

#### px = (2)

The length is expressed in pixels.

### NexClosedCaption.TTML_StyleLength Class Reference

This class describes the length of every timed text (TTML) attribute.

This will be determined based on the units of the "type" of length, as specified by `TTML_LengthType`.

**Public Member Functions**

- `int getLength ()`
- `TTML_LengthType getType ()`

**Public Attributes**

- `float length`
- `TTML_LengthType lengthType`

### NexClosedCaption.TTML_TextAlign Enum Reference

This enumeration determines the horizontal alignment of timed text (TTML) in content.

It corresponds to the *tts:textAlign* attribute, and indicates how timed text should be aligned horizontally in display blocks of the subtitles.

**Public Member Functions**

- `int getValue ()`

**Static Public Member Functions**

- `static TTML_TextAlign fromValue (int value)`


#### Center = (3)

The timed text (TTML) should be displayed aligned with the center of the text block.

#### Default = (0)

The timed text (TTML) should be displayed in the default alignment.

#### End = (5)

The timed text (TTML) should be displayed aligned with the end of the text block.

#### Left = (2)

The timed text (TTML) should be displayed aligned to the left of the text block.

#### Right = (4)

The timed text (TTML) should be displayed aligned to the right of the text block.

#### Start = (1)

The timed text (TTML) should be displayed aligned with the start of the text block.

### NexClosedCaption.TTML_TextOutlineStyleLength Class Reference

This class determines how timed text (TTML) in content should be displayed in text outline format.

It corresponds to the *tts:textOutline* attribute, and can indicate the color and thickness of the outline, as well as the blur radius.

**Public Member Functions**

- `int getColor ()`
    
    This method gets the color to be used to outline timed text (TTML) in Text Outline style, if present.
- `TTML_StyleLength getType1 ()`
    
    This method gets the thickness of the outline of timed text (TTML) in Text Outline style.
- `TTML_StyleLength getType2 ()`
    
    This method gets the blur radius of the outline of timed text (TTML) in Text Outline style, if present.

### NexClosedCaption.TTML_UnicodeBIDI Enum Reference

This enumeration specifies a directional embedding or override of text direction for timed text (TTML) in content.

It corresponds to the *tts:unicodeBidi* attribute, and relates to how text will be displayed according to the Unicode bidirectional algorithm.

**Public Member Functions**

- `int getValue ()`

**Static Public Member Functions**

- `static TTML_UnicodeBIDI fromValue (int value)`

#### BidiOverride = (3)

The timed text (TTML) should be displayed overriding the normal directionality of the text script.

This would allow, for example, the characters in Latin script (which are normally displayed left-to-right) to be displayed right-to-left instead.

#### Default = (0)

No attribute was specified; the timed text (TTML) should be displayed as normal by default.

#### Embed = (2)

The timed text (TTML) should be displayed with embedded directionality.

#### Normal = (1)

The timed text (TTML) should be displayed as normal.

### NexClosedCaption.TTML_WritingMode Enum Reference

This enumeration specifies the mode in which timed text (TTML) in content will be displayed.

This corresponds to the *tts:writingMode*, where the modes indicate how timed text and timed text blocks will be arranged when displayed. This allows different language text to be displayed for example vertically, or from right-to-left when required.
**Public Member Functions**

- `int getValue ()`

**Static Public Member Functions**

- `static TTML_WritingMode fromValue (int value)`


#### Default = (0)

The timed text (TTML) should be displayed as lrtb (left-to-right, top-to-bottom) as default.

#### lr = (5)

The timed text (TTML) should be displayed left-to-right.

#### lrtb = (1)

The timed text (TTML) should be displayed as left-to-right, top-to-bottom, as with standard Latin text.

#### rl = (6)

The timed text (TTML) should be displayed right-to-left.

#### rltb = (2)

The timed text (TTML) should be displayed right-to-left, top-to-bottom, as with Hebrew script.

#### tb = (7)

The timed text (TTML) should be displayed top-to-bottom.

#### tblr = (4)

The timed text (TTML) should be displayed top-to-bottom, left-to-right.

This is for displaying vertically oriented scripts, as in some Asian languages.

#### tbrl = (3)

The timed text (TTML) should be displayed top-to-bottom, right-to-left.

This is for displaying vertically oriented scripts, as in some Asian languages.


### NexClosedCaption.WebVTT_CueSpanTag Enum Reference

This enumeration defines the text track cue span tags for how WebVTT text tracks should be displayed.

Additional details about WebVTT cue spans can be found in the WebVTT specifications at *http://dev.w3.org/html5/webvtt/*.

**Public Member Functions**

- `int getValue ()`

**Static Public Member Functions**

- `static WebVTT_CueSpanTag fromValue (int value)`

#### BOLD = (3)

WebVTT cue span tag indicating bold text should be displayed.

#### CLASS = (1)

WebVTT cue span tag indicating the cue class.

#### ITALIC = (2)

WebVTT cue span tag indicating text should be displayed in italics.

#### LANGUAGE = (8)

WebVTT cue span tag indicating the language of cue, and must be a valid BCP 47 language tag.

#### LIST = (0)

WebVTT cue span tag indicating the cue list.

#### RUBY = (5)

WebVTT cue span tag indicating that the text represents a Ruby base and should be displayed with the RUBY_TEXT
indicated by another cue span.

#### RUBY_TEXT = (6)

WebVTT cue span tag indicating the ruby text to be displayed above the ruby base text (indicated by the RUBY element).

#### TEXT = (9)

WebVTT cue span tag indicating the cue text.

#### TIMESTAMP = (10)

WebVTT cue span tag indicating the timestamp of the cue.

#### UNDERLINE = (4)

WebVTT cue span tag indicating text should be displayed underlined.

#### UNKNOWN = (11)

Used when a WebVTT cue span tag is not recognized.

#### VOICE = (7)

WebVTT cue span tag indicating the name of the voice of the cue text.

This means for example, if cues represented a conversation happening between two individuals (Kim and Jon), this cue span would be used to indicate who was speaking the associate cue ie *kim* or *jon*.

### NexClosedCaption.WebVTT_TextAlign Enum Reference

This enumeration determines the horizontal alignment of timed text (WebVTT) in content.

It corresponds to the WebVTT alignment cue setting and are relative to the text direction. This indicates how WebVTT cues should be aligned horizontally in the text track regions of the content.

#### Default = (0)

WebVTT cue captions are aligned in the default location.

#### End = (3)

WebVTT cue captions are aligned at the end of the text track region.

#### Left = (4)

WebVTT cue captions are aligned on the left in the text track region.

#### Middle = (2)

WebVTT cue captions are aligned in the middle of the text track region.

#### Right = (5)

WebVTT cue captions are aligned on the right in the text track region.

#### Start = (1)

WebVTT cue captions are aligned at the start of the text track region.

### NexClosedCaption.WebVTT_WritingDirection Enum Reference

This enumeration specifies how WebVTT captions in content will be displayed.

This allows different language text to be displayed for example vertically, or from right-to-left when required.

**Public Member Functions**

- `int getValue ()`

**Static Public Member Functions**

- `static WebVTT_WritingDirection fromValue (int value)`

**Public Attributes**

- `Default = (0)`
- `Horizontal = (1)`
- `Vertical_Growing_Left = (2)`
- `Vertical_Growing_Right = (3)`


### NexClosedCaption.WebVTTRenderingData Class Reference

**Classes**

- `class WebVTTNodeData`
