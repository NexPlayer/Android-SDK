# Properties

There are a wide array of properties that can be adjusted to control the behavior of various aspects of the player, from buffer time (how many seconds of streaming content are buffered before playback begins) to the behavior of the player under various error conditions (whether or not to allow audio-only playback if an unsupported video codec is detected, for example).

Properties are identified with an integer identifier from the NexProperty enumeration.

The value of each property is an unsigned integer. For some properties, it may be necessary to cast this to a different type. See the individual property documentation for details. If no type is specified, it is safe to treat the property as an unsigned integer.

To set a property, call setProperty on the NexPlayer instance. To get the current value of a property, call getProperty.

> **Note** Members of the enumeration that have not been documented, as well as values that have not yet been used are subject to change in future versions. Do not access or change undocumented properties, or your code may behave unpredictably and may break in future versions.

**Property Fine-Tuning Guidelines**

The default values for the properties should be acceptable for most common cases. However, in some cases,
adjusting the properties will give better performance or better behavior.

**Fine-Tuning Buffering Time**

When dealing with streaming content, adjusting the buffer size can give smoother playback. For RTSP streaming, the recommended buffering time is between 3 and 5 seconds; for HTTP Live Streaming, the recommended buffering time is 8 seconds.

There are two settings for buffering time: the initial time (the first time data is buffered before playback starts) and the re-buffering time (if buffering is needed later, after playback has started). Both default to 5 seconds. For example, to set the buffering time to 8 seconds for HTTP Live Streaming:

```java
void setBufferingTime( NexPlayer hNexPlayer ) {
	hNexPlayer.setProperty(NexProperty.INITIAL_BUFFERING_DURATION, 8000);
	hNexPlayer.setProperty(NexProperty.RE_BUFFERING_DURATION, 8000);
}
```

**Numeric Property Identifiers**

Properties can also be identified by numeric value. This is how NexPlayer identifies properties internally, but in general, it is better to use this enum and the methods listed above instead.

If you must work with the numeric property identifiers directly, you can retrieve them using the getPropertyCode method of a member of this enum, and the methods getProperties(int) and setProperties(int, int) can be used to get or set a property based on the numeric identifier.

**int getPropertyCode ()**

Gets the integer code for the NexPlayer property.

**Returns**

The integer code for the specified property.

### ALWAYS_BUFFERING (120)

This is used to force NexPlayer to begin buffering as soon as all available audio frames have been processed, without regard to the state of the video buffer.

Under normal operation, when there are no audio frames left in the audio buffer, NexPlayer switches to buffering mode and temporarily suspends playback.

There is an exception if the video buffer is more than 60% full. In this case, NexPlayer will continue video playback even if there is no more audio available.

Setting this property totrue(1) bypasses this exception and forces the system to go to buffering immediately if there are no audio frames left to play.

**Type:** boolean

**Default:** 0

> **Warning** This property is not supported in this API version.
 
### APPLS_FORCESTART\_AVTRACK (198)

This sets whether or not NexPlayer should select a higher track if the first track is Audio only.

If the first track is audio only in HLS, a higher track will be selected.

**Type:** boolean

**Default:** 0

**Values:**

- **0:** Do not select a higher track.
- **1:** Select a higher track.

> **Note** This property must be set before NexPlayer.open is called.
  
### AS_CINEMA\_SOUND\_AVAILABILITY (0x00050006)

Indicates whether or not the NexSound audio solution component, Cinema Sound, is available on this device.

As audio solution components are optional, this property can be checked for availability.

**Type:** unsigned integer(read-only)

**Values:**

- **0:** Device does not support Cinema Sound component.
- **1:** Device supports Cinema Sound component.

### AS_EARCOMFORT\_AVAILABILITY (0x00050002)

Indicates whether or not the NexSound audio solution component, EarComfort, is available on this device.

As audio solution components are optional, this property can be checked for availability.

**Type:** unsigned integer(read-only)

**Values:**

- **0:** Device does not support EarComfort component.
- **1:** Device supports EarComfort component.

### AS_MUSIC\_ENHANCER\_AVAILABILITY (0x00050005)

Indicates whether or not the NexSound audio solution component, Music Enhancer, is available on this device.

As audio solution components are optional, this property can be checked for availability.

**Type:** unsigned integer(read-only)

**Values:**

- **0:** Device does not support Music Enhancer component.
- **1:** Device supports Music Enhancer component.

### AS_REVERB\_AVAILABILITY (0x00050003)

Indicates whether or not the NexSound audio solution component, Reverb, is available on this device.

As audio solution components are optional, this property can be checked for availability.

**Type:** unsigned integer(read-only)

**Values:**

- **0:** Device does not support Reverb component.
- **1:** Device supports Reverb component.

### AS_STEREO\_CHORUS\_AVAILABILITY (0x00050004)

Indicates whether or not the NexSound audio solution component, Stereo Chorus, is available on this device.

As audio solution components are optional, this property can be checked for availability.

**Type:** unsigned integer(read-only)

**Values:**

- **0:** Device does not support Stereo Chorus component.
- **1:** Device supports Stereo Chorus component.

### AV\_INIT_OPTION (46)

Controls when video initialization happens.

This can be any of the following values:

- **AV\_INIT\_PARTIAL (0x00000000)**
    If there is an audio track, wait for audio initialization to complete before initializing video.
- **AV\_INIT\_ALL (0x00000001)**
    Begin video initialization as soon as there is any video data, without any relation to the audio track status.

**Type:** unsigned integer

**Default:** AV\_INIT\_ALL

#### AV_INIT\_PARTIAL 0x00000000 

This is a possible setting for the AV\_INIT\_OPTION property; see that property for details.

#### AV\_INIT_ALL 0x00000001

This is a possible setting for the AV\_INIT\_OPTION property; see that property for details.

### AV_SYNC\_OFFSET (124)

Adjusts A/V synchronization by ofsetting video relative to audio.

Positive values cause the video to play faster than the audio, while negative values cause the audio to play faster than the video. Under normal operation, this can be set to zero, but in some cases where the synchronization is bad in the original content, this can be used to correct for the error.

While A/V synchronization is generally optimized internally by NexPlayer , there may occasionally be devices which need to be offset in order to improve overall A/V synchronization. For examples of how to set AV\_SET\_OFFSET based on the device in use, please see the Sample Application code as well as the introductory section A/V Synchronization section.

Appropriate values for any other problematic devices need to be determined experimentally by testing manually.

**Type:** integer

**Unit:** msec (1/1000 sec)

**Range:** -2000∼+2000

**Default:** 0

### CAPTION_WAITOPEN (540)

Avoids waiting for the first Caption segment to download when starting to play content.

This property can be used when playing Caption content. By default, NexPlayer waits until the first Caption segment is downloaded before content begins to play so that no caption text will be missed.

However, if this property is disabled (set to 0), the player will start playing content as soon as possible (instead of waiting until the first Caption segment is fully downloaded). This may be preferred if content should start playing as quickly as possible (although initial Caption may be missed).

This property should be called once, immediately after calling init but before calling open.

**Type:** boolean

**Default:** 1

**Values:**

- **0:** Content starts playing before first Caption segment is downloaded.
- **1:** Content starts playing after first Caption segment is downloaded.
 
### CHECK_HTTP\_HEADER\_LENGTH (0x00060001)

Check the HTTP Request and Response headers length.

If this property is set, NexPlayer will check the HTTP request and response headers, and send them through `onHTTPRequestandonHTTPResponse`.

**Type:** int

**Default:** 0

**Values:**

- **0:** Do not check the HTTP Request and Response headers length.
- **1:** Check the HTTP Request and Response headers length.

**See Also**
 
- NexPlayer.onHTTPRequest
- NexPlayer.onHTTPResponse
 
### CONTINUE_DOWNLOAD\_AT\_PAUSE (561)

