# Controlling the Buffer

NexPlayer loads content data into buffers in a device’s memory to prepare for playback (the so-called Prefetch buffer in NexPlayer). Buffer settings can be adjusted in multiple ways with the properties listed below:

### Control Buffer Size

 - `PREFETCH_BUFFER_SIZE`: This property sets the size of the prefetch buffer to prepare for playback. The default value is 50MB but depending on the content size, this value can be adjusted accordingly. If the buffer status satisfies either limit set by MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION, the filling of the prefetch buffer will be stopped even though there may be spare space still available in the prefetch buffer.

### Control Buffering Duration

NexPlayer uses two separate properties to determine buffering time, `INITIAL_BUFFERING_DURATION` and `RE_BUFFERING_DURATION`.

 - `INITIAL_BUFFERING_DURATION`: This property defines the initial time to buffer before beginning streaming playback (HLS, RTSP, etc). The default value is 5 seconds and when the buffer status meets this value set by INITIAL\_BUFFERING\_DURATION, the player will pause the filling of the buffer. This value is generally lower so that playback can begin as quickly as possible.
 
 - `RE_BUFFERING_DURATION`: This property defines how much content should be buffered when additional buffering during streaming playback (HLS, RTSP, etc) is necessary. The default value is 5 seconds and when the buffer status meets this value set by RE\_BUFFERING\_DURATION, the buffering will be paused. This re-buffering duration is also used when seeking in content (if the target seek destination time falls outside of the previously buffered content data).

### How Buffering Operates in General

NexPlayer will start filling the prefetch buffer automatically when the amount of data loaded in memory becomes less than the value set by a property defining the buffering minimum. Similarly, the buffer will stop loading data segments when the memory is filled more than the value set by a property defining a maximum buffered amount. The actual properties defining this behavior operate differently depending on the protocol type of the content, but these operations will run automatically in the background and can be adjusted with the following properties:

- **For Non-HTTP Protocols** :

 - `MIN_BUFFER_RATE`: If the prefetch buffer is less full than the value set by this property, the buffer will resume filling until the buffer status meets one of the conditions set by either *MAX\_BUFFER\_RATE* or *MAX\_BUFFER\_DURATION*. The default value is 30%.
 - `MAX_BUFFER_RATE`: If the prefetch buffer is more than this value percent full, buffering will be paused until the buffer status meets the condition set by the property MIN\_BUFFER\_RATE. The default value is 90%.
 - `MIN_BUFFER_DURATION`: If the duration of content available in the filling buffer is less than this value, buffering will resume filling the buffer until its status meets one of the conditions set by either MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION. The default value is 30 seconds.
 - `MAX_BUFFER_DURATION`: If the duration of content available in the filling prefetch buffer is greater than this value, buffering will be paused until the buffer status meets the condition of MIN\_BUFFER\_DURATION again. The default value is 300 seconds.

- **For HTTP Protocols** : For HTTP protocols, only properties defining buffering maximums, MAX\_BUFFER\_DURATION and MAX\_BUFFER\_RATE, are available. The properties work in the same way as for non-HTTP protocols. After being paused automatically, buffering will automatically resume after 10% of the buffer is exhausted. Note that when MAX\_BUFFER\_DURATION and MAX\_BUFFER\_RATE are both set, NexPlayer will apply the first maximum value that is met. For example, if the percentage set by MAX\_BUFFER\_RATE is passed first, the prefetch buffering will automatically pause even if the buffer is less full than the duration value set for MAX\_BUFFER\_DURATION.

## Properties

### ALWAYS_BUFFERING (120)

This is used to force NexPlayer to begin buffering as soon as all available audio frames have been processed, without regard to the state of the video buffer.

Under normal operation, when there are no audio frames left in the audio buffer, NexPlayer switches to buffering mode and temporarily suspends playback.

There is an exception if the video buffer is more than 60% full. In this case, NexPlayer will continue video playback even if there is no more audio available.

Setting this property to true(1) bypasses this exception and forces the system to go to buffering immediately if there are no audio frames left to play.

- **Default:** 0

### INITIAL_BUFFERING\_DURATION (9)

The number of milliseconds of media to buffer initially before beginning streaming playback (HLS, RTSP, etc.).

This is the initial amount of audio and video that NexPlayer buffers when it begins playback. To set this property separately, it must be set by calling setProperty after calling open() and before start() is called.

If further buffering is required later in the playback process, the value of the property `RE_BUFFERING_DURATION` will be used instead.

- **Unit:** msec (1/1000 sec)

- **Default:** 5000 (5 seconds)

### RE_BUFFERING\_DURATION (10)

The number of milliseconds of media to buffer if additional buffering is required during playback.

This is the amount of audio and video that NexPlayer buffers when the buffer becomes empty during playback (requiring additional buffering). After open() is called, this property can be set at any time during playback by calling setProperty.

For the initial buffering, the value of the property INITIAL\_BUFFERING\_DURATION is used instead.

- **Unit:** msec (1/1000 sec)

- **Default:** 5000 (5 seconds)

### PARTIAL_PREFETCH (519)

Sets whether or not to begin playback after a part of the TS file is downloaded.

By default, this property is set to 0 to download the first TS file completely to play content.

- **Default:** 0

- **Values:**

