# API Documentation

### AsfPlayReadyDRMManager Class

#### static native int initDRMManager (String strEngineLibName)

Initializes and registers the **AsfPlayReadyDRMManager**.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|


### DashDRMManager Class Reference

#### static native int initDRMManager (String strEngineLibName)

Initializes and registers the **DeceUVDRMManager**.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 

#### static native int initDRMManager (String strEngineLibName)

Initializes and registers DRMManager.

**Parameters**
 
| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|



#### static native int initManager (String strEngineLibName)

Initializes and registers the GetHttpAuthInfoManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initManager (String strEngineLibName)

Initializes and registers the GetKeyExtManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initManager (String strEngineLibName)

Initializes and registers the GetPDBlockManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initManager (String strEngineLibName)

Initializes and registers the GetPlaylistInfoManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.|
 
#### static native int initManager (String strEngineLibName)

Initializes and registers the HLSAES128DescrambleManager.

**Parameters**

| Name  | Description  | 
|---|---|
| strEngineLibName | The relevant engine library name as a string.| 
 
### HLSTsDRMManager Class Reference

This class allows NexPlayer to handle and descramble HLS TS encrypted content.

#### static native int initDRMManager (String strEngineLibName)

Initializes and registers the `HLSTsDRMManager`.

**Parameters**

| Name  | Description                                                                |
|-------|----------------|
| strEngineLibName | The relevant engine library name as a string. |

### HTTPRetrieveDataManager Class Reference

This class allows NexPlayer to support and handle offline HLS and Smooth Streaming content.
 
#### static native int initManager (String strEngineLibName, String cachFolder)

Initializes and registers the `HTTPRetrieveDataManager`.

**Parameters**

| Name  | Description                                                                |
|-------|----------------|
| strEngineLibName | The relevant engine library name as a string. |
| cachFolder | The folder to be used for the cache, as a string. |


### HTTPStoreDataManager Class Reference

#### static native int initManager (String strEngineLibName, String cachFolder)

Initializes and registers the HTTPStoreDataManager.

**Parameters**

| Name  | Description                                                                |
|-------|----------------|
| cData | The caption data for the received line of text, as an array of characters. |
| cachFolder     | The folder to be used for the cache, as a string.|

### NexHLSAES128DRMManager.IAESCallbackListener Interface Reference

An interface for GetKeyExternal and IsSupportKey Callbacks.

This must be implemented by the application.


#### byte[] getKeyFromExternal (String strKeyUrl)

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

If the DRM supports that key attribute, then it should return TRUE. Then, NexPlayer will call DRM callbacks depending on the encryption method. If the DRM does not support the key, then it should return FALSE.
In this case, NexPlayer will not call the "getKeyFromExternal" callbacks and it will decrypt using its internal decryption function.
  
### NexPlayer.IDynamicThumbnailListener Interface Reference

This interface must be implemented in order for the application to receive Dynamic Thumbnail events from NexPlayer.

NexPlayer will call the methods provided in this interface automatically during playback to notify the application when various Dynamic Thumbnail events have occurred.

In most cases, the handling of these events is optional; NexPlayer will continue play content back normally without the application doing anything special in response to the events received.

#### void onDynamicThumbnailData (NexPlayer mp, int width, int height, int cts, Object bitmap)

This method will be called by the NexPlayer engine when thumbnail data is created.

If the `enableDynamicThumbnail()` method is called before Smooth Streaming content is in the open state, then this method will be called and gets the thumbnail information associated with the content.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object generating the event.|
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
| mp | The NexPlayer object generating the event.|
 
> Implemented in NexEventReceiver.

### NexPlayer.IListener Interface Reference

The application must implement this interface in order to receive events from NexPlayer.

> **CAUTION:** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from with in IListener callbacks. The safest way to update the UI is to use `android.os.Handler` to post an event back to the main application thread.

NexPlayer will call the methods provided in this interface automatically during playback to notify the application when various events have occurred.

In most cases, the handling of these events is optional; NexPlayer will continue playback normally without the application doing anything special. There are a few exceptions to this which are listed below.

There are two categories of notifications. First of all, for any asynchronous command issued to NexPlayer (via the appropriate method call), a callback will occur when that command has completed to notify the application of the success or failure of the operation.

The other category of notifications are notifications that occur during playback to notify the application of changes in the state of NexPlayer. For example, if NexPlayer begins buffering data during streaming playback, an event occurs to allow the application to display an appropriate message, if necessary.

For asynchronous commands, the application will generally want to take action in the following cases (some applications may need to handle these differently depending on their requirements; these are correct for most cases):

- When any command fails, display an error to the user.
- When an open command succeeds, issue a start command to begin actual playback.
- When a stop command succeeds, issue a close command to close the file.

This is because commands such as open and stop take some time to execute, and follow-up commands such as
start and close can not be called immediately, but must wait until the first command has completed.

> **Warning** However, do not call close in these event handlers as this may give rise to a deadlock. A safe way to call `close` is to use the Android UI main thread’s message handler.

> See each individual `IListener` method for a recommendation on how to implement that method in your application.


#### void onAsyncCmdComplete (NexPlayer mp, int command, int result, int param1, int param2)

When an asynchronous method of NexPlayer has completed successfully or failed, this event occurs.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object generating the event.|
| command | The command which completed. This may be any of the following **Values:**|
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

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
| samplingRate | The sample rate (in Hz) of the content to be played back.| 
| channelNum | The number of channels in the content (1=mono, 2=stereo).| 
 
> Implemented in NexEventReceiver.

#### void onAudioRenderDelete(NexPlayer mp)

Notification that the audio rendering thread has been destroyed.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
  
> Implemented in NexEventReceiver.

#### void onAudioRenderPrepared (NexPlayer mp)

This method is called when NexPlayer recognizes which audio render will be used.

Because NexPlayer supports only a SW audio render, this method will not be used.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
  
> Implemented in NexEventReceiver.

#### void onBuffering (NexPlayer mp, int progress\_in\_percent)

This reports the current buffering status.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
| progress\_in\_percent | The current buffering percentage.| 
   
> Implemented in NexEventReceiver.

#### void onBufferingBegin (NexPlayer mp)

Reports the start of buffering.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
 
> Implemented in NexEventReceiver.

#### void onBufferingEnd (NexPlayer mp)

This reports the end of buffering.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
 
> Implemented in NexEventReceiver.

#### void onDataInactivityTimeOut (NexPlayer mp)

Reports Data Inactivity Timeout.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
 
> Implemented in NexEventReceiver.

#### void onDateRangeData (NexPlayer mp, NexDateRangeData[] data)

This method reports the data Range value that is contained in the EXT-X-DATERANGE tag.

**Parameters**

 
| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
| data | The array of NexDateRangeData object that includes data Range and data contained in the EXT-X-DATERANGE tag.| 
 
> Implemented in NexEventReceiver.
 
#### void onDownloaderAsyncCmdComplete (NexPlayer mp, int msg, int param1, int param2)

This function is called when an asynchronous command in the Downloader module is complete.

This method will be called whenever DownloaderOpen(), DownloaderClose(), DownloaderStart() or DownloaderStop() finish asynchronously.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
| data | The asynchronous command completed. This will be one of:<br>- NEXDOWNLOADER\_ASYNC\_CMD\_OPEN = 0x00200001<br>- NEXDOWNLOADER\_ASYNC\_CMD\_CLOSE = 0x00200002<br>- NEXDOWNLOADER\_ASYNC\_CMD\_START = 0x00200003<br>- NEXDOWNLOADER\_ASYNC\_CMD\_STOP = 0x00200004|
| param1 | This integer indicates the result of the command. It will be 0 in the event of success, or will be an error code in the event of failure.| 
| param2 | Additional information, if available, concerning the result reported in param1. For example if the error is invalid response, param2 gives the HTTP status code.|  
 
> Implemented in NexEventReceiver.

#### void onDownloaderError (NexPlayer mp, int msg, int param1)

This function is called when an error is generated by the Downloader module.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
| msg | An integer indicating the error generated by the Downloader module.| 
| param1 | This parameter is currently undefined but reserved for future use and should not be used.| 
  
> Implemented in NexEventReceiver.

#### void onDownloaderEventBegin (NexPlayer mp, int param1, int param2)

This method reports when a Downloader event has started.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
| param1 | This parameter is currently undefined and is not used but is reserved for future use.| 
| param2 | The total size of the content file to be downloaded.| 
 
> Implemented in NexEventReceiver.

#### void onDownloaderEventComplete (NexPlayer mp, int param1)

This function is called when a Downloader event has completed.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
| param1 | This parameter is currently undefined and is not used but is reserved for future use.| 

> Implemented in NexEventReceiver.

#### void onDownloaderEventProgress (NexPlayer mp,int param1,int param2,long param3,long param4)

This function is called to pass the downloading progress of a Downloader event.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
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
| mp | The NexPlayer object to which this event applies.| 
| param1 | This parameter is currently undefined and is not used but is reserved for future use.| 
| param2 | This is an integer that indicates the current state of the Downloader event. This will be one of:<br>- **NEXDOWNLOADER\_STATE\_NONE = 0**<br>- **NEXDOWNLOADER\_STATE\_CLOSED = 2**<br>- **NEXDOWNLOADER\_STATE\_STOP = 3**<br>- **NEXDOWNLOADER\_STATE\_DOWNLOAD = 4**|

> Implemented in NexEventReceiver.

#### void onEndOfContent (NexPlayer mp)

This method indicates when playback has completed successfully up to the end of the content.

This event occurs when the player reaches the end of the file or stream. In most cases, applications should respond to this by calling NexPlayer.stop and then updating the user interface.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.| 
 
> Implemented in NexEventReceiver.

#### void onError (NexPlayer mp, NexErrorCode errorcode)

An error has occurred during playback.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object generating the event.|  
| errorcode | The error code for the generated error.|  

> Implemented in NexEventReceiver.

#### void onHTTPRequest (NexPlayer mp, String strRequest)

This method allows NexPlayer to pass HTTP request messages to an application.

While NexPlayer normally handles HTTP requests and responses internally, in cases where additional information is required from the server (for example user cookies), this method can be used in conjunction with `onHTTPResponse` to allow an application to handle that information directly.

> **Note** This should be called before a request is sent to an HTTP server. To modify an HTTP request, see `onModifyHttpRequest`. To handle the response received, call `onHTTPResponse`.
 
**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.|  
| strRequest | The HTTP request to be sent to the server, as a string.|   
 
 The HTTP request to be sent to the server, as a string.
 
**See Also**
 
- NexPlayer.onHTTPResponse
- NexPlayer.onModifyHttpResponse
 
> Implemented in NexEventReceiver.


#### void onHTTPResponse (NexPlayer mp, String strResponse)

This method allows responses from an HTTP server to be received and handled in a more customized way.

While NexPlayer normally handles HTTP requests and responses internally, in cases where additional information is required from the server (for example user cookies), this method can be used in conjunction with onHTTPRequest to handle that information directly.

> **Note** This should be called after a response has been received from the server. To change the requests being made, onModifyHttpRequest should be called.
 
**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.|  
| strResponse | The response from the HTTP server, as a string.|   
 
**See Also**

- NexPlayer.onHTTPRequest
- NexPlayer.onModifyHttpRequest
 
Implemented in NexEventReceiver.

#### String onModifyHttpRequest (NexPlayer mp, int param1, Object input\_obj)

This method provides the HTTP Request that will be used by NexPlayer when an HTTP request is modified.

**Parameters**
 
| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.|  
| param1 | The length of the current HTTP Request data.|  
| input\_obj | The modified HTTP Request data.|   
 
**Returns**
 
A String with the modified HTTP request. This value will be used by NexPlayer instead of the previous HTTP
request.
 
**See Also**

Enabling Modified HTTP Requests for more information.
 
> Implemented in NexEventReceiver.

#### void onPauseSupervisionTimeOut (NexPlayer mp)

Reports Pause Supervision Timeout.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.|  

> Implemented in NexEventReceiver.

#### void onPictureTimingInfo (NexPlayer mp, NexPictureTimingInfo[] arrPictureTimingInfo)

This method provides SEI picture timing information about video frames of H.264 content when available.

