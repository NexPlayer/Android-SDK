# Optimizing the Playback

There are a wide array of properties that can be adjusted to control the behavior of various aspects of the player. Properties are identified with an integer identifier from the NexProperty enumeration.

## Properties

### AV_SYNC\_OFFSET (124)

Adjusts A/V synchronization by ofsetting video relative to audio.

Positive values cause the video to play faster than the audio, while negative values cause the audio to play faster than the video. Under normal operation, this can be set to zero, but in some cases where the synchronization is bad in the original content, this can be used to correct for the error.

While A/V synchronization is generally optimized internally by NexPlayer, there may occasionally be devices which need to be offset in order to improve overall A/V synchronization. For examples of how to set AV\_SET\_OFFSET based on the device in use, please see the Sample Application code as well as the introductory section A/V Synchronization section.

Appropriate values for any other problematic devices need to be determined experimentally by testing manually.

For example, to improve synchronization on the Galaxy Nexus, set AV\_SYNC\_OFFSET to the value XXX as follows:

```java
if(android.os.Build.MODEL.equalsIgnoreCase("Galaxy Nexus")) {
	mDevAVSyncOffset = XXX;
}
	
Log.d(TAG, "Device Model Name : " + android.os.Build.MODEL + " Dev Offset Time : " + mDevAVSyncOffset);

mNexPlayer.setProperty(NexProperty.AV_SYNC_OFFSET, mDevAVSyncOffset);
```

Appropriate values for any devices displaying AV-sync issues can be determined by trial and error with different values, but most devices’ AV synchronization should generally be handled by NexPlayer internally.

- **Type:** integer

- **Unit:** msec (1/1000 sec)

**Range:** -2000∼+2000

- **Default:** 0


### APPLS_FORCESTART\_AVTRACK (198)

This sets whether or not NexPlayer should select a higher track if the first track is Audio only.

If the first track is audio only in HLS, a higher track will be selected.

- **Type:** boolean

- **Default:** 0

- **Values:**

- **0:** Do not select a higher track.
- **1:** Select a higher track.

> **Note** This property must be set before NexPlayer.open is called.


### ENABLE_AUDIOONLY\_TRACK (556)

Sets whether to enable or disable the Audio Only track in HLS content.

This property should be called after init but before calling open.

- **Default:** 1

- **Values:**

- **0:** Audio Only track disabled.
- **1:** Audio Only track enabled.

### START_WITH\_AV (506)

Starts video together with or separately from audio.

This property starts to play audio and video together when starting, if the video timestamp is slower than audio’s timestamp.

If it is 1, it forces the video and audio to start at the same time. If it is 0, it lets the video and audio to start separately.

- **Default:** 0 (video and audio will start separately, based on the timestamps)

### PREFER_AV (130)

Controls whether NexPlayer prefers tracks with both audio and video content.

If this property is set to 0, if the available network bandwidth drops below the minimum needed to play the current track without buffering, the player will immediately switch to a lower bandwidth track, if one is available, to minimize any time spent buffering.

If this property is set to 1, the player will attempt to choose only tracks that include both audio and video content, even if that causes some buffering. However, if the buffering becomes too severe or lasts for an extended time, the player may eventually switch to an audio-only track anyway.

- **Default:** 1

- **Values:**

- 0: Immediate switching to a lower bandwidth track.
- 1: Prefer tracks with both audio and video.

### LIVE_OFFSET\_SEGMENT\_COUNT (54)

Specifies the segment offset when starting playback.

This property may have a different meaning depending on the LIVE\_VIEW\_OPTION.

If `LIVE_VIEW_OPTION` is set to `LIVE_VIEW_RECENT`, then this property specifies the offset of segment from the live edge when starting playback. For example; 

- 1: The player will select the last segment in the manifest. 
- 2: The player will select the second last segment in the manifest. 
- 3: The player will select the third last segment in the manifest. If this property is set to 0, the player will select the segment depending on its policy.

This property is not currently defined for other `LIVE_VIEW_OPTION`.

- **Default:** 0

### LIVE_OFFSET\_TIME (76)

Specifies the segment offset in time when starting playback.

This property may have a different meaning depending on the LIVE\_VIEW\_OPTION. This property has higher priority than `LIVE_OFFSET_SEGMENT_COUNT`. If `LIVE_VIEW_OPTION` is set to `LIVE_VIEW_RECENT`, then this property specifies the time offset of segment from the live edge when starting playback. For example, if the duration of each segment is 6 seconds:

**1** ∼ **6000:** The player will select the last segment in the manifest.

**6001** ∼ **12000:** The player will select the second last segment in the manifest.

**12001** ∼ **18000:** The player will select the third last segment in the manifest.

If this property is set to 0, the player will select the segment depending on its policy.

This property is not currently defined for other `LIVE_VIEW_OPTION`.

- **Unit:** msec (1/1000 sec)

- **Default:** 0


### LIVE_VIEW\_OPTION (53)

Live HLS playback option.

This must be one of the following **Values:**

- **LIVE_VIEW\_RECENT (0x00000000)** Starts playback from the 3rd segment from the last. For example, if manifest have 1.ts, 2.ts, 3.ts, 4.ts, 5.ts then playback will start from the beginning of 3.ts. 