Sets whether or not to continue downloading data in pause state when playing content.

When this property is set, content data will continue to be downloaded even when NexPlayer;™ is paused.

This property should be called after init and before calling open.

**Type:** int

**Default:** 0

**Values:**

- **0:** Stop downloading in pause state.
- **1:** Continue downloading in pause state.
 
### DATA_INACTIVITY\_TIMEOUT (19)

The amount of time to wait for a server response before generating an error event.

If there is no response from the server for longer than the amount of time specified here, an error event will be generated and playback will stop.

Set this to zero to disable timeout (NexPlayer will wait indefinitely for a response).

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 60000 (60 seconds)

### DOWNLOADER_HTTP\_HEADER (0x00090002)

This property adds additional header fields to be sent along with the HTTP headers when sending streaming requests (HLS and Smooth Streaming) from the Downloader module.

This property should be set before the Downloader module is opened by DownloaderOpen().

**Type:** String

### DOWNLOADER_USERAGENT\_STRING (0x00090001)

An RTSP/HTTP User Agent value associated with the Downloader module.

This property should be set before the Downloader module is opened.

**Type:** String

### ENABLE_AUDIOONLY\_TRACK (556)

Sets whether to enable or disable the Audio Only track in HLS content.

This property should be called after init but before calling open.

**Type:** int

**Default:** 1

**Values:**

- **0:** Audio Only track disabled.
- **1:** Audio Only track enabled.
 
### ENABLE_CEA708 (517)

Enables rendering and display of CEA 708 closed captions in content when available.

While CEA 608 closed captions are always enabled, it is necessary to set this property to 1 in order for NexPlayer to support CEA 708 closed captions.

In the case where content contains both CEA 608 and CEA 708 closed captions and this property enables CEA 708 closed captions, the application will have to handle choosing which captions to render and display to the user.

**Type:** boolean **Default:** 0 **Values:**

- **0:** CEA 708 closed captions disabled.
- **1:** CEA 708 closed captions enabled.

**See Also**
 
- NexEIA708CaptionView
- NexEIA708Struct
 
### ENABLE_DECODER\_SEAMLESS (571)

This sets whether or not to activate seamless playback when switching to another track.

It can be used from Android os 4.4 and up.

**Type:** int

**Default:** 1

**Values:**

- **0:** Disable seamless playback when switching to another track.
- **1:** Enable seamless playback when switching to another track.
 
### ENABLE_DETAIL\_ERROR (600)

Set it to get detail error through NexPlayer.getDetailedError.

For more information, NexPlayer.getDetailedError.

This property should be called after init but before calling open.

**Type:** int

**Default:** 0

**Values:**

- **0:** not supporting detail error.
- **1:** supporting detail error.
 
### ENABLE_FRAMERATE\_RESTRICTION (588)

This makes sure that the currently playing track is not switched to another one with a lower frame rate when switching to a track with a higher Bitrate.

**Type:** int

**Default:** 0

**Values:**

- **0:** Disable the frame rate restriction.
- **1:** Enable the frame rate restriction.
 
### ENABLE_H264\_SEI (509)

Enables NexPlayer to deliver SEI (Supplemental Enhancement Information) in H.264 content to the application.

When this property is set equal to 1 (enabled) and H.264 content includes SEI, NexPlayer delivers SEI picturetiming information through the onPictureTimingInfo method.

**Type:** unsigned int

**Values:**

- 0 : Disabled. Ignores any available SEI.
- 1 : Enabled. Available SEI picture timing information will be delivered through the onPictureTimingInfo method.

**Default:** 0 (disabled)

**See Also**

onPictureTimingInfo and NexPictureTimingInfo for more information.
 
### ENABLE_HTTPABRTRACKCHANGE\_CALLBACK (583)

Indicates whether or not an ABR track switch callback is available.

**Type:** int

**Default:** 0

**Values:**

- **0:** Disable an ABR track switch callback.
- **1:** Enable an ABR track switch callback.

### ENABLE_ID3\_TTML (522)

Sets whether or not to display TTML text tracks in ID3 tags automatically when they are included in content.

In the case, when both CEA closed captions and TTML text tracks in ID3 tags are included in content, this property can be used to set whether to display the TTML text tracks in ID3 tags or the closed captions automatically.

By default, this property is set to 0 to disable TTML text tracks in ID3 tags automatically if they exist in content (as was the behavior of NexPlayer previously). If for some reason it would be preferable that TTML captions in ID3 tag be displayed instead of the CEA closed captions text tracks, this property should be set to 1 using setProperty:

```java
mNexPlayer.setProperty(NexProperty.ENABLE_ID3_TTML, 1);
```

This property should only be called once, after calling init but before calling open.

**Warning**

 
Do not use with PARTIAL\_PREFETCH.
 
**Type:** boolean

**Values:**

- 0 : TTML text tracks in ID3 tags ignored; CEA closed captions enabled
- 1 : TTML text tracks in ID3 tags enabled; CEA closed captions ignored

**Default:** 0
 
### ENABLE_MODIFY\_HTTP\_REQUEST (512)

Enables NexPlayer to deliver an HTTP Request (to be used by NexPlayer) to the application.

When this property is set equal to 1 (enabled), NexPlayer delivers the HTTP Request that NexPlayer will use to the application.

This property is related to the onModifyHttpRequest method. For more information on how to modify HTTP
requests, please see the introductory section Enabling Modified HTTP Requests.

**Type:** boolean

**Default:** 0

**Values:**

- 0 : Disabled. Don’t deliver any HTTP Request.
- 1 : Enabled. Deliver HTTP Request to modify on the application side.

**See Also**
 
NexPlayer.IListener.onModifyHttpRequest
 
### ENABLE_SPD\_SYNC\_TO\_DEVICE\_TIME (594)

Enables synchronization to device UTC (SPD).

**Type:** int

**Default:** 0

**Values:**

- **0:** Disabled device UTC
- **1:** Enabled device UTC


### ENABLE_SPD\_SYNC\_TO\_GLOBAL\_TIME (591)

Enables synchronization to UTC time(SPD).

**Type:** int

**Default:** 0

**Values:**

- **0:** SPD disabled.
- **1:** SPD enabled.

### SET_REFERENCE\_SERVER\_UTC (596)

Set reference server utc for SPD.

This property should be set before calling open. The value is string of Unix epoch time in miliseconds e.g. "1602555563000" is Tuesday, October 19:23 AM (GMT).

If the value is less than availability start time in MPD, media not found will occur. If difference between reference server utc and device time is greater than a day, it will be 

**Type** String

**Unit** msec (1/1000 sec) 

**Default**: null

 
### ENABLE_TRACKDOWN (131)

Allows NexPlayer to switch to a lower bandwidth track if the resolution or bitrate of the current track is too high for the device to play smoothly.

Under normal operation, NexPlayer switches tracks based solely on current network conditions. When this property is enabled, NexPlayer will also switch to a lower bandwith track if too many frames are skipped during playback.

This is useful for content that is targeted for a variety of devices, some of which may not be powerful enough to handle the higher quality streams.

The `TRACKDOWN_VIDEO_RATIO` property controls the threshold at which the track change will occur, if frames
are being skipped.

**Type:** boolean

**Default:** 0

**Values:**

- 0: Normal behavior (switch based on network conditions only)
- 1: Switch based on network conditions and device performance.

### ENABLE_TUNNELED\_PLAYBACK (601)

Set it to enable tunneled playback if the device supports tunneled playback.

If not supported, it will be is ignored. It can be used from Android os 5.0 and up.

This property should be called after init but before calling open.

**Type:** int

**Default:** 0

**Values:**

- **0:** disable
- **1:** enable


### ENABLE_WEBVTT (518)

Sets whether or not to display WebVTT text tracks automatically when they are included in content.

In the case when both CEA 708 closed captions and WebVTT text tracks are included in content, this property can be used to set whether to display the WebVTT text tracks or the closed captions automatically.

