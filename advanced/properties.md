# Properties

There are a wide array of properties that can be adjusted to control the behavior of various aspects of the player. Properties are identified with an integer identifier from the NexProperty enumeration.

The value of each property is an unsigned integer. For some properties, it may be necessary to cast this to a different type. See the individual property documentation for details. If no type is specified, it is safe to treat the property as an unsigned integer.

To set a property, call setProperty on the NexPlayer instance. To get the current value of a property, call getProperty.

> **Note** Do not access or change undocumented properties, or your code may behave unpredictably and may break in future versions.

**Property Fine-Tuning Guidelines**

The default values for the properties should be acceptable for most common cases. However, in some cases, adjusting the properties will give better performance or better behavior.

**Fine-Tuning Buffering Time**

When dealing with streaming content, adjusting the buffer size can give smoother playback. For RTSP streaming, the recommended buffering time is between 3 and 5 seconds; for HTTP Live Streaming, the recommended buffering time is 8 seconds.

There are two settings for buffering time: the initial time (the first time data is buffered before playback starts) and the re-buffering time (if buffering is needed later, after playback has started). Both default to 5 seconds. For example, to set the buffering time to 8 seconds for HTTP Live Streaming:

```java
void setBufferingTime( NexPlayer hNexPlayer ) {
	mNexPlayer.setProperty(NexProperty.INITIAL_BUFFERING_DURATION, 8000);
	mNexPlayer.setProperty(NexProperty.RE_BUFFERING_DURATION, 8000);
}
```

**Numeric Property Identifiers**

Properties can also be identified by numeric value. This is how NexPlayer identifies properties internally, but in general, it is better to use this enum and the methods listed instead.

If you must work with the numeric property identifiers directly, you can retrieve them using the getPropertyCode method of a member of this enum, and the methods getProperties(int) and setProperties(int, int) can be used to get or set a property based on the numeric identifier.

 

### AV\_INIT_OPTION (46)

Controls when video initialization happens.

- **Type:** unsigned integer

- **Default:** AV\_INIT\_ALL

- **AV\_INIT\_PARTIAL (0x00000000):** If there is an audio track, wait for audio initialization to complete before initializing video.
- **AV\_INIT\_ALL (0x00000001):** Begin video initialization as soon as there is any video data, without any relation to the audio track status.


### CHECK_HTTP\_HEADER\_LENGTH (0x00060001)

Check the HTTP Request and Response headers length.

If this property is set, NexPlayer will check the HTTP request and response headers, and send them through `onHTTPRequest`and `onHTTPResponse`.

- **Type:** int

- **Default:** 0

- **Values:**

- **0:** Do not check the HTTP Request and Response headers length.
- **1:** Check the HTTP Request and Response headers length.

### DATA_INACTIVITY\_TIMEOUT (19)

The amount of time to wait for a server response before generating an error event.

If there is no response from the server for longer than the amount of time specified here, an error event will be generated and playback will stop.

Set this to zero to disable timeout (NexPlayer will wait indefinitely for a response).

- **Type:** unsigned integer

- **Unit:** msec (1/1000 sec)

- **Default:** 60000 (60 seconds)

### DATA_INACTIVITY\_TIMEOUT\_WARNING(135)

The amount of time to wait for a server response before generating an error(warning) event. If there is no response from the server for longer than the amount of time specified here, an error (actually warning) event will be generated but playback will continue to play until the time of DATA\_INACTIVITY\_TIMEOUT.

- **Type:** unsigned integer

- **Unit:** msec (1/1000 sec)

- **Default:** 50000 (50 seconds)

### ENABLE_DECODER\_SEAMLESS (571)

This sets whether or not to activate seamless playback when switching to another track.

- **Type:** int

- **Default:** 1

- **Values:**

- **0:** Disable seamless playback when switching to another track.
- **1:** Enable seamless playback when switching to another track.

### ENABLE_DETAIL\_ERROR (600)

Set it to get detail error through NexPlayer.getDetailedError.