- **LIVE_VIEW\_RECENT\_BYTARGETDUR (0x00000001)** Start playback from the most recently received media segement (.ts) files, based on the value set for the `EXT-X-TARGETDURATION` tag in the HLS live playlist. (The player will begin playback at the media segment that immediately precedes the media segment that is three times (x3) the target duration before the latest media segment file loaded). As a concrete example, if the target duration is set to 12 seconds and the total duration of currently loaded media segments is 48 seconds, playback will begin at the media file that immediately precedes the media segment with the timestamp at 12 (48-36) seconds. If this example HLS playlist includes media segment files 1.ts (duration of 10 seconds), 2.ts (9 sec), 3.ts (11 sec), 4.ts (10 sec), and 5.ts (8 sec), then playback will begin at the first media segment, 1.ts, because it immediate precedes the 2.ts segment (where the timestamp at 12 seconds occurs).

- **LIVE_VIEW\_FIRST (0x00000002)** Unconditionally start HLS playback from the first entry in the HLS playlist.

- **LIVE_VIEW\_LOW\_LATENCY (0x00000003)** Playback starts from a position close to real-time and frame skipping may occur during playback to maintain low latency.

?> When `EXT-X-PROGRAM-DATE-TIME` exists, playback will start from the first segment that is matching with the current time. 

- **Default:** LIVE\_VIEW\_RECENT

### LOW_LATENCY\_BUFFER\_OPTION (75)

Set a low latency buffer option.

This must be one of the following **Values:**

- **LOW\_LATENCY\_BUFFEROPTION\_NONE (0x00000000)** The latency value is set by INITIAL\_BUFFERING\_DURATION and RE\_BUFFERING\_DURATION of NexProperty. It should set the reliable value depending on the bitrate of content and network environment.
- **LOW\_LATENCY\_BUFFEROPTION\_AUTO\_BUFFER (0x00000001)** The latency value is calculated by the player at runtime. During playback, the latency may increase or decrease because it may change depending on the network environment.
- **LOW\_LATENCY\_BUFFEROPTION\_CONST\_BUFFER (0x00000002)** The latency value is calculated by the player at the beginning of playback and maintains the value unchanged during playback. The latency increases more than when using Auto Buffer Mode, but the rebuffering will be reduced and will try to maintain constant latency after rebuffering.

- **Default:** LOW\_LATENCY\_BUFFEROPTION\_NONE

#### LOW_LATENCY\_BUFFEROPTION\_AUTO\_BUFFER = 0x00000001 

This is a possible setting for the LOW\_LATENCY\_BUFFER\_OPTION property; see that property for details.

#### LOW_LATENCY\_BUFFEROPTION\_CONST\_BUFFER = 0x00000002 

This is a possible setting for the LOW\_LATENCY\_BUFFER\_OPTION property; see that property for details.

#### LOW_LATENCY\_BUFFEROPTION\_NONE = 0x00000000 

This is a possible setting for the LOW\_LATENCY\_BUFFER\_OPTION property; see that property for details.

### PREFER_BANDWIDTH (129)

This property sets the preferred bandwidth when switching tracks during live playback.

Under normal operation (when this property is zero), if the available network bandwidth drops below the minimum needed to play the current track without buffering, the player will immediately switch to a lower bandwidth track, if one is available, to minimize any time spent buffering.

If this property is set, the player will attempt to choose only tracks above the specified bandwidth, even if that causes some buffering. However, if the buffering becomes too severe or lasts for an extended time, the player may eventually switch to a lower-bandwidth track anyway.

- **Unit:** kbps (Kbits per second)

- **Default:** 0

### PREFER_LANGUAGE (530)

Sets the language of both audio and text played in multi-stream content.

It can be used to set the preferred language of audio and text streams to be displayed in content, before NexPlayer begins playing content.

?> To change any media stream while content is playing, the method setMediaStream should be called instead.  

This property should be set by calling setProperty() after init and before NexPlayer.open() is called as demonstrated in the following sample code:

```java
mNexPlayer.setProperty(NexProperty.PREFER\_LANGUAGE, "eng");
```

> **Note** Accurate language labels (not the name of a text stream) should be used for the values of this property.
 
- **Default:** null

- **Values:** Accurate language labels as Strings. For example, "eng" for English.

### PREFER_LANGUAGE\_AUDIO (531)

Sets the language to use for audio in multi-stream content, before content is played.

This property can be used to set the preferred language of audio streams to be used in content, before NexPlayer begins playing content.

?>  To change any media stream while content is playing, the method setMediaStream should be called instead. To set the preferred language for both audio and text streams to the same language, use the NexProperty, PREFER\_LANGUAGE, instead.
 
This property should be set by calling setProperty() after init and before NexPlayer.open() is called.

?> Accurate language labels (not the name of a text stream) should be used for the values of this property.

- **Default:** null

- **Values:** Accurate language labels as Strings. For example, "eng" for English.

### PREFER_LANGUAGE\_TEXT (532)

Sets the language to use for text in multistream content, before content is played.

This property can be used to set the preferred language of text streams to be displayed in content, before NexPlayer begins playing content.

?> To change any media stream while content is playing, the method setMediaStream should be called instead. To set the preferred language for both audio and text streams to the same language, use the NexProperty, PREFER\_LANGUAGE, instead.
 
This property should be set by calling setProperty() after init and before NexPlayer.open() is called.

?> Accurate language labels (not the name of a text stream) should be used for the values of this property.

- **Default:** null

- **Values:** Accurate language labels as Strings. For example, "eng" for English.

### NOTOPEN_PLAYAUDIO (27)

Prevents the audio track from playing back when set to TRUE (1).

- **Type:** boolean

- **Default:** 0

### NOTOPEN_PLAYTEXT (29)

Prevents the text (subtitle) track from playing back when set to TRUE (1).

- **Type:** boolean

- **Default:** 0

### NOTOPEN_PLAYVIDEO (28)

Prevents the video track from playing back when set to TRUE (1).

- **Type:** boolean

- **Default:** 0