This method is called when `ENABLE_H264_SEI` is enabled and the H.264 content contains supplemental en-
hancement information (SEI). While SEI may include a variety of attributes, this method specifically receives SEI picture timing information when available.

NexPlayer delivers the timing information through this method by passing an instance of NexPictureTimingInfo whenever SEI picture timing information is received.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.|  
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
| mp | The NexPlayer object generating the event.|
|strTag | The most recent #EXT-X-PROGRAM-DATE-TIME tag in the HLS content, as a string.|
|offset|The time offset of the currently decoding frame’s timestamp with respect to the #EXT-X-PROGRAM-DATE-TIME tag time, in milliseconds.|
 
**See Also**
 
getProgramTime


> Implemented in NexEventReceiver.

#### void onRTSPCommandTimeOut (NexPlayer mp)

Reports RTSP command Timeout.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object generating the event.|  

> Implemented in NexEventReceiver.

#### void onSessionData (NexPlayer mp, NexSessionData[] data)

This method reports the arbitrary session data of the HLS master playlist.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.|  
| data | The array of NexSessionData object that includes the arbitrary session data of the HLS master playlist.|  
 
> Implemented in NexEventReceiver.

#### void onSignalStatusChanged (NexPlayer mp, int pre, int now)

NexPlayer’s signal status has been changed.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object generating the event.|  
| pre | The previous signal status.| 
| now | The current signal status.| 
 
> Implemented in NexEventReceiver.


#### void onStateChanged ( NexPlayer mp, int pre, int now )

NexPlayer’s state has been changed.

This method is called when NexPlayer’s state has been changed but it does not mean that the changing operation has completed. Therefore, the next operation can be carried out only after the event onAsyncCmdComplete is received, not when this event, onStateChanged, is called.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object generating the event.|
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
| mp | The NexPlayer object to which this event applies.|
| param1 | Additional information. The meaning of this depends on the value of msg. If the description above doesn’t refer to param1, then this parameter is undefined for that value of msg and should not be used.|
| msg | The type of notification. This is one of the following **Values:**| 

- `NEXPLAYER_STATUS_REPORT_NONE (0x00000000)` 
No status change (thisvalue is not normally passed to onStatusReport, and should generally be ignored).

- `NEXPLAYER_STATUS_REPORT_AUDIO_GET_CODEC_FAILED (0x00000001)` 
Failed to determine the audio codec. This notification can happen at the beginningof playback, or during playback if there is an audio codec change. This can happenbecause of a switch to a new codec that NexPlayer does not support, or due to anerror in the format of the content or corrupted data in the content.

- `NEXPLAYER_STATUS_REPORT_VIDEO_GET_CODEC_FAILED (0x00000002)` 
Failed to determine the video codec. This notification can happen at the beginningof playback, or during playback if there is a video codec change. This can happenbecause of a switch to a new codec that NexPlayer does not support, or due to anerror in the format of the content or corrupted data in the content.

- `NEXPLAYER_STATUS_REPORT_AUDIO_INIT_FAILED (0x00000003)` 
 The audiocodec failed to initialize. This can happen for several reasons. The container mayindicate the wrong audio codec, or the audio stream may be incorrect or corrupted,or the audio stream may use a codec version or features that NexPlayer doesn’tsupport.

- `NEXPLAYER_STATUS_REPORT_VIDEO_INIT_FAILED (0x00000004)` 
 The videocodec failed to initialize. This can happen for several reasons. The container mayindicate the wrong video codec, or the video stream may be incorrect or corrupted,or the video stream may use a codec version or features that NexPlayer doesn’tsupport.

- `NEXPLAYER_STATUS_REPORT_TRACK_CHANGED (0x00000005)` 
 The track haschanged. This happens for protocols such as HLS that provide the content in multipleformats or at multiple resolutions or bitrates. The ID of the new track can be found in mCurrTrackID, and also in param1. When this event occurs, NexPlayer also generates a NEXPLAYER\_CONTENT\_INFO\_UPDATED event.

- `NEXPLAYER_STATUS_REPORT_STREAM_CHANGED (0x00000006)` 
 The streambeing played back has changed (between the states AudioOnly, VideoOnly and Audio+Video). The new stream type is in mMediaType, and also in param1.