- 0 : Partial prefetch ignored; playback will begin after downloading the first TS file completely.
- 1 : Partial prefetch enabled; playback will begin after a part of the TS file is downloaded.

### PREFETCH_BUFFER\_SIZE (16)

The size of the prefetch buffer to prepare for playback.

If the buffer status satisfies either limit set by MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION, the filling of the prefetch buffer will be stopped even though there may be spare space still available in the prefetch buffer.

If this value is set to 20MB, 1/4 (5MB) is allocated to the past (content already played) and 3/4(15MB) is allocated to the future (content yet to be played).

?> Setting too large of a value here may lead to a large consumption of data packets under 3G or LTE network conditions.
 
- **Unit:** bytes

- **Default:** 50x1024x1024 (50MB)

### MAX_BUFFER\_DURATION (143)

The maximum duration of prefetch buffer to pause filling the buffer.

If the duration of content available in the filling prefetch buffer is greater than this value, filling of the buffer will be paused until the buffer status meets the condition of MIN\_BUFFER\_DURATION.

?> Note that when setting `MAX_BUFFER_DURATION` to a specific value, the value chosen must be at least twice the value of `RE_BUFFERING_DURATION`. If a smaller value is chosen, the value of `MAX_BUFFER_DURATION` will automatically be increased to twice the value of `RE_BUFFERING_DURATION`. For example, if `RE_BUFFERING_DURATION=5000` ms and one tries to set `MAX_BUFFER_DURATION` to 7000 ms, `MAX_BUFFER_DURATION` will automatically be set to 10000 ms instead.
 
- **Unit:** milliseconds

- **Default:** 300000 (300s)

### MIN_BUFFER\_DURATION (142)

The minimum duration of prefetch buffer to resume filling the buffer.

If the duration of content available in the filling buffer is less than this value, filling of the buffer will be resumed until the buffer status meets a condition set by either MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION.

- **Unit:** milliseconds (ms)

- **Default:** 30000 (30s)

### MAX_BUFFER\_RATE (141)

The maximum filled percentage of the prefetch buffer to pause filling the buffer.

If the prefetch buffer is more than this value percent full, filling the buffer will be paused until the buffer status meets the condition set by the property `MIN_BUFFER_RATE`.

- **Unit:** percent

- **Default:** 90 (90%)

### MIN_BUFFER\_RATE (140)

The minimum filled percentage of the prefetch buffer to resume filling the buffer.

If the prefetch buffer is less full than the value set by this property, the buffer will resume filling until the buffer status meets a condition set by either MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION.

- **Unit:** percent

- **Default:** 30 (30%)

### CONTINUE_DOWNLOAD\_AT\_PAUSE (561)

Sets whether or not to continue downloading data in pause state when playing content.

When this property is set, content data will continue to be downloaded even when NexPlayer is paused.

This property should be called after init and before calling open.

- **Default:** 0

- **Values:**

- **0:** Stop downloading in pause state.
- **1:** Continue downloading in pause state.

## API Reference

### NexPlayer.getBufferInfo

```java
int getBufferInfo(int iMediaStreamType, int iBufferInfoIdx)
```

Retrieves the specified buffer information item.

This method provides the ability to monitor the buffer conditions and returns the specified buffer information that has been requested.

**Buffer Info Indexes:** The following integer constants identify different buffer information items that are available; they are passed in the info\_index argument to specify which buffer information item the caller is interested in.

Note that CTS stands for "Current Time Stamp".

**Parameters**

| Name | Description | 
|---|---|
| iMediaStreamType| The type of media stream being received and buffered. This will be one of: MEDIA\_STREAM\_TYPE\_AUDIO, or MEDIA\_STREAM\_TYPE\_VIDEO.|
| iBufferInfoIdx | The integer index of the buffer information item to return. This is one of the NEXPLAYER\_BUFINFO\_INDEX\_ constants, listed below |

**Possible Values for iBufferInfoIdx**

| Name | Description | 
|---|---|
| NEXPLAYER\_BUFINFO\_INDEX\_BUFSIZE | Buffer size.|
| NEXPLAYER\_BUFINFO\_INDEX\_INITBUFSIZE | Initial buffering size.|
| NEXPLAYER\_BUFINFO\_INDEX\_INITBUFTIME | Initial buffering time.|
| NEXPLAYER\_BUFINFO\_INDEX\_BUFFEREDSIZE | Buffered size.|
| NEXPLAYER\_BUFINFO\_INDEX\_BUFRATE | (Buffered size)∗100/(Total Buffer size), or the percentage full that the buffer is.|
| NEXPLAYER\_BUFINFO\_INDEX\_FIRSTCTS | CTS of the first frame in buffer. (If there is no frame: 0xFFFFFFFF)|
| NEXPLAYER\_BUFINFO\_INDEX\_LASTCTS | CTS of the last frame in buffer. (If there is no frame: 0xFFFFFFFF)|
| NEXPLAYER\_BUFINFO\_INDEX\_DURATION | The total duration of frames in buffer.|
| NEXPLAYER\_BUFINFO\_INDEX\_FRAMECOUNT | The total count of the frames in buffer.|
| NEXPLAYER\_BUFINFO\_INDEX\_STATE | Buffering state (0: paused, 1: resumed).|

**Returns**
 
The integer value of the requested buffer information item.