By default, this property is set to 1 to enable WebVTT text tracks automatically if they exist in content (as was the behavior of NexPlayer previously). If for some reason it would be preferable that CEA 708 closed captions be displayed instead of the WebVTT text tracks, this property should be set to 0 with by with setProperty:

```java
mNexPlayer.setProperty(NexProperty.ENABLE\_WEBVTT, 0);
```

This property should only be called once, immediately after calling init but before calling open.

**Type:** boolean

**Values:**

- 0 : WebVTT text tracks ignored; CEA 708 closed captions enabled
- 1 : WebVTT text tracks enabled; CEA 708 closed captions ignored

**Default:** 1 (WebVTT text tracks enabled)
 
### ENHANCED_SOUND\_AVAILABILITY (0x00050008)

Indicates whether or not the NexSound audio solution, speed control component, DTS audio solution headphoneX, and head tracking are available on this device.

As audio solutions components are optional in the NexPlayer SDK, this property can be used to checked their availability.

When this property is set equal to 1 (enabled), NexPlayer uses NexSound audio solution and speed control.

When this property is set equal to 2 (enabled), NexPlayer uses DTS audio solution and headphone X. When this property is set equal to 4 (enabled), NexPlayer uses DTS audio solution and head tracking.

This property is related to the `notifyHeadsetState` method.

**Type:** unsigned integer

**Default:** 0 (Disabled/Not Available)

**Values:**

- **0:** Disabled/Not Available. NexPlayer does not support any other sound effects.
- **1:** NexSound Speed Control/Available. NexPlayer supports NexSound audio solution and speed control.
- **2:** DTS Headphone X/Available. NexPlayer supports DTS audio solution and headphone X.
- **4:** DTS Head Tracking/Available. NexPlayer supports DTS audio solution and head tracking.

**See Also**
 
NexPlayer.notifyHeadsetState
 
### FIRST_DISPLAY\_VIDEOFRAME (60)

Controls what is displayed while the player is waiting for audio data.

If this is set to 1 (the default), the first video frame is displayed as soon as it has been decoded, and the player waits in a "freeze-frame" state until the audio starts, at which point both the audio and video play together.

If this is set to 0, the player will not display the first video frame until the audio is ready to play. Whatever was previously displayed will continue to be visible (typically a black frame).

Once audio has started, the behavior for both settings is the same; this only affects what is displayed while the player is waiting for audio data.

Under old versions of the SDK (prior to the addition of this property) the default behavior was as though this property were set to zero.

**Type:** boolean

**Default:** 1

### HLS_RUNMODE (133)

Controls the algorithm used for bitrate switching when playing an HLS stream.

**Type:** unsigned integer

**Default:** 0

**Values:**

- **0:** Use a more aggressive algorithm: up-switching happens sooner.
- **1:** Use a more conservative algorithm: up-switching happens only if a significant amount of extra bandwidth is available beyond that required to support the given bitrate. This is similar to the iPhone algorithm.

### HTTP_CREDENTIAL (134)

Additional HTTP headers to use to supply credentials when a 401 response is received from the server.

The string should be in the form of zero or more HTTP headers (header name and value), and each header
(including the last) should be terminated with a CRLF sequence, for example:

"id: test1\r\npw: 12345\r\n"

The particulars of the headers depend on the server and the authentication method being used.

**Type:** String

### HTTP_FAILOVER\_DURATION (610)

Set the duration for retrying when **404 Not Found** or **403 Forbidden** HTTP status code occurred.

When getting **404 Not Found** or **403 Forbidden** HTTP status code while playing live content, NexPlayer will retry to connect during this value. If NexPlayer fails to connect during that time, NexPlayer will change to another track.

In this case, the failed track is temporarily disabled. The disabled track will enable after 5 and 10 minutes.