For more information, NexPlayer.getDetailedError.

This property should be called after init but before calling open.

- **Type:** int

- **Default:** 0

- **Values:**

- **0:** not supporting detail error.
- **1:** supporting detail error.

### ENABLE_SUPPORT\_HTTP2 (904)

When this property is 1, all the request will be made over HTTP/2 protocol. By default HTTP/1.1 will be used.

- **Type:** integer
 
- **Default:** 0

### ENABLE_H264\_SEI (509)

Enables NexPlayer to deliver SEI (Supplemental Enhancement Information) in H.264 content to the application.

When this property is set equal to 1 (enabled) and H.264 content includes SEI, NexPlayer delivers SEI picture timing information through the onPictureTimingInfo method.

- **Type:** unsigned int

- **Default:** 0 (disabled)

- **Values:**

- **0:** Disabled. Ignores any available SEI.
- **1:** Enabled. Available SEI picture timing information will be delivered through the onPictureTimingInfo method.


### ENABLE_MODIFY\_HTTP\_REQUEST (512)

Enables NexPlayer to deliver an HTTP Request (to be used by NexPlayer) to the application.

When this property is set equal to 1 (enabled), NexPlayer delivers the HTTP Request to the onModifyHttpRequest listener on the application side.

- **Type:** boolean

- **Default:** 0

- **Values:**

- **0:** Disabled. Don’t deliver any HTTP Request.
- **1:** Enabled. Deliver HTTP Request to modify on the application side.


### ENABLE_TUNNELED\_PLAYBACK (601)

Set it to enable tunneled playback if the device supports tunneled playback.

If not supported, it will be is ignored. It can be used from Android os 5.0 and up.

This property should be called after init but before calling open.

- **Type:** int

- **Default:** 0

- **Values:**

- **0:** disable
- **1:** enable


 
### FIRST_DISPLAY\_VIDEOFRAME (60)

Controls what is displayed while the player is waiting for audio data.

If this is set to 1 (the default), the first video frame is displayed as soon as it has been decoded, and the player waits in a "freeze-frame" state until the audio starts, at which point both the audio and video play together.

If this is set to 0, the player will not display the first video frame until the audio is ready to play. Whatever was previously displayed will continue to be visible (typically a black frame).

Once audio has started, the behavior for both settings is the same; this only affects what is displayed while the player is waiting for audio data.

- **Type:** boolean

- **Default:** 1



### HTTP_CREDENTIAL (134)

Additional HTTP headers to use to supply credentials when a 401 response is received from the server.

The string should be in the form of zero or more HTTP headers (header name and value), and each header (including the last) should be terminated with a CRLF sequence, for example:

```"id: test1\r\npw: 12345\r\n"```

The particulars of the headers depend on the server and the authentication method being used.

- **Type:** String


### HTTP_FAILOVER\_DURATION (610)

Set the duration for retrying when **404 Not Found** or **403 Forbidden** HTTP status code occurred.

When getting **404 Not Found** or **403 Forbidden** HTTP status code while playing live content, NexPlayer will retry to connect during this value. If NexPlayer fails to connect during that time, NexPlayer will change to another track.

In this case, the failed track is temporarily disabled. The disabled track will enable after 5 and 10 minutes.