- `NEXPLAYER_STATUS_REPORT_DSI_CHANGED (0x00000007)` 
 An attribute relating to the video or audio format (such as the resolution, bitrate, etc.)` 
 has changed. This is considered Decoder Specific Information (DSI).

- `NEXPLAYER_STATUS_REPORT_OBJECT_CHANGED (0x00000008)` 
 One of thecodec objects in use has changed (that is, the audio or video codec in use haschanged). See mAudioCodec and mVideoCodec to get the ID of the new codec.

- `NEXPLAYER_STATUS_REPORT_CONTENT_INFO_UPDATED (0x00000009)` 
 The content information has changed. When onStatusReport is called with any other non Failure value for msg, it will also be called with this as well. This is a good place to monitor insignificant changes to the content information.

- `NEXPLAYER_STATUS_REPORT_DOWNLOAD_PROGRESS (0x00000080)` 
 Reports the progress made storing content for offline play. This message will be calledwhen content is opened with NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAM type.For this notification, the parameter param1 returns the percentage of downloading completed (0-100).

- `NEXPLAYER_STATUS_REPORT_AVMODE_CHANGED (0x0000000A)` 
 Thestream being played back has changed and the new stream has a different mediatype. This event happens whenever the state changes between video-only, audio-only and audio-video. param1 contains the new media - Type: 1 for audio, 2 for video, 3 for both.

- `NEXPLAYER_STATUS_REPORT_HTTP_INVALID_RESPONSE (0x0000000B)` 
 An HTTP error response was received from the server.param1 contains the error code(this is a normal HTTP response code, such as 404, 500, etc.)

- `NEXPLAYER_STATUS_REPORT_DISCONTINUITY_EXIST (0x00000012)` 
 There is a discontinuity tag found in the HLS content playlist.

- `NEXPLAYER_STATUS_REPORT_EXTERNAL_DOWNLOAD_CANCELED(0x00000020)` 
 The player canceled External PD Mode and played content onNormal PD Mode. (e.g. The engine attempted to play regular content instead of piffcontent on External PD Mode).

- `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED(0x00000021)` 
 Either the Minimum bandwidth or Maximum bandwidth has beenchanged.

- `NEXPLAYER_STATUS_REPORT_STREAM_RECV_PAUSE (0x00000060)` 
 Whenthe prefetch buffer exceeds the maximum value, the player pauses the buffer control.The user can adjust the maximum value of the prefetch buffer by using setProperty ofthe properties MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION.

- `NEXPLAYER_STATUS_REPORT_STREAM_RECV_RESUME (0x00000061)` 
 Whenthe prefetch buffer is below the minimum value, the player resumes the buffer control. The user can adjust the mimimum value of the prefetch buffer by using setProperty ofthe properties MIN\_BUFFER\_RATE or MIN\_BUFFER\_DURATION.

- `NEXPLAYER_STATUS_REPORT_DOWNLOAD_PROGRESS (0x00000080)` 
 Reports the progress made storing content for offline play. This message will be calledwhen content is opened with NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAM type.For this notification, the parameter param1 returns the percentage of downloadingcomplete (0-100).

- `NEXPLAYER_STATUS_REPORT_MAX (0xFFFFFFFF)` 
 This value is reserved; do not use it.

> Implemented in NexEventReceiver. 
 

#### void onTime ( NexPlayer mp, int millisec )

This method indicates that playback has progressed to the specified position.

This event occurs once per second. If the application is displaying the current play position, it should update it to reflect this new value.

Applications that wish to update the play time more often that once per second or with a greater accuracy may ignore this event and create their own timer, in which case they can use the current play time reported in NexContentInformation.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object generating the event.|
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
| mp | The NexPlayer object to which this event applies.|
| TimedMeta | An NexID3TagInformation object that contains the timed metadata associated with the content to be displayed.|
 
> Implemented in NexEventReceiver.
 
 
### INexDRMLicenseListener Interface Reference

The application must implement this interface in order to receive events from NexPlayer.

#### byte[] onLicenseRequest ( byte[ ]requestData)**

This method provides the license request data that will be used by DRM Client.

**Parameters**
 
| Name        | Description                              |
|-------------|----------------------|
| requestData | requestData is the license request data. |
 
**Returns**

 
A *Object* with license response data. DRM Client will use this *string* without any modification. If modification is not needed, then the UI should return null.
 
 
### NexPlayer.IReleaseListener Interface Reference

This interface can be implemented in an application in order to receive NexPlayer release events from NexPlayer.

In most cases, the handling of these events is optional; NexPlayer will continue playback normally without the application doing anything special in response to the events received.

 
  
#### static native int initManager (String strEngineLibName) *[static]*

Initializes and registers the `MPDDescrambleManager`.

**Parameters**
 
| Name             | Description                                   |
|------------------|---------------------------|
| strEngineLibName | The relevant engine library name as a string. |

### NexNetAddrTable.NetAddrTableInfo Class Reference

This class defines the information possible for an entry made with the method *8addEntry*, including the hostname and its corresponding IP address when a customized IP address is desired.
 
### Nex3DAudioSolution01 Class Reference

This class allows NexPlayer to handle audio and convert to 3D audio.

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
 
 
### NexALFactory Class Reference

The primary interface to the `NexALFactory`.

`NexALFactory` handles codecs and renderer selection for the NexPlayer SDK. To use the NexPlayer SDK, the application must create an instance of the `NexALFactory` class (supplied as part of the NexPlayer SDK).

In addition, an application must also do the following:

1. Create an instance of NexPlayer  and an instance of `NexALFactory` and set the codec usage policy.

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
 
3. After playback by NexPlayer, `NexALFactory.release` should be called when instances of NexPlayer and
    `NexALFactory` are no longer needed.

 	```java
		mNexPlayer.release();
		mNexALFactory.release();
	```
 
**Classes**

- `interface ICodecDownListener`
- `enum NexALFactoryErrorCode`
   
    Possible error codes that can be returned by NexPlayer’s *NexALFactory*.

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
inform NexPlayer of the newly available codecs.

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

This method is called by the NexPlayer Engine. This is just for native methods. Don’t use this method for other purposes.

#### boolean init (Context context, String strModel, String strRenderMode, int logLevel, int colorDepth)

Initializes `NexALFactory`.

NexPlayer automatically detects the devices where HW codecs and H.264 Main/High profiles can be supported so there is no need to indicate any specific device model to the player.

> **Warning** Although it is possible to change the device model parameter, *strModel*, it is not recommended because changing the model name may result in the H/W decoder not working properly. Please do NOT change the device model name in the sample code. Similarly, although it is possible to change the render mode parameter, *strRenderMode*, NexPlayer is only guaranteed to work properly with *strRenderMode* set to *NEX\_DEVICE\_USE\_AUTO*. Please do NOT change the render mode in the sample code.

**Parameters**

 
| Name          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|---------------|------------------------|
| context       | The current context; from *Activity* subclasses, you can just pass *this*.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| srtModel      | Device model name. NexPlayer includes multiple renderer modules, and past versions of the player selected the module most suitable to the device based on this value. The renderer is now set by the parameter *strRenderMode*. Under normal use, you should pass the MODEL as available via the Android API in *android.os.Build.MODEL*. For example:  	*nexALFactory.init(this, android.os.Build.MODEL, 	NEX\_DEVICE\_USE\_AUTO, 0, 1);*     NexPlayer uses this to select the most appropriate renderer if no renderer is selected (*NULL* is passed) with the parameter *strRenderMode* below. For OS versions up to Gingerbread, this is always the Android Renderer (although from Froyo, other renderers are supported as well) if the SW codec is in use. For Honeycomb and Ice Cream Sandwich (ICS), this is always the OpenGL renderer when the SW codec is in use.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| srtRenderMode | The Renderer to use, as a string. The recommended render mode to use is *NEX\_DEVICE\_USE\_AUTO*, which will choose the most appropriate render mode automatically. |
| logLevel      | NexPlayer SDK logging level. This affects the messages that the SDK writes to the Android log.   - **-1** : Do not output any log messages. - **0** : Output basic log messages only (recommended). - **1** ∼ **4** : Output detailed log messages; higher numbers result in more verbose log entries, but may cause performance issues in some cases and are not recommended for general release code.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
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

This method rescans the codec files in the application files directory(*/data/data/<package\_name>/files*) to update the codecs available in NexPlayer.

> **Warning** This must be called after `NexALFactory.init` has been called.
 
Any time an application downloads an additional codec by calling `NexALFactory.downloadCodec`, this method
should be called to inform NexPlayer of the newly available codecs.

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
  
 
### NexALFactory.NexALFactoryErrorCode Enum Reference

Possible error codes that can be returned by NexPlayer’s *NexALFactory*.

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


#### static NexALFactoryErrorCode fromIntegerValue (int code)

This method gets the error code of a given *NexALFactoryError*, from a given integer value.

#### String getDesc ( )

This method gets the description of a given *NexALFactoryError*, given an error constant.

#### int getIntegerCode ( )

This method gets the integer code for a given *NexALFactoryError*.

### NexContentInformation Class Reference

Stores and provides information about an individual codec used by the NexPlayer engine.

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

Possible **Values:**

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

Possible **Values:**

- 1 : Audio codec
- 2 : Video codec

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

### NexEventReceiver Class Reference

This class implements all NexPlayer interfaces.

An instance of *NexEventReceiver* can be used for parameter of NexPlayer.addEventRecevier, `NexPlayer.removeEventReceiver`


#### void onAsyncCmdComplete (NexPlayer mp,int command,int result,int param1,int param2)**

When an asynchronous method of NexPlayer has completed successfully or failed, this event occurs.

**Parameters**

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th>mp</th>
  <td>The NexPlayer object generating the event.</td>
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

- NEXPLAYER\_ASYNC\_CMD\_OPEN\_LOCAL

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- SOURCE\_OPEN\_TIMEOUT
	- NOT_SUPPORT\_AUDIO\_CODEC
	- NOT_SUPPORT\_VIDEO\_CODEC
	- NOT_SUPPORT\_MEDIA
	- FILE_INVALID\_SYNTAX
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD_OPEN\_STREAMING

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- SOURCE\_OPEN\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO_CODEC
	- NOT\_SUPPORT\_VIDEO_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD\_START\_LOCAL

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- DATA\_INACTIVITY\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO_CODEC
	- NOT\_SUPPORT\_VIDEO_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- CODEC\_DECODING\_ERROR
	- NOT\_SUPPORT\_VIDEO\_RESOLUTION
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD\_START\_STREAMING

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- DATA\_INACTIVITY\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- CODEC\_DECODING\_ERROR
	- NOT\_SUPPORT\_VIDEO\_RESOLUTION
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD\_STOP

	- NOT\_SUPPORT\_MEDIA
	- ERROR_NETWORK\_PROTOCOL
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD\_PAUSE

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- ERROR\_NETWORK\_PROTOCOL
	- UNKNOWN


- NEXPLAYER_ASYNC_CMD_RESUME

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- UNKNOWN

- NEXPLAYER_ASYNC_CMD_SEEK

	- INVALID\_STATE
	- NOT\_SUPPORT\_TO\_SEEK
	- DATA\_INACTIVITY\_TIMEOUT
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- CODEC\_DECODING_ERROR
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD\_SETEXTSUBTITLE

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD\_REINITVIDEO

	- INVALID_STATE
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- FILE\_INVALID\_SYNTAX
	- ERROR\_NETWORK\_PROTOCOL
	- CODEC\_DECODING\_ERROR
	- NOT\_SUPPORT\_TO\_SEEK
	- DATA\_INACTIVITY\_TIMEOUT
	- UNKNOWN

- NEXPLAYER\_ASYNC\_CMD\_FASTPLAY\_START

	- INVALID\_STATE
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD\_FASTPLAY\_STOP

	- NOT\_SUPPORT\_AUDIO\_CODEC
	- CODEC\_DECODING\_ERROR


- NEXPLAYER_ASYNC_CMD_SET_MEDIA_STREAM

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- UNKNOWN


- NEXPLAYER_ASYNC\_CMD\_OPEN\_STORE\_STREAM

	- INVALID\_PARAMETER
	- SOURCE\_OPEN\_TIMEOUT
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- ERROR\_NETWORK\_PROTOCOL
	- NOT\_SUPPORT\_MEDIA
	- FILE\_INVALID\_SYNTAX
	- UNKNOWN


- NEXPLAYER\_ASYNC\_CMD\_START\_STORE\_STREAM

	- INVALID\_STATE
	- INVALID\_PARAMETER
	- NOT\_SUPPORT\_AUDIO\_CODEC
	- NOT\_SUPPORT\_VIDEO\_CODEC
	- NOT\_SUPPORT\_MEDIA
	- ERROR\_NETWORK\_PROTOCOL
	- FILE\_INVALID\_SYNTAX
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

**Parameters**

| Name         | Description                                               |
|--------------|-------------------|
| mp           | The NexPlayer object to which this event applies.      |
| samplingRate | The sample rate (in Hz) of the content to be played back. |
| channelNum   | The number of channels in the content (1=mono, 2=stereo). |

Implements `NexPlayer.IListener`.

#### void onAudioRenderDelete (NexPlayer mp)

Notification that the audio rendering thread has been destroyed.


**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The NexPlayer object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onAudioRenderPrepared (NexPlayer mp)

This method is called when NexPlayer recognizes which audio render will be used.

Because NexPlayer supports only a SW audio render, this method will not be used.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The NexPlayer object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onBuffering (NexPlayer mp,int progress_in_percent)

This reports the current buffering status.

**Parameters**

| Name                | Description                                          |
|---------------------|--------------|
| mp                  | The NexPlayer object to which this event applies. |
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
| mp   | The NexPlayer object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onDataInactivityTimeOut (NexPlayer mp)

Reports Data Inactivity Timeout.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The NexPlayer object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onDateRangeData (NexPlayer mp, NexDateRangeData[ ] data)

This method reports the dataRange value that is contained in the EXT-X-DATERANGE tag.

**Parameters**

| Name | Description                                                                                                  |
|------|------|
| mp   | The NexPlayer object to which this event applies.                                                         |
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
| mp     | The NexPlayer object to which this event applies.                                      |
| msg    | An integer indicating the error generated by the Downloader module.                       |
| param1 | This parameter is currently undefined but reserved for future use and should not be used. |

Implements `NexPlayer.IListener`.

#### void onDownloaderEventBegin (NexPlayer mp, int param1, int param2)

This method reports when a Downloader event has started.

**Parameters**

| Name   | Description                                                                           |
|--------|---------------------------|
| mp     | The NexPlayer object to which this event applies.                                  |
| param1 | This parameter is currently undefined and is not used but is reserved for future use. |
| param2 | The total size of the content file to be downloaded.                                  |

Implements `NexPlayer.IListener`.

#### void onDownloaderEventComplete (NexPlayer mp, int param1)

This function is called when a Downloader event has completed.

**Parameters**

| Name   | Description                                                                           |
|--------|---------------------------|
| mp     | The NexPlayer object to which this event applies.                                  |
| param1 | This parameter is currently undefined and is not used but is reserved for future use. |

Implements `NexPlayer.IListener`.

#### void onDownloaderEventProgress (NexPlayer mp, int param1, int param2, long param3, long param4)

This function is called to pass the downloading progress of a Downloader event.

**Parameters**

| Name   | Description                                                                                  |
|--------|----------------------------------|
| mp     | The NexPlayer object to which this event applies.                                         |
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
  <td>The NexPlayer object to which this event applies.</td>
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

This method will be called by the NexPlayer engine when thumbnail data is created.

If the *enableDynamicThumbnail()* method is called before Smooth Streaming content is in the *open* state,
then this method will be called and gets the thumbnail information associated with the content.

**Parameters**


| Name   | Description                                        |
|--------|------------|
| mp     | The NexPlayer object generating the event.      |
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
| mp     | The NexPlayer object generating the event.      |

Implements `NexPlayer.IDynamicThumbnailListener`.

#### void onEndOfContent (NexPlayer mp)

This method indicates when playback has completed successfully up to the end of the content.

This event occurs when the player reaches the end of the file or stream. In most cases, applications should respond to this by calling `NexPlayer.stop` and then updating the user interface.


**Parameters**

| Name   | Description                                        |
|--------|------------|
| mp     | The NexPlayer object generating the event.      |

Implements `NexPlayer.IListener`.

#### void onError (NexPlayer mp, NexErrorCode errorcode)

An error has occurred during playback.

**Parameters**

| Name      | Description                                   |
|-----------|---------------------------|
| mp        | The NexPlayer object generating the event. |
| errorcode | The error code for the generated error.       |

Implements `NexPlayer.IListener`.

#### int onHTTPABRTrackChange (NexPlayer mp, int param1, int param2, int param3)

This method will be called by the NexPlayer engine when the ABR track is switched.

**Parameters**

| Name   | Description                                   |
|--------|---------------------------|
| mp     | The NexPlayer object generating the event. |
| param1 | The current network bandwidth.                |
| param2 | The current track bandwidth.                  |
| param3 | The target track bandwidth.                   |

**Returns**


The exact track bandwidth that the user wants to set to forcibly.

Implements `NexPlayer.IHTTPABRTrackChangeListener`.


#### void onHTTPRequest (NexPlayer mp, String strRequest)

This method allows NexPlayer to pass HTTP request messages to an application.

While NexPlayer normally handles HTTP requests and responses internally, in cases where additional information is required from the server (for example user cookies), this method can be used in conjunction with *onHTTPResponse* to allow an application to handle that information directly.

>**Note** This should be called before a request is sent to an HTTP server. To modify an HTTP request, see *onModifyHttpRequest*. To handle the response received, call *onHTTPResponse*.

**Parameters**

| Name       | Description                                               |
|------------|-------------------|
| mp         | The NexPlayer object to which this event applies.      |
| strRequest | The HTTP request to be sent to the server, as a *String*. |

**See Also**

- `NexPlayer.onHTTPResponse`
- `NexPlayer.onModifyHttpResponse`

Implements `NexPlayer.IListener`.

#### void onHTTPResponse (NexPlayer mp, String strResponse)

This method allows responses from an HTTP server to be received and handled in a more customized way.

While NexPlayer normally handles HTTP requests and responses internally, in cases where additional information is required from the server (for example user cookies), this method can be used in conjunction with *onHTTPRequest* to handle that information directly.

>**Note** This should be called after a response has been received from the server. To change the requests being made,on *ModifyHttpRequest* should be called.


**Parameters**

| Name        | Description                                          |
|-------------|--------------|
| mp          | The NexPlayer object to which this event applies. |
| strResponse | The response from the HTTP server, as a *String*.    |

**See Also**


- `NexPlayer.onHTTPRequest`
- `NexPlayer.onModifyHttpRequest`

Implements `NexPlayer.IListener`.

#### String onModifyHttpRequest (NexPlayer mp, int param1, Object input_obj)

This method provides the HTTP Request that will be used by NexPlayer when an HTTP request is modified.

**Parameters**

| Name      | Description                                          |
|-----------|--------------|
| mp        | The NexPlayer object to which this event applies. |
| param1    | The length of the current HTTP Request data.         |
| input_obj | The modified HTTP Request data.                      |


**Returns**

A String with the modified HTTP request. This value will be used by NexPlayer instead of the previous HTTP
request.

**See Also**


- Enabling Modified HTTP Requests for more information.

Implements `NexPlayer.IListener`.

#### void onOfflineKeyExpiredListener (NexPlayer mp)

This method will be called by the NexPlayer engine when the keyId of media DRM should be expired.


**Parameters**

| Name | Description                                   |
|------|---------------------------|
| mp   | The NexPlayer object generating the event. |

**Returns**


the key ID of media drm stored with onOfflineKeyStoreListener.

Implements `NexPlayer.IOfflineKeyListener`.

#### byte[] onOfflineKeyRetrieveListener (NexPlayer mp)

This method will be called by the NexPlayer engine when the keyId of media DRM should be retrieved.

**Parameters**

| Name | Description                                   |
|------|---------------------------|
| mp   | The NexPlayer object generating the event. |

**Returns**


the key ID of media drm stored with onOfflineKeyStoreListener.

Implements `NexPlayer.IOfflineKeyListener`.

#### void onOfflineKeyStoreListener (NexPlayer mp,byte[ ]keyId)

This method will be called by the NexPlayer engine when the keyId of media DRM should be stored.

**Parameters**


| Name  | Description                                   |
|-------|---------------------------|
| mp    | The NexPlayer object generating the event. |
| keyId | The Key ID of Media drm for offline playback. |


Implements `NexPlayer.IOfflineKeyListener`.

#### void onPauseSupervisionTimeOut (NexPlayer mp)

Reports Pause Supervision Timeout.

**Parameters**

| Name | Description                                   |
|------|---------------------------|
| mp   | The NexPlayer object generating the event. |

Implements `NexPlayer.IListener`.

#### void onPictureTimingInfo (NexPlayer mp, NexPictureTimingInfo[ ] arrPictureTimingInfo)**

This method provides SEI picture timing information about video frames of H.264 content when available.

This method is called when *ENABLE_H264_SEI* is enabled and the H.264 content contains supplemental enhancement information (SEI). While SEI may include a variety of attributes, this method specifically receives SEI
picture timing information when available.

NexPlayer delivers the timing information through this method by passing an instance of `NexPictureTimingInfo`
whenever SEI picture timing information is received.

**Parameters**


| Name                 | Description                                                                                         |
|----------------------|---------------------|
| mp                   | The NexPlayer object to which this event applies.                                                |
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
| mp     | The NexPlayer object generating the event.                                                                                         |
| strTag | The most recent #EXT-X-PROGRAM-DATE-TIME tag in the HLS content, as a *String*.                                                       |
| offset | The time offset of the currently decoding frame’s timestamp with respect to the #EXT-X-PR- OGRAM-DATE-TIME tag time, in milliseconds. |


#### void onRTSPCommandTimeOut (NexPlayer mp)

Reports RTSP command Timeout.

**Parameters**

| Name | Description                                   |
|------|---------------------------|
| mp   | The NexPlayer object to which this event applies. |

Implements `NexPlayer.IListener`.

#### void onSessionData (NexPlayer mp, NexSessionData[ ] data)

This method reports the arbitrary session data of the HLS master playlist.

**Parameters**

| Name | Description                                                                                               |
|------|---------------------------|
| mp   | The NexPlayer object to which this event applies.                                                      |
| data | The array of `NexSessionData` object that includes the arbitrary session data of the HLS master playlist. |

Implements `NexPlayer.IListener`.

#### void onSignalStatusChanged (NexPlayer mp, int pre, int now)

NexPlayer’s signal status has been changed.

**Parameters**

| Name | Description                                          |
|------|--------------|
| mp   | The NexPlayer object to which this event applies. |
| pre  | The previous signal status.                          |
| now  | The current signal status.                           |

Implements `NexPlayer.IListener`.

#### void onStateChanged (NexPlayer mp, int pre, int now)

NexPlayer’s state has been changed.

This method is called when NexPlayer’s state has been changed but it does not mean that the changing operation
has completed. Therefore, the next operation can be carried out only after the event *onAsyncCmdComplete* is
received, not when this event,*onStateChanged*, is called.

**Parameters**

| Name | Description                                  |
|------|--------------------------|
| mp   | The NexPlayer object generating the event |
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
  <td>The NexPlayer object to which this event applies.</td> 
</tr>
<tr>
  <th rowspan="22">msg</th>
</tr>
  <tr><td><b>NEXPLAYER_STATUS_REPORT_NONE (0x00000000)</b>: No status change (this value is not normally passed to *onStatusReport*, and should generally be ignored)</td></tr>
  <tr><td><b>NEXPLAYER_STATUS_REPORT_AUDIO_GET_CODEC_FAILED (0x00000001)</b>: Failed to determine the audio codec. This notification can happen at the beginning of playback, or during playback if there is an audio codec change. This can happen because of a switch to a new codec that NexPlayer does not support, or due to an error in the format of the content or corrupted data in the content.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_VIDEO_GET_CODEC_FAILED (0x00000002)</b>: Failed to determine the video codec. This notification can happen at the beginning of playback, or during playback if there is a video codec change. This can happen because of a switch to a new codec that NexPlayer does not support, or due to an error in the format of the content or corrupted data in the content.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_AUDIO_INIT_FAILED (0x00000003)</b>: The audio codec failed to initialize. This can happen for several reasons. The container may     indicate the wrong audio codec, or the audio stream may be incorrect or corrupted, or the audio stream may use a codec version or features that NexPlayer doesn’t support.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_VIDEO_INIT_FAILED (0x00000004)</b>: The video codec failed to initialize. This can happen for several reasons. The container may     indicate the wrong video codec, or the video stream may be incorrect or corrupted, or the video stream may use a codec version or features that NexPlayer doesn’t support.</td></tr>
	
<tr><td><b>NEXPLAYER_STATUS_REPORT_TRACK_CHANGED (0x00000005)</b>: The track has changed. This happens for protocols such as HLS that provide the content in multiple formats or at multiple resolutions or bitrates. The ID of the new track can be found in mCurrTrackID, and also inparam1. When this event occurs, NexPlayer also enerates a eNEXPLAYER_CONTENT_INFO_UPDATED event.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_STREAM_CHANGED (0x00000006)</b>: The stream being played back has changed (between the states Audio-Only, Video-Only and     Audio+Video). The new stream type is in mMediaType, and also in param1.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_DSI_CHANGED (0x00000007)</b>: An attribute relating to the video or audio format (such as the resolution, bitrate, etc.) has changed. This is considered Decoder Specific Information (DSI).</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_OBJECT_CHANGED (0x00000008)</b>: One of the codec objects in use has changed (that is, the audio or video codec in use has     changed). See mAudioCodec and mVideoCodec to get the ID of the new codec.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_CONTENT_INFO_UPDATED (0x00000009)</b>: The content information has changed. When onStatusReport is called with any other non-Failure value for msg, it will also be called with this as well. This is a good place to monitor insignificant changes to the content information.</td></tr>
	
  <tr><td><b>NEXPLAYER_STATUS_REPORT_DOWNLOAD_PROGRESS (0x00000080)</b>: Reports the progress made storing content for offline play. This message will be called     when content is opened with NEXPLAYER_SOURCE_TYPE_STORE_STREAM type. For this notification, the parameter param1 returns the percentage of downloading     complete (0-100).</td></tr>
	
<tr><td><b>NEXPLAYER_STATUS_REPORT_AVMODE_CHANGED (0x0000000A)</b>: The stream being played back has changed and the new stream has a different media type. This event happens whenever the state changes between video-only, audio-only and audio-video. param1 contains the new media - Type: 1 for audio, 2 for video, 3 for     both.</td></tr>
	
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
| mp        | The NexPlayer object to which this event applies.                                                                                                  |
| numTracks | The number of subtitle tracks available for this media. Note that this may be 0 if there are no subtitles, or this function may not be called at all. |

Implements `NexPlayer.IListener`.

#### void onTextRenderRender (NexPlayer mp, int trackIndex, NexClosedCaption textInfo)

This function is called when new subtitle data is ready for display.

This is called whenever playback reaches a point in time where subtitles on any track need to be displayed or cleared.

The text to display is provided in a *NexClosedCaption* object as a byte array; it is the responsibility of the application to convert this to text with the appropriate encoding. Where possible, the encoding information will be provided in the NexC osedCaption.mEncodingType, but many subtitle file formats do not explicitly specify an encoding, so it may be necessary for the application to guess the encoding or allow the user to select it.

**Parameters**


| Name       | Description                                                          |
|------------|------------------------------|
| mp         | The NexPlayer object to which this event applies.                 |
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
| mp       | The NexPlayer object generating the event |
| millisec | Current play position in milliseconds.       |

Implements `NexPlayer.IListener`.

#### void onTimedMetaRenderRender (NexPlayer mp, NexID3TagInformation TimedMeta)

This method is called when new timed metadata is ready for display in HLS.

Timed metadata includes additional information about the playing content that may be displayed to the user and this information may change at different times throughout the content. Each time new metadata is available for display, this method is called.

**See Also**


- NexID3TagInformation for more details on the available metadata information.


**Parameters**

| Name      | Description                                                                                                    |
|-----------|--------|
| mp        | The NexPlayer object to which this event applies.                                                           |
| TimedMeta | An `NexID3TagInformation` object that contains the timed metadata associated with the content to be displayed. |

Implements `NexPlayer.IListener`.

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

#### void setAESCallbackListener (IAESCallbackListener listener)

This method sets and registers a *IAESCallbackListener* listener.

**Parameters**

| Name     | Description            |
|----------|----|
| listener | `IAESCallbackListener` |

**See Also**


- `NexPlayer.IHTTPABRTrackChangeListener`


#### static void d (String tag, String msg)

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
 
#### final int NETADDR\_TABLE\_FALLBACK = 1

This is a possible table type for the method setNetAddrTable.

When the parameter `nNetAddrTableType` in `NexPlayer.setNetAddrTable` is set to this table type, the method will try to retrieve the host information from the existing host database using the given hostname. If this fails, the method will check the table registered as the parametertableto retrieve the custom IP address corresponding to the given hostname.

In other words, this means that the table of net addresses can be used as a fallback option when the needed host information cannot be retrieved.
 
#### final int NETADDR\_TABLE\_OVERRIDE = 0

This is a possible table type for the methodsetNetAddrTable.

When the parameter nNetAddrTableType in NexPlayer.setNetAddrTableis set to this table type, the method will try to get the host information using the hostname and its corresponding custom IP address, set by the developer, from the table registered as the parameter table. If this fails, the player will try to get the host information from the existing host database.

In other words, this means that the information in the table registered will be used with priority, overriding the information from the existing host database.
 
 
### NexPictureTimingInfo Class Reference

This class allows NexPlayer to handle SEI picture timing information in H.264 content.

In summary, this class passes timing information about each video frame in H.264 content if the content provides SEI picture timing information. NexPlayer passes an instance of this class through the onPictureTimingInfo listener.

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

- **Values:**

- 1 : Indicates that several clock timestamp syntax elements are present and follow immediately.
- 0 : Indicates that the related clock timestamp elements are **present**.
 
#### int mCountDroppedFlag

This is the cnt\_dropped\_flag value in SEI picture timing information in H.264 content.

Based on the counting method set by mCountingType, this value specifies that one or more values of mNFrames should be skipped.
 
#### int mCountingType

This is the counting\_type value in SEI picture timing information in H.264 content.

It indicates the method of dropping values of the n\_framesin SEI picture timing information.

- **Values:**

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

- **Values:**

- 0 : Original picture scan was progressive.
- 1 : Original picture scan was interlaced.
- 2 : Original picture scan is unknown.
- 3 : Reserved.

#### int mDiscontinuityFlag

This is the `discontinuity_flag` value in SEI picture timing information in H.264 content.

Please see the H.264 specifications for details in how to interpret the values here.

- **Values:**

- 0 : Continuous clock timestamps.
- 1 : Discontinuity in clock timestamps.
 
#### int mFullTimestampFlag

This is the `full_timestamp_flag` value in SEI picture timing information in H.264 content.

- **Values:**

- 0 : Indicates that the `n_frames` element is followed only by the `seconds_flag`
- 1 : Indicates that a full timestamp is included and that the `n_frames` element is followed by `seconds_value`, `minutes_value`, and `hours_value`.

 
#### int mHours

This is the `hours_value` in SEI picture timing information in H.264 content.

- **Values:** 0 to 23 (inclusive)
 
#### int mMinutes

This is the `minutes_value` in SEI picture timing information in H.264 content.

- **Values:** 0 to 59 (inclusive)

#### int mNFrames

This is the `n_frames` value in SEI picture timing information in H.264 content.

It is used to determine the clock timestamp and is a frame-based counter.

#### int mNuitFieldBasedFlag

This is the `nuit_field_based_flag` in SEI picture timing information in H.264 content.

This value can be used to calculate the clock timestamp of H.264 video frames.
 
#### int mSeconds

This is the `seconds_value` in SEI picture timing information in H.264 content.

- **Values:** 0 to 59 (inclusive)

#### int mTimeOffset

This is the `time_offset` value in SEI picture timing information in H.264 content.

It can be used to determine the clock timestamp.

### NexPlayer Class Reference

The primary interface to the NexPlayer engine.

For details on usage, see the NexPlayer Engine package documentation.

**Classes**

- `interface IDynamicThumbnailListener`

    This interface must be implemented in order for the application to receive Dynamic Thumbnail events from NexPlayer.

- `interface IHTTPABRTrackChangeListener`

    This interface must be implemented in order for the application to receive an ABR Track switch event from NexPlayer.

- `interface IListener`
    
    The application must implement this interface in order to receive events from NexPlayer.

- `interface IMetaDataEventListener`

- `interface IOfflineKeyListener`

- `interface IReleaseListener`
    
    This interface can be implemented in an application in order to receive NexPlayer release events from NexPlayer.

- `interface IVideoRendererListener`
    
    The application must implement this interface in order to receive video renderer-specific events from NexPlayer.

- `class NexDRMInitInfo`

- `enum NexErrorCategory`
    
    This enum defines the categories for errors.

- `enum NexErrorCode`
	
	Possible error codes that NexPlayer can return.
 
- `enum NexProperty`
    
    This enumerator defines the possible properties that can be set on a NexPlayer instance.

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

    No state information available for NexPlayer (this is the state after release has been called); a possible return value of NexPlayer.getState.

- `static final int NEXPLAYER_STATE_CLOSED = 1`

    No media source is open (this is the state when the NexPlayer instance is initially created, and after close has completed); a possible return value of getState.

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

Sole constructor for NexPlayer.

After constructing a NexPlayer object, you must call NexPlayer.init before you can call any other methods

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

This method adds a client module to NexPlayer.

> **Warning** Do not call this method when playing local content. It should only be used for streaming content.  Note that client modules are optional features of the NexPlayer SDK. For more information on how to integrate and use a client module available in the SDK (as well as sample code), please see the relevant NexXXXClient class.

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

Adds a callback that will be invoked when a NexPlayer instance is released.

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
| listener |The object on which methods will be called when the instance of NexPlayer is released.| 


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

This audio effect interface enhances sound on NexPlayer but is only available in some product categories.

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
 #### int changeSubtitleFD (AssetFileDescriptor afd)

Open the caption resource file which is attached in "res/raw" or "assets" folder.

Access should be provided by AssetFileDescriptor. Length and Offset will be calculated internally.

**Parameters**

| Name | Description | 
|---|---|
| afd | Asset file descriptor|
 
**Returns**

The status of the operation: this is zero in the case of success, or a non-zero NexPlayer error code in the case of failure.
 
> **Warning** When building the APK, most of resources will be compressed. This makes it difficult to extract FileDescriptor. To avoid compressing, you MUST change your file’s extension. These extensions are allowed: ".jpg", ".jpeg", ".png", ".gif", ".wav", ".mp2", ".mp3", ".ogg", ".aac", ".mpg", ".mpeg", ".mid", ".midi", ".smf", ".jet", ".rtttl", ".imy", ".xmf", ".mp4", ".m4a", ".m4v", ".3gp", ".3gpp", ".3g2", ".3gpp2", ".amr", ".awb", ".wma", ".wmv"
 
  
#### int close ()

This method ends all the work on the content currently open and closes content data.

The content must be stopped before calling this method.

The correct way to finish playing content is to either wait for the end of content, or to call stop and wait for the stop operation to complete, then call close.

> **Warning** However, do not call close in IListener’s event handlers as this may give rise to a deadlock. A safe way to call close is to use the Android UI main thread’s message handler.
 
**Returns**

Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
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

Note that this method cannot be called until after initializing NexPlayer by calling init(). Anytime DownloaderOpen() is called, this method must also be called properly close the Downloader module. If a call is also made to DownloaderStart(), then DownloaderStop() must be called BEFORE calling DownloaderClose() to properly end the event.

**Returns**

Zero if successful, or an error code in the event of failure.
 
#### native int DownloaderGetInfo(Object info)

This method is called to get information about a Downloader event.

Note that this method cannot be called until after initializing NexPlayer by calling init().


**Parameters**

| Name | Description | 
|---|---|
| info | The Downloader object to get information about. |

#### native int DownloaderOpen(String strUrl, String strStorePath, String proxyPath, int proxyPort, int eType)

This method is called to open a new event in the Downloader module.

The Downloader module allows users to download and save streaming progressive download (PD) content in MP4
containers so that it can be viewed at a later time. It must be opened before opening the content to be downloaded and calling `NexPlayer.open()`.

Note that this method cannot be called until after initializing NexPlayer by calling init().

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

Note that this method cannot be called until after both initializing NexPlayer by calling init() and opening an event in the Downloader module with DownloaderOpen().

**Returns**
 
Zero if successful, or an error code in the event of failure.
 
#### native int DownloaderStop()

This method is called to stop downloading and saving content in a Downloader event.

Note that this method cannot be called until after initializing NexPlayer by calling init(). Anytime a call is made to `DownloaderStart()`, it must be matched by a call to this method to properly stop and finish a Downloader event.

**Returns**

Zero if successful, or an error code in the event of failure.

#### native int enableDynamicThumbnail()

This method is used to enable and apply the Dynamic Thumbnail feature for Smooth Streaming content.

Refer to the following steps to use this method accurately:

1. The `enableDynamicThumbnail()` method should be called before `NexPlayer.open`.
2. When open completes, use the `getContentInfo()` method to get the total playtime of the content. By dividing the extracted total playtime value by the number of the thumbnail buffer array from the UI (the number of available thumbnails), the interval time is determined. The interval time can then be used with the `setOptionDynamicThumbnail()` method to get thumbnail information.
3. If the setting above works normally, NexPlayer will use the `onDynamicThumbnailData()` method to send thumbnail data to the UI.
4. The `disableDynamicThumbnail()` method should be called before `NexPlayer.close` when closing content.
5. If a video track is changed while content is playing, these methods should be called in the following order:
    - FIRST, `disableDynamicThumbnail()`
    - SECOND, `enableDynamicThumbnail()` to enable Dynamic Thumbnails for the new content, and
    - LASTLY, `setOptionDynamicThumbnail(OPTION_DYNAMIC_THUMBNAIL_INTERVAL, interval_time, 0)` to set the appropriate interval for the new thumbnails.

**Returns**
 
Zero if successful, or an error code in the event of failure.
 
 
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
 
Zero for success, or a non-zero NexPlayer error code in the event of a failure.
  
#### native int fastPlayStart (int msec, float rate)

This method activates thefastPlayfeature in HLS content.

> **Warning**  This method can be used in HLS content only.
 
The `fastPlay` feature allows NexPlayer to play HLS content at a speed other than normal playback speed.
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
 
Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
#### int fastPlayStop (boolean bResume)

This function turns off thefastPlayfeature in HLS content.

Once the `fastPlay` feature has been activated by calling fastPlayStart, this method must be called in order to stop fastPlay.

In order to reactivate the fastPlay feature after calling fastPlayStop, simply call the fastPlayStart method again. If fastPlayStop is called when fastPlay is not activated, an error will be returned.

**Parameters**

| Name | Description | 
|---|---|
| bResume | This boolean value sets whether to resume playback after fastPlay or not. If bResume = 1, video will automatically resume playback when fastPlay stops. If bResume= 0, when fastPlay stops, the content in NexPlayer will be paused.|
 
**Returns**

Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
#### native int getAudioSessionId()

This method gets an audio session ID in order to use Android’s audio effects with NexPlayer.
 
This API allows NexPlayer to support use of the Android audio effects like the Android Audio Equalizer. This method should be called before using any audio effect.

**Returns**

An audio session ID as an integer.
    

#### int getClientStatus ( int id)

This method gets the current status of a client module integrated into the NexPlayer SDK.

> **Warning** Note that client modules are optional features of the NexPlayer SDK. For more information on how to integrate and use a client module available in the SDK (as well as sample code), please see the relevant NexXXXClient class.
 
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

**Video Performance Information (Available only via `getContentInfoInt`):** The NexPlayer engine reads
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

This method gets the current play time position of NexPlayer in the given content.

This method can be called at any time to check the current position.

**Returns**
 
The current play time position inmsec(milliseconds).

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
  
 
#### native int GetRenderMode ()

Returns the type of renderer in use by the NexPlayer engine.

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

This method returns the name of the NexPlayer SDK in use. It can be used for confirmation and for debugging purposes but should generally be ignored.

**Returns**
 
The name of the NexPlayer SDK as a string.
 
#### long[] getSeekableRangeInfo()

This method returns the range of the current content that is seekable.

This method is used to allow NexPlayer to support timeshifting playback within HLS Live and Smooth Streaming content. Based on the amount of content available from the server at a particular time, it determines the seekable range within the playing content which also indicates the range where playback may be timeshifted. This range will be constantly shifting as the live streaming content available from the server changes in real time, so this method will need to be repeatedly called to ensure accurate shifting of playback.

For local content this method will always return the same two values, and the second value indicating the end of the seekable range will continuously change in progressive download (PD) content, but this method is most relevant when playing live streaming content, as with HLS and Smooth Streaming.

For more information about how this method may be used to timeshift playback in live content, please also refer to the introductory section on time shift support.

**Returns**

An array of twolongs, the firstlongbeing the timestamp indicating the start of the seekable range and the
second being the timestamp indicating the end of the seekable range.
 
#### native int getState()

This method retrieves the current state of NexPlayer.

Calling methods such as open and start does not immediately change the state. The state changes asynchronously, and the new state goes into effect at the same time onAsyncCmdComplete is called to notify the application.

**Returns**
 
A constant indicating the current state. This is one of the following **Values:**
 
- NEXPLAYER\_STATE\_CLOSED
- NEXPLAYER\_STATE\_NONE
- NEXPLAYER\_STATE\_PAUSE
- NEXPLAYER\_STATE\_PLAY
- NEXPLAYER\_STATE\_STOP
 
#### native int getVersion(int mode)

Gets NexPlayer SDK version information.

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
 
#### native int GLInit ( int width,int height)

Informs NexPlayer of the current size of the GLSurfaceView subclass instance.

This should be called whenever the size of theGLSurfaceViewsubclass instance changes, as well as when the
instance is initially created. This is because internally, OpenGL APIs use a different coordinate system, and NexPlayer must know the pixel dimensions in order to map the OpenGL coordinate system to per-pixel coordinates.

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
exact, set totrue. In other words, NexPlayer will seek exactly to the time specified bymsec(milliseconds).

**Returns**
 
Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
#### native int gotoCurrentLivePosition(boolean exact)

This method moves to the current live position after the actual playback position.

Normally, when playing live content, previously recorded data (for example, a few seconds earlier than the actual live position) to avoid buffering. This method however ignores this concept and moves directly to the latest loaded playback position (where the server is currently being encoded).

**Parameters**

| Name | Description | 
|---|---| 
|exact| If exact is true, the player will seek exactly to the time specified bymsec(milliseconds). Otherwise, the playhead will seek to the nearest approximate position for faster seeking performance. |
 
**Returns**

Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
#### NexErrorCode init (Context context)

This method initializes NexPlayer.

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
 
NexPlayer error code for the generated error.
 
#### NexErrorCode init (Context context, int logLevel)

This method initializes NexPlayer.

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
|logLevel| NexPlayer SDK logging level. This affects the messages that the SDK writes to the Android log.<br>**-1** : Do not output any log messages.<br>**0** : Output basic log messages only (recommended).<br>**1** ∼ **4** : Output detailed log messages; higher numbers result in more verbose log entries, but may cause performance issues in some cases and are not recommended for general release code.|

**Returns**

NexErrorCode.NONE if initialization succeeded; NexPlayer errorcode for the generated error in
the case of a failure (in the case of failure, check the log for details).
 
 
#### boolean isInitialized ( )

Determines if NexPlayer is currently initialized.

To initialize NexPlayer, NexPlayer.init must be called. If that method returnstrue, then this method will also return true if called on the same instance of NexPlayer.

In some cases, it is necessary to call NexPlayer functions from event handlers in subclasses ofActivity(such as `onPause` or `onStop`). In such event handlers, it is possible for them to be called before code that initializes NexPlayer, or for them to be called after a failed initialization. Therefore, any calls to NexPlayer methods made from onPause or similar event handlers must be protected as follows:

```java
if( nexPlayer.isInitialized()) {
// Calls to other methods are safe here
}
```
**Returns**
 
true if NexPlayer is currently initialized.
 
#### native int notifyHeadsetState(int uiOnOff)

This method notifies the NexPlayer engine whether a wired headset has been plugged in or unplugged.

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
|uiOnOff| An integer indicating whether enhanced sound ison(a headset is plugged in) or off(the headset is unplugged) when enhanced sound is available in the NexPlayer SDK. Possible **Values:**<br>- on = 1<br>- off = 0|

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

The status of the operation: this is zero in the case of success, or a non-zero NexPlayer error code in the
case of failure.
 
> **Note** This only indicates the success or failure ofstartingthe operation. Even if this reports success, the operation may still fail later, asynchronously, in which case the application is notified in onAsyncCmdComplete.
 

#### int openFD (AssetFileDescriptor afd)

Open the media resource file which is attached in "res/raw" or "assets" folder Access should be provided by AssetFileDescriptor.

Length and Offset will be calculated internally.

**Parameters**

| Name | Description | 
|---|---| 
|afd| Asset file descriptor.|
 
**Returns**
 
The status of the operation: this is zero in the case of success, or a non-zero NexPlayer error code in the
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

The status of the operation: this is zero in the case of success, or a non-zero NexPlayer error code in the
case of failure.
 
> **Warning** When building the APK, most of resources will be compressed. This makes it difficult to extract FileDescriptor. To avoid compressing, you MUST change your file’s extension. Below extensions are allowed: ".jpg", ".jpeg", ".png", ".gif", ".wav", ".mp2", ".mp3", ".ogg", ".aac", ".mpg", ".mpeg", ".mid", ".midi", ".smf", ".jet", ".rtttl", ".imy", ".xmf", ".mp4", ".m4a", ".m4v", ".3gp", ".3gpp", ".3g2", ".3gpp2", ".amr", ".awb", ".wma", ".wmv"

#### int pause()

This method pauses the current playback.

Please note that when the hardware codec is in use, if the application is sent to the background by pressing the home button, pausing and resuming playback may return an error because of resource limitations. To avoid this potential issue, stopping and starting playback is recommended in algorithm handling this specific case of the application being sent to the background because the home button was pressed.

**Returns**

Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
#### native int playspeedcontrol(float fPlaySeed)

This method controls the playback speed of content by the given percent.

> **Note** Speed Control is an optional feature. This method makes it possible to allow users to adjust the playback speed of content, from a quarter of the original speed to double speed, by changing the value of the parameter fPlaySeed. For example, to play content at half-speed,fPlaySeedshould be set to 0.5
 
This method doesn’t work if it is called when NexPlayer is stopped.

**Parameters**

| Name | Description | 
|---|---| 
|fPlaySeed| This float represents the percentage by which to change the playback speed. It must be in
the range of 0.25 to 2.0, which adjusts the playback speed from 0.25x to 2x the original speed
of the content.|
 
> **Warning** When using this method with HLS or Smooth Streaming content, playing multitrack content may cause unstable performance. Therefore, playing content as a single track is encouraged.
 
#### native int reconnectNetwork()

This method allows NexPlayer to reconnect to the media server in the case of streaming content.

It allows NexPlayer to reconnect to a media server when network conditions may have closed a connection.

> **Warning** This is only supported in HLS, DASH, SmoothStreaming and PD streaming content.
 
**Returns**

Zero if successful or a non-zero error code.
 

#### void release()

This method releases resources used by the NexPlayer instance.

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

This method removes a client module integrated into the NexPlayer SDK.

Note that client modules are optional features of the NexPlayer SDK. For more information on how to integrate and use a client module available in the SDK (as well as sample code), please see the relevant NexXXXClient class.

> **Warning** When NexPlayer is released, the client will be removed automatically.
 
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
|listener| The object on which methods will be called when the instance of NexPlayer is released.|
 
**See Also**

- NexPlayer.IReleaseListener
- NexPlayer.addReleaseListener
 
#### int resume ()

This method resumes playback beginning at the point at which the player was last paused.

**Returns**
 
Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
#### native int seek ( int msec,boolean exact)

This method seeks the playback position to the specified time.

This doesn’t work if NexPlayer is stopped or if the stream doesn’t support seeking, but does work if NexPlayer is playing or paused.

Note that even if the parameterexactisTRUE, it is possible to minimize seek time by adjusting the NexProperty SEEK\_RANGE\_FROM\_RA\_POINT.

Note that NexPlayer’s state will be changed to pause and resume automatically if this method is called during playback. Therefore, if getState is calling while NexPlayer is seeking, the UI can get NEXPLAYER\_STATE\_PAUSE.

**Parameters**

| Name | Description | 
|---|---|
|msec| The offset inmsec(milliseconds) from the beginning of the media to which the playback position should seek.|
|exact| If exact is true, the player will seek exactly to the time specified bymsec(milliseconds). Otherwise, the playhead will seek to the nearest approximate position for faster seeking performance.
 
**Returns**

Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
**See Also**
 
NexProperty.SEEK\_RANGE\_FROM\_RA\_POINT
 
#### int seek (int msec)

This function seeks the playback position exactly to a specific time.

This doesn’t work if NexPlayer is stopped or if the stream doesn’t support seeking, but does work if NexPlayer is playing or paused.

This method behaves in the same way as the method seek(int msec, boolean exact) with the second parameter,
exact, set totrue. In other words, NexPlayer will seek exactly to the time specified bymsec(milliseconds).

**Parameters**

| Name | Description | 
|---|---|
|msec| The offset in milliseconds from the beginning of the media to which the playback position should seek.|
 
**Returns**

Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
**See Also**
 
NexPlayer.seek(int msec, boolean exact)
 
#### native int setAudioPitch ( int iPitchIndex)

This method sets the pitch control settings for audio in content.

> **Note** Audio pitch control is an optional feature in the NexPlayer SDK.
 
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
 
When Auto Volume is turnedon, NexPlayer automatically adjusts the volume level of different content so that
it is played at a consistent and optimal volume level, allowing the user to play different content without having to constantly adjust the volume when new content starts.

By default, Auto Volume is turnedoff(identical to the behavior of the player in product categories that do not support this feature).

**Parameters**

| Name | Description | 
|---|---| 
|uiOnOff| This turns the Auto Volume featureonand. By default, this feature isoff= 0.<br>Possible **Values:** <br>- on= 1<br>- off= 0|

**Returns**
 
The new value of Auto Volume. If Auto Volume was turnedoff, this will be 0.
If Auto Volume was turnedon, it will return 1.
If Auto Volume is not supported in this version of the NexPlayer, this will return the error, NOT\_SUPPORT
(0x8000000FL).
 
#### native int SetBitmap (Object mFrameBitmap)

Sets a bitmap to be used to receive rendered frames for display, when using the Java-based renderer.

For more information on this method, please also refer to theJava Renderersection of the NexPlayer Engine
documentation.

**Parameters**

| Name | Description | 
|---|---| 
|mFrameBitmap| The bitmap to receive rendered frames (when using Java-based renderer).|
 
**Returns**

Always 0, but may change in future versions. The return value should be ignored.
  
#### int setClientTimeShift (boolean bEnable, String strFileBufferPath, int uiTimeShiftBufferSize,int uiTimeShiftDuration)

This method enables the client time shift feature in the NexPlayer SDK.

Time shifting is a feature to store realtime data as it is received so that the user can watch past data while playing live content. When this feature is enabled, NexPlayer prepares for the time shift and only afterpauseis called, it stores received data from a live stream in local file storage with the specified buffer size and duration set with this API. As a result, the user can seek and pause even when the content playing is live. This method will be stopped when the methodgotoCurrentLivePositionis called.

> **Note** This method should be called between calls toinit()andopen(). Furthermore, onceopen()is called,
the parameter values cannot be changed unless the application is closed by callingclose()and then
initialized withinit()again.
 
> **Warning** Values for the uiTimeShiftBufferSize and uiTimeShiftDuration parameter should be set
carefully because each device has different capabilities and the NexPlayer SDK can’t guarantee that the
device has enough free space to store data as the user specifies. If storage becomes full and there is no
available space to save the new data, NexPlayer will force the content to resume to use up saved data and
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
 

#### native int SetContrastBrightness (int Contrast, int Brightness)

This method allows NexPlayer to adjust the contrast and brightness of the displayed content.

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

This method sets the debugging log levels related to codecs, rendering, and protocols in NexPlayer.

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

This method inputs the license file information into a NexPlayer buffer. This should be called after calls toNexAlFactory::initand before calling `NexPlayer::setNexAlFactory`. The location of the license file included with the NexPlayer SDK Java files can be set using the method `setLicenseFile`.

**Parameters**

| Name | Description | 
|---|---|
|strBuffer| Information in the license file, as a string.|
 
**See Also**

 
setLicenseFile(String strPath) for more information.
  
#### native int setLicenseFile (String strPath)

This method sets the path to the specific license file included with the NexPlayer SDK.

This should be called after NexAlFactory::init and before NexPlayer::setNexAlFactory. The license file will be included with the NexPlayer SDK Java files and when called with this API, an application will be able to input the license file information to run NexPlayer.

> **Warning** The license file will be updated regularly, so please always check for updates and be sure to replace and use the latest license file in applications built with the NexPlayer SDK.
 
**Parameters**

| Name | Description | 
|---|---|
|strPath| Path to the license file, as a string.|
 
**See Also**

setLicenseBuffer(String strBuffer)
 
#### void setLicenseRequestListener (INexDRMLicenseListener listener)

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
 
#### int setNetAddrTable(NexNetAddrTable table,int nNetAddrTableType)

This method sets a table and table type to be used by the NexPlayer to retrieve host information when custom IP addresses should be used.

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

Sets the NexALFactory in order to inform what type of codec NexPlayer will use.

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

Sets the value of an individual NexPlayer integer property based on the numerical ID of the property.

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
  
#### native int setRenderOption(int iFlag)

This function configures the paint flags used with the Android bitmap rendering module.

There are multiple rendering modules that can be used for displaying video and NexPlayer automatically selects the best one for the given content and device.

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

In prior versions of the NexPlayer SDK, it was only possible to set a user cookie before content was opened in the player but this method makes it possible to set a cookie while content is playing. The cookie set with this method may also be different than an initial cookie set.

**Parameters**

| Name | Description | 
|---|---|  
|strCookie| The user cookie to set, as a string. When setting a cookie string, it should start with "Set-Cookie:". For example:<br>`mNexPlayer.setUserCookie("Set-Cookie: [cookie string]");`<br>When setting two or more cookies, it should start with "Cookie:" and each cookies are separated by ";". For example:<br> `mNexPlayer.setUserCookie("Cookie: [cookie string1];[cookie string2];[cookie string3]...");`|
 
**Returns**
 
Zero if successful, non-zero if there was an error.
  
#### int setVideoBitrates(int[] bitrates)

This method allows specific subtracks to be selected and played based on the bitrates of the tracks in HLS content.

Only the tracks with the bitrates passed to this method with the parameterbitrateswill be played by NexPlayer.

**Parameters**

| Name | Description | 
|---|---|  
|bitrates| The bitrates of the HLS content subtracks to play, as an integer array.|
 
**Returns**

Zero if successful or a non-zero error code.
 
#### int setVideoBitrates (int[] bitrates, int option)

This method allows specific subtracks to be selected and played based on the bitrates of the tracks in HLS content.

Only the tracks with the bitrates passed on this method with the parameterbitrateswill be played by Nex-
Player. However, choosing a different option with the parameteroptionallows NexPlayer to choose and play
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

- renderers The introductory section on renderers in the NexPlayer SDK.
- NexVideoRenderer
- NexPlayer.IVideoRendererListener
 
#### native int setVolume (float fGain)

This sets the player output volume.

This affects the output of the player before it is mixed with other sounds. Normally, this should be left at the default setting of 1.0, and the volume should be adjusted via the device master volume setting (adjustable by the user via the hardware volume buttons on the device). However, if the application contains multiple audio sources (or if there is other audio being played on the device), this property can be used to reduce the NexPlayer volume in relation to other sounds.

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

The status of the operation. This is zero in the case of success, or a non-zero NexPlayer error code in the
case of failure.
 
> **Note** This only indicates the success or failure ofstartingthe operation. Even if this reports success, the operation may still fail later, asynchronously, in which case the application is notified in `onAsyncCmdComplete`.
 
#### native int start (int msec,boolean pauseAfterReady)

Starts playing media from the specified timestamp.

The media must have already been successfully opened with open. This only works for media that is in the stopped state; to change the play position of media that is currently playing or paused, call seek instead.

When this operation completes, onAsyncCmdComplete is called with one of the following command constants
(depending on the types pecified in theopencall):

- NEXPLAYER\_ASYNC\_CMD\_START\_LOCAL
- NEXPLAYER\_ASYNC\_CMD\_START\_STREAMING
- NEXPLAYER\_ASYNC\_CMD\_START\_STORE\_STREAM

Success or failure of the operation can be determined by checking theresultargument passed toonAsync-
CmdComplete. If the result is 0, the media was successfully opened; if it is any other value, the operation failed.

**Parameters**

| Name | Description | 
|---|---|  
|msec| The offset (in milliseconds) from the beginning of the media at which to start playback. This should be zero to start at the beginning. This parameter will be ignored if content is opened with NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAMsince the content will be stored instead of played. This parameter must be set to a valid value within the seekable range. The value of the seekable range can be obtained using the `getSeekableRangeInfo()` API. If the content is a live stream, it is recommended to use the LIVE\_VIEW\_OPTION property.|
|pauseAfterReady| If this value is true, NexPlayer will pause just after buffering and before play This parameter will be ignored if content is opened with the NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAM parameter.  
Note that if this value isTRUE, NexPlayer’s state will be changed to NEXPLAYER\_STATE\_PAUSE when initial
buffering is done. This could take some time.|

**Returns**
 
The status of the operation. This is zero in the case of success, or a non-zero NexPlayer error code in the
case of failure.
 
> **Note** This only indicates the success or failure ofstartingthe operation. Even if this reports success, the operation may still fail later, asynchronously, in which case the application is notified inonAsyncCmdComplete.
 
#### int stop ()

This function stops the current playback.

**Returns**

Zero for success, or a non-zero NexPlayer error code in the event of a failure.

#### void videoOnOff(boolean bOn)

This method turns video rendering on or off.

If video rendering is turned off, any existing frame will remain on the display. If you wish to clear it, you may directly draw to the surface and fill it with black pixels after turning off video rendering.

> **Warning** This method only turns video rendering on or off. Video decoding is still performed.
 
**Parameters**

| Name | Description | 
|---|---| 
|bOn| TRUE to render video, FALSE to turn off video rendering.|

**Parameters**

| Name | Description | 
|---|---| 
|bOn| 1 to turn on video rendering, 0 to turn off video rendering. Other values are reserved and
should not be used.|
|bErase| This parameter is reserved; it must be zero.|
 
**Returns**
 
Always zero, but may change in future versions; the return value should be ignored.
 

#### final int AVAILBITRATES\_HIGH = 0x00000003

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int AVAILBITRATES\_INSIDERANGE = 0x00000005

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.

#### final int AVAILBITRATES\_LOW = 0x00000004

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int AVAILBITRATES\_MATCH = 0x00000001

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int AVAILBITRATES\_NEAREST = 0x00000002

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int AVAILBITRATES\_NONE = 0x00000000

This is a possible value for the option parameter in `setVideoBitrates(int [] bitrates, int option)`.
 
#### final int MEDIA\_STREAM\_DEFAULT\_ID = 0xFFFFFFFF

Possible value for arguments to NexPlayer.setMediaStream().

#### final int MEDIA\_STREAM\_DISABLE\_ID = 0xFFFFFFFE

Possible value for arguments to NexPlayer.setMediaStream().

#### final int MEDIA\_STREAM\_TYPE\_AUDIO = 0x00

Possible value for NexStreamInformation.mType; see there for details.

#### final int MEDIA\_STREAM\_TYPE\_TEXT = 0x02

Possible value for NexStreamInformation.mType; see there for details.

#### final int MEDIA\_STREAM\_TYPE\_VIDEO = 0x01

Possible value for NexStreamInformation.mType; see there for details.

#### final int MEDIA\_TRACK\_DEFAULT\_ID = 0xFFFFFFFF

Possible value for arguments to NexPlayer.setMediaTrack().

#### final int MEDIA\_TRACK\_DISABLE\_ID = 0xFFFFFFFE

Possible value for arguments to NexPlayer.setMediaTrack().

#### final int MEDIA\_TRACK\_TYPE\_AUDIO = 0x10

Possible value for NexStreamInformation.mType; see there for details.

#### final int NEX\_AS\_CINEMA\_SOUND = 0x00000006

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final int NEX\_AS\_EARCOMFORT = 0x00000001

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final int NEX\_AS\_MUSIC\_ENHANCER = 0x00000004

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final int NEX\_AS\_REVERB = 0x00000002

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final int NEX\_AS\_STEREO\_CHORUS = 0x00000003

One of the NexSound audio modes to be set by the uiAudioMode parameter in audioSetParam().

#### final String NEX\_DEVICE\_USE\_ANDROID\_3D = "Android 3D"

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.

#### final String NEX\_DEVICE\_USE\_AUTO = "Auto"

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.
 
#### final String NEX\_DEVICE\_USE\_JAVA = "JAVA"

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.

#### final String NEX\_DEVICE\_USE\_ONLY\_ANDROID = "Android"

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.

#### final String NEX\_DEVICE\_USE\_OPENGL = "OPENGL"

A possible value for the strRenderMode parameter of NexALFactory.init.

See that method description for details.

#### final int NEXDOWNLOADER\_ASYNC\_CMD\_CLOSE = 0x00200002

Possible value for msg parameter of onDownloaderAsyncCmdComplete.

#### final int NEXDOWNLOADER\_ASYNC\_CMD\_OPEN = 0x00200001

Possible value for msg parameter of onDownloaderAsyncCmdComplete.

#### final int NEXDOWNLOADER\_ASYNC\_CMD\_START = 0x00200003

Possible value for msg parameter of onDownloaderAsyncCmdComplete.

#### final int NEXDOWNLOADER\_ASYNC\_CMD\_STOP = 0x00200004

Possible value for msg parameter of onDownloaderAsyncCmdComplete.

#### final int NEXDOWNLOADER\_OPEN\_TYPE\_APPEND = 1

This is a possible value for the parameter eType in the method DownloaderOpen().

#### final int NEXDOWNLOADER\_OPEN\_TYPE\_CREATE = 0

This is a possible value for the parameter eType in the method DownloaderOpen().

#### final int NEXDOWNLOADER\_STATE\_CLOSED = 2

This is a possible value for the parameter param2 of onDownloaderEventState.

#### final int NEXDOWNLOADER\_STATE\_DOWNLOAD = 4

This is a possible value for the parameter param2 of onDownloaderEventState.

#### final int NEXDOWNLOADER\_STATE\_NONE = 0

This is a possible value for the parameter param2 of onDownloaderEventState.

#### final int NEXDOWNLOADER\_STATE\_STOP = 3

This is a possible value for the parameter param2 of onDownloaderEventState.

#### final int NEXPLAYER\_ASYNC\_CMD\_FASTPLAY\_START = 0x00000027

Possible value for command parameter of onAsyncCmdComplete.
 
#### final int NEXPLAYER\_ASYNC\_CMD\_FASTPLAY\_STOP = 0x00000028

Possible value for command parameter of onAsyncCmdComplete.
 
#### final int NEXPLAYER\_ASYNC\_CMD\_NONE = 0x00000000

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_OPEN\_LOCAL = 0x00000001

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_OPEN\_STORE\_STREAM = 0x00000101

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_OPEN\_STREAMING = 0x00000002

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_PAUSE = 0x00000009

Possible value for command parameter of onAsyncCmdComplete.
 
#### final int NEXPLAYER\_ASYNC\_CMD\_RESUME = 0x0000000A

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_SEEK = 0x0000000B

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_SET\_MEDIA\_STREAM = 0x00000031

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_SET\_MEDIA\_STREAM\_TRACK = 0x00000033

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_SET\_MEDIA\_TRACK = 0x00000032

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_START\_LOCAL = 0x00000005

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_START\_STORE\_STREAM = 0x00000102

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_START\_STREAMING = 0x00000006

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_ASYNC\_CMD\_STOP = 0x00000008

Possible value for command parameter of onAsyncCmdComplete.

#### final int NEXPLAYER\_SIGNAL\_STATUS\_NORMAL = 0

Normal signal status; see `onSignalStatusChanged` for details.

#### final int NEXPLAYER\_SIGNAL\_STATUS\_OUT = 2

No signal (out of service area); see `onSignalStatusChanged` for details.

#### final int NEXPLAYER\_SIGNAL\_STATUS\_WEAK = 1

Weak signal status; see `onSignalStatusChanged` for details.

#### final int NEXPLAYER\_SOURCE\_TYPE\_LOCAL\_NORMAL = 0

Treats path as a local media file; a possible value for the type parameter of NexPlayer.open.

#### final int NEXPLAYER\_SOURCE\_TYPE\_STORE\_STREAM = 2

Treats path as a URL to a streaming media source to be stored for offline playback; a possible value for the type parameter of NexPlayer.open.

#### final int NEXPLAYER\_SOURCE\_TYPE\_STREAMING = 1

Treats path as a URL to a streaming media source; a possible value for the type parameter of NexPlayer.open.

#### final int NEXPLAYER\_STATUS\_REPORT\_AUDIO\_GET\_CODEC\_FAILED = 0x1

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_AUDIO\_INIT\_FAILED = 0x3

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_AVMODE\_CHANGED = 0xa

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_CONTENT\_INFO\_UPDATED = 0x9

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_DISCONTINUITY\_EXIST = 0x12

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_DOWNLOAD\_PROGRESS = 0x80

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_DSI\_CHANGED = 0x7

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_EXTERNAL\_DOWNLOAD\_CANCELED = 0x20

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_HTTP\_INVALID\_RESPONSE = 0xb

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_MAX = 0xFFFFFFFF

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_MINMAX\_BANDWIDTH\_CHANGED = 0x21

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_NONE = 0x0

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_OBJECT\_CHANGED = 0x8

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_STREAM\_CHANGED = 0x6

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_STREAM\_RECV\_PAUSE = 0x60

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_STREAM\_RECV\_RESUME = 0x61

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_TARGET\_BANDWIDTH\_CHANGED = 0x22 , [protected]

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_TRACK\_CHANGED = 0x5

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_VIDEO\_GET\_CODEC\_FAILED = 0x2

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_STATUS\_REPORT\_VIDEO\_INIT\_FAILED = 0x4

Possible value for msg parameter of onStatusReport.

#### final int NEXPLAYER\_TRACK\_ENABLE\_OPTION\_DISABLED\_TEMPORARY = 1

possible value for the NexPlayer.enableTrack method

Enable the track which is disabled by temporary content issues; possible value for the NexPlayer.enableTrack
method

#### final int OPTION\_DYNAMIC\_THUMBNAIL\_INTERVAL = 1

This is one possible option property for the Dynamic Thumbnail feature in Smooth Streaming content and a possible value of the option parameter of `setOptionDynamicThumbnail`.
 
#### final int RENDER\_MODE\_VIDEO\_ALLFLAG = 0xFFFFFFFF

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### final int RENDER\_MODE\_VIDEO\_ANTIALIAS = 0x00000004

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### final int RENDER\_MODE\_VIDEO\_DITHERING = 0x00000002

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### final int RENDER\_MODE\_VIDEO\_FILTERBITMAP = 0x00000001

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### final int RENDER\_MODE\_VIDEO\_NONE = 0x00000000

This is a possible value for the iFlag parameter of setRenderOption.

See that method for details.

#### int RTSP\_METHOD\_ALL

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

#### int RTSP\_METHOD\_DESCRIBE = 0x00000001

This is a possible value for themethodsparameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_GETPARAMETER = 0x00000020

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_OPTIONS = 0x00000004

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_PAUSE = 0x00000010

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_PLAY = 0x00000008

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_SETUP = 0x00000002

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

#### int RTSP\_METHOD\_TEARDOWN = 0x00000040

This is a possible value for methods parameter of addRTSPHeaderFields.

See that method for details.

### NexSessionData Class Reference

#### String mValue

It is identified by a string, DATA-ID.

If LANGUAGE is specified, this attribute must be included in a human-readable form in the specified language.

### NexSoundEffect Class Reference

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

It is only supported with the SOUND\_EFFECT\_3DAUDIO\_SOLUTION01 or the SOUND\_EFFECT-HEAD\_TRACKING option.

**Parameters**

| Name            | Description              |
|-----------------|------|
| w | The w of quaternion that used to represent a rotation in 3D space. |
| x | The x of quaternion that used to represent a rotation in 3D space. |
| y | The y of quaternion that used to represent a rotation in 3D space. |
| z | The z of quaternion that used to represent a rotation in 3D space. |


### NexSystemInfo Class Reference

This class provides NexPlayer with information about the system and device.

#### static int getCPUInfo ( )

This method returns the CPU architecture information.

**Returns**

CPU architecture information; one of:
 
- `NEX_SUPPORT_CPU_ARMV5`
- `NEX_SUPPORT_CPU_ARMV6`
- `NEX_SUPPORT_CPU_ARMV7`
- `NEX_SUPPORT_CPU_ARM64_V8A`
- `NEX_SUPPORT_CPU_X86`
- `NEX_SUPPORT_CPU_X86_64`

#### static int getPlatformInfo ( )

This method returns the Android Version of the device platform.


#### final int NEX\_SUPPORT\_CPU\_X86 = 0x86

Return value of getCPUInfo() for Intel x86 chipsets.
 
#### boolean x86Disabled = false

Allows the CPU architecture (whether it should be viewed as x86 or ARM) to be set externally.

Set this to TRUE to ignore internal settings and force set the CPU architecture to ARM, or FALSE to check whether
the internal setting is set to ARM or x86.

### NexVideoView( Context context )

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

 
Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
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


Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
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

 
Zero for success, or a non-zero NexPlayer error code in the event of a failure.
  
#### int getAudioSessionId ( )

This method gets an audio session ID in order to use Android’s audio effects with the NexPlayer.

**See Also**

 
- NexPlayer.getAudioSessionId

#### int getBufferPercentage ( )

This method determines the amount of currently buffered data, in percentage.

It calculates the percentage of data that has been buffered with the cts of the last frame in buffer. Note that CTS
stands for "Current Time Stamp".

**Returns**

 
The percentage of buffered data.

 
#### NexCaptionPainter getCaptionPainter ( )

This method gets an object of the  NexCaptionPainter.

To use any specific feature provided by the NexCaptionPainter, use this method to call desired API to the NexCaptionPainter object.

**Returns**

A NexCaptionPainter object.

 
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

This method gets the current play time position of NexPlayer in the given content.

This method can be called at any time to check the current position.

**Returns**

 
The current play time position in milliseconds (msec).
 
#### int getDuration ( )

This method gets the total duration of a media content.

For live contents, the seekable range will be returned.

**Returns**

 
The total duration of a media content, in milliseconds (msec).

#### NexPlayer getNexPlayer ( )

This method gets an object of the NexPlayer.

To use a specific feature provided by the NexPlayer SDK, use this method to call desired API to the NexPlayer object.

**Returns**

 
A NexPlayer object.
 
#### Object getProperty ( NexPlayer.NexProperty property )

This method gets the value of an individual properties of the NexPlayer.

The properties control the behavior of NexPlayer and the features that are enabled.

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

This method clears the resources of NexVideoView including NexPlayer and NexALFactory.

This method must be called when the activity is destroyed.
 
#### void resume ( )

This method resumes the playback, beginning at the point at which the player was last paused.

#### void seekTo ( int msec )

This method seeks the playback position to the specified time.

This method will operate when the NexPlayer is playing or paused but will not operate when NexPlayer has
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

This method sets MediaController to NexVideoView to control the NexPlayer.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| controller   | A MediaController object to connect to NexPlayer.                                                                                                                                                            |

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
 
Zero for success, or a non-zero NexPlayer error code in the event of a failure.
 
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

This method sets the value of an individual properties of the NexPlayer.

It’s recommended to call this method after getting the OnConfigurationcallback by registering OnConfigurationListener on NexVideoView. We can not guarantee what result the NexPlayer will
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
 your index file is unmerged.

### NexVideoView.OnBufferingUpdateListener Interface Reference

The application must implement this interface in order to receive buffering events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.

#### void onBuffering ( NexPlayer mp, int progressInPercent )

reports the current buffering status.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer object to which this event applies.                                                                                                                                                            |
| progressInPercent   | The current buffering percentage.                                                                                                                                                   |
 
#### void onBufferingBegin ( NexPlayer mp )

the start of buffering.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer object to which this event applies.                                                                                                                                                            |
 
#### void onBufferingEnd ( NexPlayer mp )

This reports the end of buffering.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer object to which this event applies.                                                                                                                                                            |
 
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
| mp   | The NexPlaye object generating the event.                                                                                                                                                            |
 
### NexVideoView.OnConfigurationListener Interface Reference

The application must implement this interface in order to receive NexVideoView events before NexPlayer is opened.

The application must implement settings for the NexPlayer before the NexPlayer.open() such assetProperty.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may
not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is
to use android.os.Handler to post an event back to the main application thread.
 
### NexVideoView.OnDynamicThumbnailListener Interface Reference

The application must implement this interface in order to receive Dynamic Thumbnail related events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may
not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 

#### void onDynamicThumbnailData ( int cts, Bitmap bitmap )

This method will be called by the NexPlayer engine when thumbnail data is created.

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
| mp   | The NexPlayer object generating the event.                                                                                                                                                            |
| errorCode   | The error code for the generated error.                                                                                                                                                   |
 
### NexVideoView.OnExternalSubtitleChangedListener Interface Reference

The application must implement this interface in order to receive onExternalSubtitleChanged events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
#### void onExternalSubtitleChanged ( NexPlayer mp, int result )

An event will occur when addSubtitleSource is successful.

**Parameters**

| Name   | Description                                                                                                                                                   |
|--------|---------------|
| mp   | The NexPlayer object to which this event applies.                                                                                                                                                            |
| result   | Zero for success, or a non-zero NexPlayer error code in the event of a failure.                                                                                                                                                   |
 
### NexVideoView.OnFastPlayListener Interface Reference

The application must implement this interface in order to receive fastPlay related events from NexVideoView.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
#### void onFastPlayStart ( NexPlayer mp, int result )

An event will occur when fastPlayStart is successful.

**Parameters**

| Name   | Description                                                                                                                                                   
|--------|-----------------|
| mp   | The NexPlayer object to which this event applies. |
| result   | Zero for success, or a non-zero NexPlayer error code in the event of a failure. |
 
#### void onFastPlayStop ( NexPlayer mp, int result )

An event will occur when fastPlayStop is successful.

**Parameters**

**Parameters**

| Name   | Description                                                                                                                                                   
|--------|-----------------|
| mp   | The NexPlayer object to which this event applies.|
| result   | Zero for success, or a non-zero NexPlayer error code in the event of a failure.|
 
### NexVideoView.OnInfoListener Interface Reference

This interface transfer updated NexContentInformation to the application.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 
#### void onInfo ( NexPlayer mp, NexContentInformation info )

An event will occur when NexContentInformation is being updated.

**Parameters**

| Name   | Description|
--------|-------------------|
| mp   | The NexPlayer object to which this event applies.  |
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
|mp| The NexPlayer object to which this event applies.|
|result| Zero for success, or a non-zero NexPlayer error code in the event of a failure.|
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
|mp| The NexPlayer object to which this event applies.|

 
### NexVideoView.OnPreparedListener Interface Reference

The application must implement this interface in order to receiveNexVideoViewevents when NexPlayer is ready for the playback.

This callback must be registered to operateNexVideoViewsuccessfully.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
  
#### void onPrepared (NexPlayermp)

This method is called when setVideoPath or setVideoURI is successful.

In case of an error, an onError event will occur instead of anonPreparedevent.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer object to which this event applies.|
 
### NexVideoView.OnResumeCompleteListener Interface Reference

The application must implement this interface in order to receiveonResumeCompleteevents fromNexVideo-
View.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
 

#### void onResumeComplete (NexPlayermp)

An event will occur whenresumeis successful.

**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer object to which this event applies.|
 
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
|result| Zero for success, or a non-zero NexPlayer error code in the event of a failure.|
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
|mp| The NexPlayer object to which this event applies.|
  
### NexVideoView.OnStopCompleteListener Interface Reference

The application must implement this interface in order to receiveonStopCompleteevents fromNexVideo-
View.

> **Warning** These callbacks may occur in any thread, not necessarily the main application thread. In some cases, it may not be safe to call UI-related functions from within IListener callbacks. The safest way to update the UI is to use android.os.Handler to post an event back to the main application thread.
  
#### void onStopComplete (NexPlayer mp,int result)

An event will occur whenstopPlaybackis successful.


**Parameters**

| Name  | Description  | 
|---|---|
|mp| The NexPlayer object to which this event applies.|
|result| Zero for success, or a non-zero NexPlayer error code in the event of a failure.|
 
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
|mp| The NexPlayer object to which this event applies.|
| timedMeta| An NexID3TagInformation object that contains the timed metadata associated with the content to be displayed.|
 
### NexVideoView.OnTimeUpdateListener Interface Reference

**Public Member Functions**

- `void onTime (NexPlayer mp, int currTime)`

#### static native int initDRMManager ( String strEngineLibName)

Initializes and registers the PiffPlayReadyDRMManager.

**Parameters**

| Name  | Description  | 
|---|---|
|strEngineLibName|The relevant engine library name as a string.|
 
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

### NexVideoView.Settings Class Reference

This class manages the setting values needed for initializing Video Renderer, Caption Renderer and NexPlayer internally.

To initialize successfully,*setSettings* must be called before *setVideoPath* or *setVideoURI* is called, after changing the setting value by using *setValue*. Note that *setSettings* is not guaranteed to work properly when called at any other time.

#### Object getValue (int key)

This method gets the setting value correspondent to a specific key.

**Parameters**

| Name | Description                        |
|------|----------------|
| key  | The key to retrieve setting value. |

**Returns**

The value correspondent to the key.

#### boolean setValue (int key,int value)

This method sets the setting values for the properties of NexPlayer.

**Parameters**

| Name  | Description                                                                                                                                         |
|-------|---------------------------|
| key   | The key to set new settings value, as an *integer*. This will be one of the following values : - **0 : INT_LOG_LEVEL** - **2 : PIXELFORMAT_FORMAT** |
| value | The new value for the property, as an *integer*.                                                                                                |
**Returns**

The value of the property.

#### boolean setValue (int key,boolean value)

This method sets the setting values for the properties of NexPlayer.

**Parameters**


| Name  | Description                                                                                    |
|-------|-------------------------|
| key   | The key to set new settings value, as an integer. Supported key value : 3: BOOL\_USE\_UDP |
| value | The new value for the property, in boolean.|

**Returns**

The value of the property.

#### boolean setValue (int key, CEARenderMode value)

This method sets the setting values for the properties of NexPlayer.


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

#### static native int initDRMManager (String strEngineLibName)

Initializes and registers the `SmoothStreamFragmentDRMManager`.

**Parameters**

| Name             | Description                                   |
|------------------|---------------------------|
| strEngineLibName | The relevant engine library name as a string. |

#### static native int initDRMManager (String strEngineLibName) *[static]*

Initializes and registers the `SmoothStreamPiffDRMManager`.

**Parameters**

| Name             | Description                                   |
|------------------|---------------------------|
| strEngineLibName | The relevant engine library name as a string. |

#### static native int initDRMManager (String strEngineLibName) *[static]*

Initializes and registers the `SmoothStreamPlayReadyDRMManager`.

**Parameters**

| Name             | Description                                   |
|------------------|---------------------------|
| strEngineLibName | The relevant engine library name as a string. |

### NexThumbnail.ThumbnailInformation Class Reference

**Public Member Functions**

- `int getThumbnailInfoWidth ()`
- `int getThumbnailInfoHeight ()`
- `int getThumbnailInfoPitch ()`
- `int getThumbnailInfoRatate ()`


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