If set value is 0, the duration is set to the segment duration(#EXT-X-TARGETDURATION) of the content.

> **Warning** This is only for HLS Live content.
 
**Type:** unsigned integer

**Unit:** milliseconds

**Default:** 0xFFFFFFFF

**Values:**

- **0:** Retry only for the duration of segment(#EXT-X-TARGETDURATION).
- **Above 0:** Retry only for the value(msec).
 
### IGNORE_ABNORMAL\_SEGMENT\_TIMESTAMP (508)

Ignores abnormal segment timestamps.

If it is 1 or enabled, NexPlayer will ignore abnormal segment timestamps. If it is 0 or disabled, NexPlayer will not ignore any abnormal segment timestamps.

**Type:** boolean

> **Warning** This property is not supported in this API version.
 
### IGNORE_AUDIO\_LOST\_FRAME (119)

If set to 1, lost audio frames are always ignored (silence is never inserted).

See `TOO_MUCH_LOSTFRAME_DURATION` for details about the insertion of silence for lost audio frames.

**Type:** boolean

**Default:** 0

> **Warning** This property is not supported in this API version.
 
### IGNORE_AV\_SYNC (121)

Whentrue(1), this property causes audio/video synchronization to be bypassed; not currently supported.

In this state, audio and video are played back independently as soon as data is received.

This property can be enabled if audio and video synchronization are not important, and if real-time behavior is needed between the server and the client.

In normal cases, this shouldnotbe used (it should be set to zero) because it will cause video and audio to quickly lose synchronization for most normal media streams.

**Type:** boolean

**Default:** 0

> **Warning** This property is not supported in this API version.
 
### IGNORE_CARRIAGERETURN\_WHEN\_RECEIVE\_ROLLUP (511)

Ignores the Roll Up (RU) column reset command in CEA 608 closed captions.

Because CEA 608 closed captions support the Roll Up (RU) mode, the player starts displaying captions "rolling up" the screen after receiving the Roll Up(RU) command.

The RU command can however have two meanings according to the specifications. One indicates the start of Roll Up mode. The other indicates that the line should be erased and the prompt(cursor) moved to the left hand edge of the display (to prepare for a new caption).

In the event that some content contains many extra RU commands in the stream, captions may not be displayed
properly because they will not be displayed fully and will be continuouly erased from the screen.

If this property is enabled, NexPlayer will ignore those extra RU column reset commands and thus will not erase the affected line or move the cursor.

**Type:** unsigned int

**Default:** 0

**Values:**

- 0 : Disabled. CEA 608 closed captions will be displayed according to the specifications.

- 1 : Enabled. Roll Up column reset commands in CEA 608 closed captions will be skipped.

### IGNORE_CEA608\_TEXTMODE\_COMMAND (514)

Allows NexPlayer to ignore thetext modecommand in CEA608 closed captions.

This property may be useful in cases where CEA 608 closed captions have been implemented in ways other than strictly following the standard specifications which include extratext modecommands. It allows NexPlayer to properly display those alternatively implemented captions in video content.

In content that includes standard CEA 608 closed captions that follow the specifications, enabling this property may result in captions that do not appear as expected, so use of this property is discouraged in those cases as NexPlayer will properly display CEA 608 closed captions according to the specifications.
 
**Type:** unsigned integer

**Default:** 0

**Values:**

- **0:** Disabled. NexPlayer will display CEA 608 closed captions according to the specifications.
- **1:** Enabled. NexPlayer will ignore thetext modecommand when displaying CEA 608 closed captions.
 
### INITIAL_BUFFERING\_DURATION (9)

The number of milliseconds of media to buffer initially before beginning streaming playback (HLS, RTSP, etc.).

This is the initial amount of audio and video that NexPlayer buffers when it begins playback. To set this property separately, it must be set by calling setPropertyaftercalling open() and before start() is called.

If further buffering is required later in the playback process, the value of the property `RE_BUFFERING_DURATION` will be used instead.

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 5000 (5 seconds)

### LIVE_OFFSET\_SEGMENT\_COUNT (54)

Specifies the segment offset when starting playback.

This property may have different meaning depending on the LIVE\_VIEW\_OPTION.

If `LIVE_VIEW_OPTION` is set to `LIVE_VIEW_RECENT`, then this property specifies the offset of segment from the live edge when starting playback. For example; 

- 1: The player will select the last segment in the manifest. 
- 2: The player will select the second last segment in the manifest. 
- 3: The player will select the third last segment in the manifest. If this property is set to 0, the player will select the segment depending on its policy.

This property is not currently defined for other `LIVE_VIEW_OPTION`.

**Type:** integer

**Default:** 0

### LIVE_OFFSET\_TIME (76)

Specifies the segment offset in time when starting playback.

This property may have different meaning depending on the LIVE\_VIEW\_OPTION. This property has higher priority than `LIVE_OFFSET_SEGMENT_COUNT`. If `LIVE_VIEW_OPTION` is set to `LIVE_VIEW_RECENT`, then this property specifies the time offset of segment from the live edge when starting playback. For example, if the duration of each segment is 6 seconds:

**1** ∼ **6000:** The player will select the last segment in the manifest.

**6001** ∼ **12000:** The player will select the second last segment in the manifest.

**12001** ∼ **18000:** The player will select the third last segment in the manifest.

If this property is set to 0, the player will select the segment depending on its policy.

This property is not currently defined for other `LIVE_VIEW_OPTION`.

**Type:** integer

**Unit:** msec (1/1000 sec)

**Default:** 0


### LIVE_VIEW\_OPTION (53)

Live HLS playback option.

This must be one of the following values:

- **LIVE_VIEW\_RECENT (0x00000000)** Start playback from the most recently received media segment (.ts) files of the HLS live playlist. For example, if 5.ts is the latest media segment (.ts) , playback will begin at the beginning of that segment.

- **LIVE_VIEW\_RECENT\_BYTARGETDUR (0x00000001)** Start playback from the most recently received media segement (.ts) files, based on the value set for the EXT-X-TARGETDURATION tag in the HLS live playlist. (The player will begin playback at the media segment that is immediately precedes the media segment that is three times (x3) the target durationbefore the latest media segment file loaded.) As a concrete example, if the target duration is set to 12 seconds and the total duration of currently loaded media segments is 48 seconds, playback will begin at the media file that immediately precedes the media segment with the timestamp at 12 (48-36) seconds. If this example HLS playlist includes media segment files 1.ts (duration of 10 seconds), 2.ts (9 sec), 3.ts (11 sec), 4.ts (10 sec), and 5.ts (8 sec), then playback will begin at the first media segment, 1.ts, because it immediate precedes the 2.ts segment (where the timestamp at 12 seconds occurs).

- **LIVE_VIEW\_FIRST (0x00000002)** Unconditionally start HLS playback from the first entry in the HLS playlist.

- **LIVE_VIEW\_LOW\_LATENCY (0x00000003)** Playback starts from a position close to real-time and frame skipping may occur during playback to maintain low latency.

**Type:** unsigned integer

**Default:** LIVE\_VIEW\_RECENT

#### LIVE\_VIEW\_RECENT 0x00000000 

This is a possible setting for the `LIVE_VIEW_OPTION` property; see that property for details.

#### LIVE\_VIEW\_RECENT\_BYTARGETDUR 0x00000001 

This is a possible setting for the `LIVE_VIEW_OPTION` property; see that property for details.

#### LIVE_VIEW\_FIRST 0x00000002 

This is a possible setting for the `LIVE_VIEW_OPTION` property; see that property for details.

#### LIVE_VIEW\_LOW\_LATENCY 0x00000003 

This is a possible setting for the `LIVE_VIEW_OPTION` property; see that property for details.

### LOCK\_END\_DATE (0x000A0002)

For limited time versions of NexPlayer, this indicates the end date of the limited period of valid use.

Time locked versions of NexPlayer will only be valid and play content during the period defined by the properties `LOCK_START_DATE` and `LOCK_END_DATE`, and will otherwise return an error `PLAYER_ERROR_TIME_LOCKED`.

This property cannot be set independently but can only be retrieved by calling getStringProperty. This may be useful for informing users of the limited availability of the player they are using.

**Type:** String

**Default:** 0

### LOCK_START\_DATE (0x000A0001)

For limited time versions of NexPlayer, this indicates the start date of the limited period of valid use.

Time locked versions of NexPlayer will only be valid and play content during the period defined by the properties `LOCK_START_DATE` and `LOCK_END_DATE`, and will otherwise return an error `PLAYER_ERROR_TIME_LOCKED`.

This property cannot be set independently but can only be retrieved by calling getStringProperty. This may be useful for informing users of the limited availability of the player they are using.

**Type:** String

**Default:** 0
 
### LOG_LEVEL (35)

The logging level for the NexPlayer protocol module.

This affects the type of messages that are logged by the protocol module (it does not affect the logging level of other NexPlayer components).

This value is made by or-ing together zero or more of the following values:

- **LOG\_LEVEL\_NONE (0x00000000)** Don’t log anything(not currently supported)
- **LOG\_LEVEL\_DEBUG (0x00000001)** Log start, stop and errors (default for the debug version)
- **LOG\_LEVEL\_RTP (0x00000002)** Generate log entries relating to RTP packets
- **LOG\_LEVEL\_RTCP (0x00000004)** Generate log entries relating to RTCP packets
- **LOG\_LEVEL\_FRAME (0x00000008)** Log information about the frame buffer
- **LOG\_LEVEL\_ALL (0x0000FFFF)** Log everything(not currently supported)

**Type:** unsigned integer

**Default:** LOG\_LEVEL\_DEBUG

#### LOG_LEVEL\_ALL = 0x0000FFFF 

This is a possible setting for the LOG\_LEVEL property; see that property for details.

#### LOG_LEVEL\_DEBUG = 0x00000001 

This is a possible setting for the LOG\_LEVEL property; see that property for details.

#### LOG_LEVEL\_FRAME = 0x00000008 

This is a possible setting for the LOG\_LEVEL property; see that property for details.

#### LOG_LEVEL\_NONE = 0x00000000 

This is a possible setting for the LOG\_LEVEL property; see that property for details.

#### LOG_LEVEL\_RTCP = 0x00000004 

This is a possible setting for the LOG\_LEVEL property; see that property for details.

#### LOG_LEVEL\_RTP = 0x00000002 

This is a possible setting for the LOG\_LEVEL property; see that property for details.

### LOW_LATENCY\_BUFFER\_OPTION (75)

Set a low latency buffer option.

This must be one of the following values:

- **LOW\_LATENCY\_BUFFEROPTION\_NONE (0x00000000)** The latency value is set by INITIAL\_BUFFERIN-
    G\_DURATION and RE\_BUFFERING\_DURATION of NexProperty. It should set the reliable value depending
    on the bitrate of content and network environment.
- **LOW\_LATENCY\_BUFFEROPTION\_AUTO\_BUFFER (0x00000001)** The latency value is calculated by the
    player at runtime. During playback, the latency may increase or decrease because it may change depending
    on the network environment.
- **LOW\_LATENCY\_BUFFEROPTION\_CONST\_BUFFER (0x00000002)** The latency value is calculated by the
    player at the beginning of playback and maintains the value unchanged during playback. The latency in-
    creases more than when using Auto Buffer Mode, but the rebuffering will be reduced and try to maintain
    constant latency after rebuffering.

**Type:** unsigned integer

**Default:** LOW\_LATENCY\_BUFFEROPTION\_NONE

#### LOW_LATENCY\_BUFFEROPTION\_AUTO\_BUFFER = 0x00000001 

This is a possible setting for the LOW\_LATENCY\_BUFFER\_OPTION property; see that property for details.

#### LOW_LATENCY\_BUFFEROPTION\_CONST\_BUFFER = 0x00000002 

This is a possible setting for the LOW\_LATENCY\_BUFFER\_OPTION property; see that property for details.

#### LOW_LATENCY\_BUFFEROPTION\_NONE = 0x00000000 

This is a possible setting for the LOW\_LATENCY\_BUFFER\_OPTION property; see that property for details.

### MAX_BUFFER\_DURATION (143)

The maximum duration of prefetch buffer to pause filling the buffer.

If the duration of content available in the filling prefetch buffer is greater than this value, filling of the buffer will be
paused until the buffer status meets the condition of MIN\_BUFFER\_DURATION.

> **Warning** Note that when setting `MAX_BUFFER_DURATION` to a specific value, the value chosen must be at least twice the value of `RE_BUFFERING_DURATION`. If a smaller value is chosen, the value of `MAX_BUFFER_DURATION` will automatically be increased to twice the value of RE_BUFFERING_DURATION. For example, if `RE_BUFFERING_DURATION=5000` ms and one tries to set `MAX_BUFFER_DURATION` to 7000 ms, `MAX_BUFFER_DURATION` will automatically be set to 10000 ms instead.
 
**Type:** unsigned integer

**Unit:** milliseconds

**Default:** 300000 (300s)

### MAX_BUFFER\_RATE (141)

The maximum filled percentage of the prefetch buffer to pause filling the buffer.

If the prefetch buffer is more than this value percent full, filling the buffer will be paused until the buffer status meets the condition set by the property `MIN_BUFFER_RATE`.

**Type:** unsigned integer

**Unit:** percent

**Default:** 90 (90%)
 
### MAX_BW (117)

When using HLS ABR, this is the maximum allowable bandwidth.

Any track with a bandwidth greater than this value will not be played back.

> **Warning** To take effect, this property should be set before calling `NexPlayer.open.NexPlayer.setProperty(MAX_BW)` can be used to set the bandwidth limit for initial segments of content, which are downloaded shortly after NexPlayer opens. To change the maximum allowable bandwidth dynamically while content is playing, please call the method changeMaxBandWidth instead.
 
This property should be set to zero for no maximum.

**Type:** unsigned integer

**Unit:** bps (bits per second)

**Default:** 0 (no maximum)

### MAX_CAPTION\_LENGTH (901)

Set it to extend max caption length.

This property should be called after init but before calling open.

**Type:** int

**Default:** 8192
 
### MAX_H264\_PROFILE (118)

Limits the H.264 profile that can be selected from an HLS playlist.

Under normal operation, the track with the highest supported H.264 profile is selected from an HLS playlist. If this property is set, no track with a profile higher than this value will be selected.

This should be set to zero for no limit.

**Type:** unsigned integer

**Default:** 0 (use any profile)

### MAX_HEIGHT (126)

Limits the maximum height (in pixels) of the video tracks that can be selected during streaming play.

This is used to prevent NexPlayer from attempting to play tracks that are encoded at too high a resolution for the device to handle effectively. NexPlayer will instead select a track with a lower resolution.

**Type:** integer

**Unit:** pixels

**Default:** 0x7FFFFFFF

### MAX_WIDTH (125)

Limits the maximum width (in pixels) of the video tracks that can be selected during streaming play.

This is used to prevent NexPlayer from attempting to play tracks that are encoded at too high a resolution for the device to handle effectively. NexPlayer will instead select a track with a lower resolution.

**Type:** integer

**Unit:** pixels

**Default:** 0x7FFFFFFF

### MIN_BUFFER\_DURATION (142)

The minumum duration of prefetch buffer to resume filling the buffer.

If the duration of content available in the filling buffer is less than this value, filling of the buffer will be resumed until the buffer status meets a condition set by either MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION.

**Type:** unsigned integer

**Unit:** milliseconds (ms)

**Default:** 30000 (30s)
 
### MIN_BUFFER\_RATE (140)

The minumum filled percentage of the prefetch buffer to resume filling the buffer.

If the prefetch buffer is less full than the value set by this property, the buffer will resume filling until the buffer status meets a condition set by either MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION.

**Type:** unsigned integer

**Unit:** percent

**Default:** 30 (30%)
 
### MIN_BW (516)

When using HLS ABR, this is the minimum allowable bandwidth.

Any track with a bandwidth smaller than this value will not be played back.

> **Note** To dynamically set a minimum bandwidth allowed while content is playing, please call the method `NexABRController::changeMinBandWidth()` instead. This property should be set to zero for no minimum.
 
**Type:** unsigned integer

**Unit:** bps (bits per second)

**Default:** 0 (no minimum)

### NEW_TRACK\_SELECTION\_MODE (510)

Sets the track selection mode NexPlayer will use when playing Smooth Streaming content.

This property determines how a new track is selected when starting to play new Smooth Streaming content. Based on the mode set here, NexPlayer will prefer the specified range of tracks when selecting which to play first.

While the default setting of selecting high bitrate tracks will be acceptable generally, there may be certain circumstances in which it is preferable that a lower bitrate track be selected first, and this property offers that flexibility.

Please see the sample code for an example of how to use this property.

**Type:** unsigned integer

**Values:**

- 0: Based on the estimated bitrate when receiving the manifest file, NexPlayer selects a lower bitrate track than the estimated bitrate. For example, for track bitrates of 1, 2, 3, and 4Mbps, NexPlayer calculates a bitrate of 3.2Mbps, and thus selects the 3Mbps bitrate track.
- 1: Prefer high bitrate tracks.
- 2: Prefer mid-range bitrate tracks.
- 3: Prefer low bitrate tracks.

**Default:** 1: Prefer high bitrate tracks.
 
### NOTOPEN_PLAYAUDIO (27)

Prevents the audio track from playing back when set to TRUE (1).

**Type:** boolean

**Default:** 0

### NOTOPEN_PLAYTEXT (29)

Prevents the text (subtitle) track from playing back when set to TRUE (1).

**Type:** boolean

**Default:** 0

### NOTOPEN_PLAYVIDEO (28)

Prevents the video track from playing back when set to TRUE (1).

**Type:** boolean

**Default:** 0

### OPEN_MEDIA\_FILE\_FROM\_SPECIFIED\_TS (513)

Allows NexPlayer to begin downloading content media files from a specified time stamp in the content.

 >**Warning** This property is currently only supported for VOD in HTTP Live Streaming (HLS).
 
NexPlayer allows users to start playback in the middle of a content file with the start api, but typically, before playback can begin, the player still opens content from the first media file available and then has to receive all of the media files between the first file and the point where the user would like to start playback.

When playback is to start in the middle of content, this property allows the player to skip receiving the unneeded earlier media files based on the time stamp value set by the application, and instead begin downloading media files from a position closer to the specified time stamp instead.

This property can thus reduce the time needed to open and start playing a media file in the middle of VOD content.

> **Note** This property must be set before NexPlayer.open is called.
 
**Type:** unsigned integer

**Unit:** msec (1/1000 s)

**Default:** 0xFFFFFFFF

### PARTIAL_PREFETCH (519)

Sets whether or not to begin playback after a part of the TS file is downloaded.

By default, this property is set to 0 to download the first TS file completely to play content.

**Type:** boolean

**Default:** 0

**Values:**

- 0 : Partial prefetch ignored; playback will begin after downloading the first TS file completely.
- 1 : Partial prefetch enabled; playback will begin after a part of the TS file is downloaded.
 
### PLAYABLE\_FOR\_NOT\_SUPPORT\_AUDIO\_CODEC (48)

If set to 0, returns an error or generates an error event if the audio codec is not supported.

The default behavior (if this is 1) is to allow media playback even if the audio codec is not supported.

**Type:** unsigned integer

**Default:** 1

### PLAYABLE_FOR\_NOT\_SUPPORT\_VIDEO\_CODEC (49)

If set to 0, returns an error or generates an error event if the video codec is not supported.

The default behavior (if this is 1) is to allow media playback even if the video codec is not supported.

**Type:** unsigned integer

**Default:** 1

### PREFER_AV (130)

Controls whether NexPlayer prefers tracks with both audio and video content.

If this property is set to 0, if the available network bandwidth drops below the minimum needed to play the current track without buffering, the player will immediately switch to a lower bandwidth track, if one is available, to minimize any time spent buffering.

If this property is set to 1, the player will attempt to choose only tracks that include both audio and video content, even if that causes some buffering. However, if the buffering becomes too severe or lasts for an extended time, the player may eventually switch to an audio-only track anyway.

**Type:** unsigned integer

**Default:** 1

**Values:**

- 0: Immediate switching to a lower bandwidth track.
- 1: Prefer tracks with both audio and video.

**See Also**
 
PREFER\_BANDWIDTH

### PREFER_BANDWIDTH (129)

This property sets the preferred bandwidth when switching tracks during streaming play.

Under normal operation (when this property is zero), if the available network bandwidth drops below the minimum needed to play the current track without buffering, the player will immediately switch to a lower bandwidth track, if one is available, to minimize any time spent buffering.

If this property is set, the player will attempt to choose only tracks above the specified bandwidth, even if that causes some buffering. However, if the buffering becomes too severe or lasts for an extended time, the player may eventually switch to a lower-bandwidth track anyway.

**Type:** unsigned integer

**Unit:** kbps (Kbits per second)

**Default:** 0

**See Also**

PREFER\_AV
 
### PREFER_LANGUAGE (530)

Sets the language of both audio and text played in multi-stream content.

It can be used to set the preferred language of audio and text streams to be displayed in content, before NexPlayer begins playing content.

> **Warning** To change any media streamwhilecontent is playing, the method setMediaStream should be called instead.  

This property should be set by calling setProperty() after init and before NexPlayer.open() is called as demonstrated in the following sample code:

```java
mNexPlayer.setProperty(NexProperty.PREFER\_LANGUAGE, "eng");
```

> **Note** Accurate language labels (not the name of a text stream) should be used for the values of this property.
 
**Type:** String

**Default:** null

**Values:** Accurate language labels asStrings. For example, "eng" for English.
 
### PREFER_LANGUAGE\_AUDIO (531)

Sets the language to use for audio in multi-stream content, before content is played.

This property can be used to set the preferred language of audio streams to be used in content,beforeNex-
Player™ begins playing content.

> **Warning** To change any media streamwhilecontent is playing, the method setMediaStream should be called instead. To set the preferred language for both audio and text streams to the same language, use the NexProperty, PREFER\_LANGUAGE, instead.
 
This property should be set by calling setProperty() after init and before NexPlayer.open() is called.

> **Note** Accurate language labels (not the name of a text stream) should be used for the values of this property.
 
**Type:** String

**Default:** null

**Values:** Accurate language labels asStrings. For example, "eng" for English.
 
### PREFER_LANGUAGE\_TEXT (532)

Sets the language to use for text in multi-stream content, before content is played.

This property can be used to set the preferred language of text streams to be displayed in content, before NexPlayer begins playing content.

> **Warning** To change any media streamwhilecontent is playing, the method setMediaStream should be called instead. To set the preferred language for both audio and text streams to the same language, use the NexProperty, PREFER\_LANGUAGE, instead.
 
This property should be set by calling setProperty() after init and before NexPlayer.open() is called.

> **Note** Accurate language labels (not the name of a text stream) should be used for the values of this property.
 
**Type:** String

**Default:** null

**Values:** Accurate language labels asStrings. For example, "eng" for English.
 
### PREFETCH_BUFFER\_SIZE (16)

The size of the prefetch buffer to prepare for playback.

If the buffer status satisfies either limit set by MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION, the filling of the prefetch buffer will be stopped even though there may be spare space still available in the prefetch buffer.

If this value is set to 20MB, 1/4 (5MB) is allocated to the past (content already played) and 3/4(15MB) is allocated to the future (content yet to be played).

> **Warning** Setting too large of a value here may lead to a large consumption of data packets under 3G or LTE network conditions.
 
**Type:** unsigned integer

**Unit:** bytes

**Default:** 50x1024x1024 (50MB)
 
### PROXY_ADDRESS (31)

Set the proxy address.

**Type:** String

**Default:** null

### PROXY_PORT (32)

Set the proxy port number.

**Type:** integer

**Default:** 0

### RE_BUFFERING\_DURATION (10)

The number of milliseconds of media to buffer if additional buffering is required during streaming playback (HLS, RTSP, etc).

This is the amount of audio and video that NexPlayer buffers when the buffer becomes empty during playback (requiring additional buffering).Afteropen() is called, this property can be set at any time during playback by calling setProperty.

For the initial buffering, the value of the property INITIAL\_BUFFERING\_DURATION is used instead.

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 5000 (5 seconds)

### REQUEST_RADIO\_METADATA\_MODE (515)

Allows NexPlayer to add an explicit request for metadata in internet radio stream content.

> **Warning** This is currently only supported in SHOUTcast and IceCast HLS content.
 
If an explicit request for metadata is not made, a server may or may not send internet radio stream metadata even if it exists.

Setting this property to 1 means an explicit request for internet radio stream metadata will be included with every content request sent to a server. If this property is set to 2, NexPlayer will only add an explicit request for metadata **after** initially receiving content and identifying it as a SHOUTcast or Icecast stream.

**Values:**

- **0 : DEFAULT :** Default mode. Does not add an additional explicit request for internet radio stream metadata.
- **1 : INSERT\_HEADER :** Always inserts a header with a request for internet radio stream metadata (with every content request).
- **2 : INSERT\_HEADER\_AFTER\_TRIAL :** If NexPlayer determines content is a SHOUTcast or Icecast stream, a header with an explicit request for metadata will be added to subsequent server requests.
 
### RFC_BUFFER\_COUNT (0x00070001)

Controls the maximum number of pages the player can allocate for the remote file cache.

The remote file cache stores data that has been read from disk or received over the network (this includes local, streaming and progressive content).

In general, this value should not be changed, as an incorrect setting can adversely affect performance, particularly when seeking.

In order to play multiplexed content, at least one audio chunk and one video chunk must fit inside a single RFC buffer page. For certain formats (PIFF, for example) at very high bitrates, the chunks may be too big to fit in a single page, in which case the RFC buffer page size will need to be increased. If the system has limited memory resources, it may be necessary to decrease the buffer count when increasing the page size.

Increasing the page size can increase seek times, especially for data received over the network (progressive download and streaming cases), so this value should not be changed unless there are issues playing specific content that cannot be solved in another way.

**Type:** unsigned integer

**Unit:** number of buffers

**Default:** 20

> **Warning** This property is not supported in this API version.
 
### RFC_BUFFER\_PAGE\_SIZE (0x00070002)

Controls the size of each page in the remote file cache.

Use caution when adjusting this value. Improper settings may adversely affect performance, or may cause some content to fail to play.

**See Also**
 
RFC\_BUFFER\_COUNT for a detailed description.
 
**Type:** unsigned integer

**Unit:** kilobytes (kB)

**Default:** 256

> **Warning** This property is not supported in this API version.

### RTP_PORT\_MAX (23)

The maximum possible port number for the RTP port that is created when performing RTSP streaming over UDP.

**Type:** unsigned integer

**Default:** 7000

> **Warning** This property is not supported in this API version.

### RTP_PORT\_MIN (22)

The minimum possible port number for the RTP port that is created when performing RTSP streaming over UDP.

**Type:** unsigned integer

**Default:** 6000

> **Warning** This property is not supported in this API version.

### SEEK_NEAREST\_IDR\_FRAME (217)

Sets the idr frame search option during seek.

If you want to search nearest IDR frame set 

```
SEEK_NEAREST_IDR_FRAME_DURING_LOCAL(1) | SEEK_NEAREST_IDR_FRAME_DURING_STREAMING(2)
``` 

as content type.

**Type:** unsigned integer

**Default:** SEEK\_NEAREST\_IDR\_FRAME\_DURING\_STREAMING(2)

**Values:**

- **0:** not search the nearest idr-frame.
- **1:** search the nearest idr-frame on Local Content.
- **2:** search the nearest idr-frame on Streaming Content.
 
> **Warning** This property is not supported in this API version.
 
### SEEK_RANGE\_FROM\_RA\_POINT (102)

Sets the range where NexPlayer will seek to a Random Access point rather than the exact target position provided in the seek API.

> **Warning** This property is only valid when the first parameter,exact, in the seek API istrue.
 
Setting this value is a kind of option for the seek API and can be used to minimize the time required to seek in content by taking advantage of Random Access points in the content.

A Random Access point is a specific position that the parser is allowed to seek to directly.

This value sets the range where NexPlayer will seek from a Random Access point given by the parser to a target position that equals msec(milliseconds), the first parameter in the seek() API.

If the exact parameter, the second parameter in the seek API, istrueand the difference between a Random Access point and the target position is within this value, seek will find and seek to the exact target position. If the exact parameter is set to true and the difference between a Random Access point and the target position is beyond this range, seek will give up the accurate target point and will instead seek to and play from the Random Access point.

For example, if NexPlayer is seeking to 10000 ms exactly (exact=true) and there is a Random Access point at 7000 ms, if this property is set to less than 3000 ms, the player will ignore the exact target value and will instead play from 7000 ms. On the other hand, if this property is set to more than 3000 ms, then NexPlayer will seek exactly to 10000 ms and begin playback.

> **Warning** Please remember that in order to seek to a target position, audio or video frames have to be decoded. If too large of a value is set here, it may cause the seek process to consume an excessive amount of time especially in high resolution video content.
 
**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 10000 (10 seconds)

**See Also**
 
seek for more information
 
### SEGMENT_TS\_RELIABLE (570)

Sets whether or not to trust a content segment’s timestamp when playback starts.

This property should be called after init but before calling open.

**Type:** int

**Default:** 1

**Values:**

- **0:** Adjust the timestamp during playback.
- **1:** Trust the timestamp during playback.
 
### SEND_ALL\_DASH\_MPD\_EVENTS (605)

Set it to decide which events passed through `onDashScte35Event` listener.

This property should be called after init but before calling open.

**Type:** int

**Default:** 0

**Values:**

- **0:** Only scte35 events will be passed through onDashScte35Event listener.
- **1:** All the events in the MPD will be passed through onDashScte35Event listener.
 
### SET_PRESENTATION\_DELAY (590)

For DASH, use suggestedPresentationDelay to synchronize end users.

For HLS, use the #EXT-X-PROGRAM-DATE-TIME tag to sync end users.

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 2000 (2 sec)
 
### SET_CEA608\_TYPE (502)

Sets the type of caption display for CEA 608 captions, but is a deprecated property.

Because CEA 608 closed captions include multiple text attributes and additional display modes, in past versions of the NexPlayer SDK, this property allowed these captions to be displayed more simply in BASIC form (where the CEA 608 captions were essentially treated in the same way as other forms of subtitles) or allowed the player to fully support all attributes and display modes available with CEA 608 specifications.

Because the BASIC mode did not always easily allow the player to display the captions in such a way that they were easily read, especially with live content, and to always support the full specification, this property has been deprecated and CEA 608 closed captions are always fully implemented according to the specification, as if this property were set to 1.

**Type:** unsigned integer

**Default:** 0

**Values:**

- 0 : BASIC: Captions displayed one row at a time.
- 1 : FULL: Each character in the Closed Captions added individually. This type of caption display supports all CEA 608 text attributes and display specifications.

> **Deprecated** Do not use.

### SET_COOKIE (500)

Controls whether or not the player honors cookies sent by the server.

**Type:** unsigned integer

**Default:** 1

**Values:**

- **0:** Ignore HTTP cookie headers sent by the server.
- **1:** Cookie headers received from a streaming server along with the initial manifest or playlist are included with further HTTP requests during the session.

### SET_DURATION\_OF\_UPDATE\_CONTENT\_INFO (501)

For internal use only. This should be otherwise ignored.

### SET_LIVEBACKOFF (504)

Sets the SmoothStreamingLiveBackOffproperty when playing Smooth Streaming content.

This property sets the duration of content (closest to live) that cannot yet be accessed or downloaded by the player.

It is like setting how long to wait before asking for the latest fragment in a live presentation, and thus basically set the played "live" point back from the actual live content available on the server.

The end-to-end latency of the player (what is being played "live" in the player compared to what is available live on the server) is at least the duration of LiveBackOff added to the duration set for LivePlaybackOffset with `SET_LIVEPLAYBACKOFFSET`.

**Type:** unsigned int

**Units:** milliseconds (ms)

**Default:** 6000 (ms)
 
### SET_LIVEPLAYBACKOFFSET (505)

Sets the `SmoothStreamingLivePlaybackOffset` property when playing Smooth Streaming content.

This property sets the duration away from the live position to start playback when joining a live presentation when the LiveView option is set to "Recent", but excludes theLiveBackOffduration (set by SET\_LIVEBACKOFF).

As a result, live content will be played behind the actual live position by a duration determined by both LiveBackOff and the value for LivePlaybackOffset set here.

Setting this property enables faster startup because it allows a buffer to be built up as fast as bandwidth will support (potentially faster than real time), which creates a buffer against network jitter. It does however also increase end-to-end latency, which means what is played "live" in the player is farther behind the actual live playing point of the content.

**Type:** unsigned int

**Units:** milliseconds (ms)

**Default:** 7000 (ms)

 
### SET_SPD\_SYNC\_DIFF\_TIME (592)

If the current playback is not more synchronized than this value, the player will speed up playback and make sync.

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 300 (300 msec)
 
### SET_SPD\_TOO\_MUCH\_DIFF\_TIME (593)

If playback is out of sync than this value, the player will jump to synchronize the video rather than make it by speeding up.

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 5000 (5 seconds)
 
### SET_TO\_SKIP\_BFRAME (103)

If set to true, unconditionally skips all B-frames without decoding them; not currently supported.

**Type:** boolean

**Default:** 0

### SOCKET_CONNECTION\_TIMEOUT (20)

The amount of time to wait before timing out when establishing a connection to the server.

If the connection to the server (the socket connection) cannot be established within the specified time, an error event will be generated and playback will not start.

Set this to zero to disable timeout (NexPlayer will wait indefinitely for a connection).

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 30000 (30 seconds)

### SOCKET_OPERATION\_TIMEOUT (73)

The maximum waiting time for an HTTP request/response message to be sent to NexPlayer.

The maximum waiting time for an HTTP request/response message after it is sent to the streaming server. If the reply does not arrive within this time, it will be regarded as an error.

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 30,000 (30 seconds)

### SOURCE_OPEN\_TIMEOUT (63)

Sets the amount of time to wait for an open request to complete.

This is used when NexPlayer tries to open new media. If there is no response from the server for longer than the amount of time specified here, the open request will be stopped and onAsyncCmdComplete will be called with the result, namely the error code, `NexErrorCode.SOURCE_OPEN_TIMEOUT`.

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 300000 (300 seconds)

### SPEED\_CONTROL\_AVAILABILITY (0x00050001)

Indicates whether or not speed control is available on this device.

As audio solution components are optional, this property can be checked for availability.

This is useful to determine whether to display the speed control in the user interface.

**Type:** unsigned integer(read-only)

**Values:**

- **0:** Device does not support speed control.
- **1:** Device supports speed control.

### START\_NEARESTBW (555)

Sets a target bandwidth (before playing HLS content) when selecting which track to play as playback starts.

While NexPlayer automatically chooses an ideal track to play based on several factors including device capability and network conditions, there may be situations in which starting playback from a track with a bandwidth near a particular bandwidth is desired.

When this property is set, NexPlayer selects and starts playing the track in content that has the bandwidth closest to the set bandwidth value, initially ignoring other factors.

Note that as playback continues, the track played may change as NexPlayer judges all factors that influence streaming playback and chooses the best option.

This property should be called after init but before calling open.

**Type:** int

**Unit:** bps (bits per second)

**Default:** null

**Values:** The target bandwidth value, in bits per second (bps). Note that if `START_NEARESTBW` is set to 0, NexPlayer will play normally, as if this property has not been set.

### START_WITH\_AV (506)

Starts video together with or separately from audio.

This property starts to play audio and video together when starting, if the video timestamp is slower than audio’s timestamp.

If it is 1, it forces the video and audio to start at the same time. If it is 0, it lets the video and audio to start separately.

**Type:** boolean

**Default:** 0 (video and audio will start separately, based on the timestamps)

### SUPPORT_ABR (116)

If set to 1, enables HLS Adaptive Bit Rate (ABR) support.

**Type:** boolean

**Default:** 1

### SUPPORT_APPLE\_HTTP (115)

If set to 1, enables Apple HTTP Live Streaming (HLS) support.

**Type:** boolean

**Default:** 1

### SUPPORT_EYE\_PLEASER (50)

This property enables the Eye Pleaser feature.

If the decoding or display of video frames takes too long, it may be necessary to skip some frames in order to maintain a normal rate of playback. Under normal operation, frames are skipped immediately to catch up. When Eye Pleaser is enabled, skipped frames are spread out to try to make playback appear smoother.

Note that in older versions of the NexPlayer SDK, this property was also called USE\_EYEPLEASER.

**Type:** integer

**Default:** 1

**Values:**

- 0: Normal operation (frames are skipped immediately).
- 1: Eye Pleaser enabled (skipped frames are spread out).

### SUPPORT_LOCAL (110)

If set to 1, enables local file playback support.

**Type:** boolean

**Default:** 1

### SUPPORT_MS\_SMOOTH\_STREAMING (123)

If set to 1, this enables MS Smooth Streaming support.

**Type:** boolean

**Default:** 1

### SUPPORT_PD (112)

If set to 1, enables progressive download support.

**Type:** boolean

**Default:** 1

### SUPPORT_RDT (114)

If set to 1, enables Real Media Streaming support.

**Type:** boolean

**Default:** 0

### SUPPORT_RTSP (111)

If set to 1, enables RTSP streaming support.

**Type:** boolean

**Default:** 0

> **Warning** This property is not supported in this API version.
 
### SUPPORT_WMS (113)

If set to 1, enables Microsoft Windows Media Streaming support.

**Type:** boolean

**Default:** 0

### SW_DECODED\_VIDEO\_BUFFER\_COUNT (200)

Sets the size of the buffer used to receive decoded video frames when the software video codec is used.

Setting the buffer size in advance based on device system performance can improve decoding performance with
the SW codec, as more data can be decoded and saved in the buffer.

> **Note** This property must be used with the property `USE_SYNCTASK` set to 1.
 
**Type:** unsigned integer

**Unit:** decoded video frame count

**Default:** 0
 
> **Warning** This property is not supported in this API version.

### TIMED_ID3\_META\_KEY (521)

Allows custom ID3 tags added to timed metadata in content to be recognized and handled by NexPlayer.

When customized ID3 tags with additional information have been added to the timed metadata in content, this property can be used to help NexPlayer recognize and pass those ID3 tags and the extra information they contain to an application.

Additional customized timed metadata will be saved as an ArrayList of NexID3TagText objects and can be retrieved by calling NexID3TagInformation.getArrExtraData.

This property must be set before NexPlayer.open is called.

**Type:** String

**Values:** a list of the customized ID3 tag names separated by semicolons (;)

**Default:** nothing

**See Also**

- NexID3TagText.getExtraDataID
- NexID3TagInformation.getArrExtraData
- NexID3TagInformation.setArrExtraData
 
### TIMESTAMP_DIFFERENCE\_VDISP\_SKIP (14)

The number of milliseconds that video is allowed to run behind audio before the system begins skipping frames to maintain synchronization.

For example, 70 means that if the current video time is more than 70msec behind the audio time, the current video frame will be skipped. This is used to adjust video and audio synchronization.

> **Note** As of version 6.33, the default value changed from 200 msec to 70 msec.
 
**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 70 (0.07 sec)

### TIMESTAMP_DIFFERENCE\_VDISP\_WAIT (13)

The number of milliseconds (as a negative number) that video is allowed to run ahead of audio before the system waits for audio to catch up.

For example, -50 means that if the current video time is more than 50msec ahead of the audio time, the current video frame will not be displayed until the audio catches up to the same time stamp. This is used to adjust video and audio synchronization.
 
**Type:** integer(should be negative)

**Unit:** msec (1/1000 sec)

**Default:** -50 (50msec)

### TOO_MUCH\_LOSTFRAME\_DURATION (105)

Maximum amount of silence to insert to make up for lost audio frames.

Under normal operation, if audio frames are lost (if there is a time gap in received audio frames), silence will be inserted automatically to make up the gap.

However, if the number of audio frames lost represents a span of time larger than the value set for this property, it is assumed that there is a network problem or some other abnormal condition and silence is not inserted.

This prevents, for example, a corruption in the time stamp in an audio frame from causing the system to insert an exceptionally long period of silence (which could possibly prevent further audio playback or cause other unusual behavior).

**Type:** unsigned integer

**Unit:** msec (1/1000 sec)

**Default:** 20000 (20 seconds)

> **Warning** This property is not supported in this API version.

### TRACKDOWN_VIDEO\_RATIO (132)

This property controls the ratio of skipped frames that will be tolerated before a track change is forced, if `ENABLE_TRACKDOWN` is enabled.

The formula used to determine if a track switch is necessary is:

```
(^100) *(RenderedFrames / DecodedFrames) < TRACKDOWN\_VIDEO\_RATIO
```

In other words, if this property is set to 70, and `ENABLE_TRACKDOWN` is set to 1, NexPlayer will require that at least 70% of the decoded frames be displayed. If less than 70% can be displayed (greater than 30% skipped frames), then the next lower bandwidth track will be selected.

A performance-based track switch **permanently** limits the maximum bandwidth of tracks that are eligible for play back until the content is closed. For this reason, setting this ratio higher than the default value of 70 is strongly discouraged. (This differs from the bandwidth-based algorithm, which continuously adapts to current network bandwidth).

**Type:** integer
**Range:** 0 to 100
**Default:** 70

### USE_SYNCTASK (187)

Sets whether or not NexPlayer should use SyncTask feature; not currently supported.

When the software video codec is being used, SyncTask can improve decoding performance.

> **Note** This property must be set before playing content so it must be set when the codec mode (SW) is selected, prior to calling NexPlayer.init or NexPlayer.open.
 
**Type:** unsigned integer

**Default:** 1

**Values:**

- **0:** Do not use SyncTask.
- **1:** Use SyncTask.
 
> **Warning** This property is not supported in this API version.
 
### USERAGENT_STRING (58)

RTSP/HTTP User Agent value.

**Type:** String

**Default:** "User-Agent: Mozilla/5.0 (iPhone; U; CPU iPhone OS 3\_1\_2 like Mac OS X; ko-kr) AppleWebKit/528.18 (KHTML, like Gecko) Version/4.0 Mobile/7D11 Safari/528.16"

### ENABLE_SUPPORT\_HTTP2 (904)

When this property is 1, all the request will be made over HTTP/2 protocol. By default HTTP/1.1 will be used.

**Type:** integer
 
**Default:** 0