If set value is 0, the duration is set to the segment duration(#EXT-X-TARGETDURATION) of the content.

> **Warning** This is only for HLS Live content.
 
- **Type:** unsigned integer

- **Unit:** milliseconds

- **Default:** 0xFFFFFFFF

- **Values:**

- **= 0:** Retry only for the duration of segment (#EXT-X-TARGETDURATION).
- **> 0:** Retry only for the value(msec).



### LOCK\_END\_DATE (0x000A0002)

For limited-time versions of NexPlayer, this indicates the end date of the limited period of valid use.

Time locked versions of NexPlayer will only be valid and play content during the period defined by the properties `LOCK_START_DATE` and `LOCK_END_DATE`, and will otherwise return an error `PLAYER_ERROR_TIME_LOCKED`.

This property cannot be set independently but can only be retrieved by calling getStringProperty. This may be useful for informing users of the limited availability of the player they are using.

- **Type:** String

- **Default:** 0

### LOCK_START\_DATE (0x000A0001)

For limited time versions of NexPlayer, this indicates the start date of the limited period of valid use.

Time locked versions of NexPlayer will only be valid and play content during the period defined by the properties `LOCK_START_DATE` and `LOCK_END_DATE`, and will otherwise return an error `PLAYER_ERROR_TIME_LOCKED`.

This property cannot be set independently but can only be retrieved by calling getStringProperty. This may be useful for informing users of the limited availability of the player they are using.

- **Type:** String

- **Default:** 0

### LOG_LEVEL (35)

The logging level for the NexPlayer protocol module.

This affects the type of messages that are logged by the protocol module (it does not affect the logging level of other NexPlayer components).

- **Type:** unsigned integer

- **Default:** LOG\_LEVEL\_DEBUG

- **Values:**

- **LOG\_LEVEL\_NONE (0x00000000)** Don’t log anything (not currently supported).
- **LOG\_LEVEL\_DEBUG (0x00000001)** Log start, stop and errors (default for the debug version).
- **LOG\_LEVEL\_RTP (0x00000002)** Generate log entries relating to RTP packets.
- **LOG\_LEVEL\_RTCP (0x00000004)** Generate log entries relating to RTCP packets.
- **LOG\_LEVEL\_FRAME (0x00000008)** Log information about the frame buffer.
- **LOG\_LEVEL\_ALL (0x0000FFFF)** Log everything (not currently supported).

### MAX_H264\_PROFILE (118)

Limits the H.264 profile that can be selected from an HLS playlist.

Under normal operation, the track with the highest supported H.264 profile is selected from the playlist. If this property is set, no track with a profile higher than this value will be selected.

This should be set to zero for no limit.

- **Type:** unsigned integer

- **Default:** 0 (use any profile)



### OPEN_MEDIA\_FILE\_FROM\_SPECIFIED\_TS (513)

Allows NexPlayer to begin downloading content media files from a specified time stamp in the content.

 >**Warning** This property is currently only supported for VOD in HTTP Live Streaming (HLS).
 
NexPlayer allows users to start playback in the middle of a content file with the start api, but typically, before playback can begin, the player still opens content from the first media file available and then has to receive all of the media files between the first file and the point where the user would like to start playback.

When playback is to start in the middle of content, this property allows the player to skip receiving the unneeded earlier media files based on the time stamp value set by the application, and instead begin downloading media files from a position closer to the specified time stamp instead.

This property can thus reduce the time needed to open and start playing a media file in the middle of VOD content.

> **Note** This property must be set before NexPlayer.open is called.
 
- **Type:** unsigned integer

- **Unit:** msec (1/1000 s)

- **Default:** 0xFFFFFFFF

 
### PLAYABLE\_FOR\_NOT\_SUPPORT\_AUDIO\_CODEC (48)

If set to 0, it returns an error or generates an error event if the audio codec is not supported.

The default behavior (if this is 1) is to allow media playback even if the audio codec is not supported.

- **Type:** unsigned integer

- **Default:** 1


### PLAYABLE_FOR\_NOT\_SUPPORT\_VIDEO\_CODEC (49)

If set to 0, it returns an error or generates an error event if the video codec is not supported.

The default behavior (if this is 1) is to allow media playback even if the video codec is not supported.

- **Type:** unsigned integer

- **Default:** 1


 
### PROXY_ADDRESS (31)

Set the proxy address.

- **Type:** String

- **Default:** null

### PROXY_PORT (32)

Set the proxy port number.

- **Type:** integer

- **Default:** 0


### SEEK_RANGE\_FROM\_RA\_POINT (102)

Sets the range where NexPlayer will seek to a Random Access point rather than the exact target position provided in the seek API.

> **Warning** This property is only valid when the first parameter, exact, in the seek API is true.
 
Setting this value is a kind of option for the seek API and can be used to minimize the time required to seek in content by taking advantage of Random Access points in the content.

A Random Access point is a specific position that the parser is allowed to seek to directly.

This value sets the range where NexPlayer will seek from a Random Access point given by the parser to a target position that equals msec (milliseconds), the first parameter in the seek() API.

If the exact parameter, the second parameter in the seek API, is true and the difference between a Random Access point and the target position is within this value, seek will find and seek to the exact target position. If the exact parameter is set to true and the difference between a Random Access point and the target position is beyond this range, seek will give up the accurate target point and will instead seek to and play from the Random Access point.

For example, if NexPlayer is seeking to 10000 ms exactly (exact=true) and there is a Random Access point at 7000 ms, if this property is set to less than 3000 ms, the player will ignore the exact target value and will instead play from 7000 ms. On the other hand, if this property is set to more than 3000 ms, then NexPlayer will seek exactly to 10000 ms and begin playback.

> **Warning** Please remember that in order to seek to a target position, audio or video frames have to be decoded. If too large of a value is set here, it may cause the seek process to consume an excessive amount of time especially in high resolution video content.
 
- **Type:** unsigned integer

- **Unit:** msec (1/1000 sec)

- **Default:** 10000 (10 seconds)


 
### SEGMENT_TS\_RELIABLE (570)

Sets whether or not to trust a content segment’s timestamp when playback starts.

This property should be called after init but before calling open.

- **Type:** int

- **Default:** 1

- **Values:**

- **0:** Adjust the timestamp during playback.
- **1:** Trust the timestamp during playback.


 
### SEND_ALL\_DASH\_MPD\_EVENTS (605)

Set it to decide which events passed through `onDashScte35Event` listener.

This property should be called after init but before calling open.

- **Type:** int

- **Default:** 0

- **Values:**

- **0:** Only scte35 events will be passed through onDashScte35Event listener.
- **1:** All the events in the MPD will be passed through onDashScte35Event listener.



### SET_COOKIE (500)

Controls whether or not the player honors cookies sent by the server.

- **Type:** unsigned integer

- **Default:** 1

- **Values:**

- **0:** Ignore HTTP cookie headers sent by the server.
- **1:** Cookie headers received from a streaming server along with the initial manifest or playlist are included with further HTTP requests during the session.


### SET_NOTVENDOR_CODEC (905)

When this property is enabled the player will disregard the default vendor codec.

- **Type:** Boolean

- **Default:** 0

- **Values:**

- **0:** uses the default vendor codec.
- **1:** enables the not vendor codec. (e.g c2.android.avc.codec)



### SET_REFERENCE\_SERVER\_UTC (596)

Set reference server utc for SPD.

This property should be set before calling open. The value is string of Unix epoch time in miliseconds e.g. "1602555563000" is Tuesday, October 19:23 AM (GMT).

If the value is less than availability start time in MPD, media not found will occur. If difference between reference server utc and device time is greater than a day, it will be.

**Type** String

**Unit** msec (1/1000 sec) 

- **Default**: null



 
### SET_TO\_SKIP\_BFRAME (103)

If set to true, unconditionally skips all B-frames without decoding them; not currently supported.

- **Type:** boolean

- **Default:** 0



### SOCKET_CONNECTION\_TIMEOUT (20)

The amount of time to wait before timing out when establishing a connection to the server.

If the connection to the server (the socket connection) cannot be established within the specified time, an error event will be generated and playback will not start.

Set this to zero to disable timeout (NexPlayer will wait indefinitely for a connection).

- **Type:** unsigned integer

- **Unit:** msec (1/1000 sec)

- **Default:** 30000 (30 seconds)


### SOCKET_OPERATION\_TIMEOUT (73)

The maximum waiting time for an HTTP request/response message to be sent to NexPlayer.

The maximum waiting time for an HTTP request/response message after it is sent to the streaming server. If the reply does not arrive within this time, it will be regarded as an error.

- **Type:** unsigned integer

- **Unit:** msec (1/1000 sec)

- **Default:** 30,000 (30 seconds)

### SOURCE_OPEN\_TIMEOUT (63)

Sets the amount of time to wait for an open request to complete.

This is used when NexPlayer tries to open new media. If there is no response from the server for longer than the amount of time specified here, the open request will be stopped and onAsyncCmdComplete will be called with the result, namely the error code, `NexErrorCode.SOURCE_OPEN_TIMEOUT`.

- **Type:** unsigned integer

- **Unit:** msec (1/1000 sec)

- **Default:** 300000 (300 seconds)



### SPEED\_CONTROL\_AVAILABILITY (0x00050001)

Indicates whether or not speed control is available on this device.

As audio solution components are optional, this property can be checked for availability.

This is useful to determine whether to display the speed control in the user interface.

- **Type:** unsigned integer(read-only)

- **Values:**

- **0:** Device does not support speed control.
- **1:** Device supports speed control.



### SUPPORT_EYE\_PLEASER (50)

This property enables the Eye Pleaser feature.

If the decoding or display of video frames takes too long, it may be necessary to skip some frames in order to maintain a normal rate of playback. Under normal operation, frames are skipped immediately to catch up. When Eye Pleaser is enabled, skipped frames are spread out to try to make playback appear smoother.

- **Type:** integer

- **Default:** 1

- **Values:**

- **0:** Normal operation (frames are skipped immediately).
- **1:** Eye Pleaser enabled (skipped frames are spread out).




 
### TIMESTAMP_DIFFERENCE\_VDISP\_SKIP (14)

The number of milliseconds that video is allowed to run behind audio before the system begins skipping frames to maintain synchronization.

For example, 70 means that if the current video time is more than 70ms behind the audio time, the current video frame will be skipped. This is used to adjust video and audio synchronization.
 
- **Type:** unsigned integer

- **Unit:** ms (1/1000s)

- **Default:** 70 (0.07s)

### TIMESTAMP_DIFFERENCE\_VDISP\_WAIT (13)

The number of milliseconds (as a negative number) that video is allowed to run ahead of audio before the system waits for audio to catch up.

For example, -50 means that if the current video time is more than 50 msec ahead of the audio time, the current video frame will not be displayed until the audio catches up to the same time stamp. This is used to adjust video and audio synchronization.
 
- **Type:** integer (should be negative)

- **Unit:** ms (1/1000s)

- **Default:** -50 (50ms)


### USERAGENT_STRING (58)

RTSP/HTTP User Agent value.

- **Type:** String

- **Default:** "User-Agent: Mozilla/5.0 (iPhone; U; CPU iPhone OS 3\_1\_2 like Mac OS X; ko-kr) AppleWebKit/528.18 (KHTML, like Gecko) Version/4.0 Mobile/7D11 Safari/528.16"

### SET_SSL\_CERTIFICATE\_VERIFICATION (908)

NexPlayer ignores any SSL error by default and keeps playing the content. By enabling this property, NexPlayer will throw an error when there is an error during the SSL handshake.

- **Type:** integer

- **Default:** 0

> Since version 6.72.0.857

### SET_FALLBACK\_URL (909)

Sets a fallback url for DASH contents and switches to this given backup URL seamlessly when there is a network error.

- **Type:** String

- **Default:** null

> Since version 6.72.0.858

### SUPPORT_EXTERNAL\_PCM

NexPlayer is able to expose audio PCM data to application side for any post audio processing. You can process the audio data on the application side and return back to the NexPlayer SDK to apply any audio modification you would like to introduce. When this property is enabled following event will be generated in `NexEventReceiver`:

```java
@Override
public byte[] onHandlingExternalPCM(NexPlayer mp, int ts, Object ob) {
   byte[] pkt = (byte[]) ob;
   int timestamp = ts;
	//Process the audio data here
   return pkt;
}
```

- **Type:** integer

- **Default:** 0

> Since version 6.72.0.857