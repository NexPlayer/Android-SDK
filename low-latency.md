# Low Latency

Low latency technology can make the user view the live content as close to real-time as possible.
### How to enable low latency mode

You can enable the low latency mode by using the below properties.

```java
mNexPlayer.setProperty(NexProperty.LIVE_VIEW_OPTION, NexProperty.LIVE_VIEW_LOW_LATENCY);
mNexPlayer.setProperty(NexProperty.PARTIAL_PREFETCH, 1);
```		       
### How to adjust the latency

You can further configure and optimise the playback by using these options:
#### Buffering Option 1

Manual Mode The latency value is set by `INITIAL_BUFFERING_DURATION` and `RE_BUFFERING_DURATION` of NexProperty. It should set the reliable value depending on the bitrate of content and network environment.

```java          
mNexPlayer.setProperty(NexPlayer.NexProperty.LOW_LATENCY_BUFFER_OPTION, NexPlayer.NexProperty.
LOW_LATENCY_BUFFEROPTION_NONE);
```

- **Case 1 :** For **Ultra-Low Latency** This mode would be suitable for a managed network maintaining constant bandwidth(ex. Video services based on broadband). The latency might be around
1000ms. 

```java    
mNexPlayer.setProperty(NexPlayer.NexProperty.INITIAL_BUFFERING_DURATION, 500);
mNexPlayer.setProperty(NexPlayer.NexProperty.RE_BUFFERING_DURATION, 500);
```  

?> Buffering may frequently occur when bandwidth (Throughput) is not sufficient to deliver a
segment or chunk in time.
					
			
- **Case 2 :** For Low Latency This mode would be suitable for public networks such as WiFi and LTE. The latency might be around 3000ms. 

```java                
mNexPlayer.setProperty(NexPlayer.NexProperty.INITIAL_BUFFERING_DURATION, 2000);
mNexPlayer.setProperty(NexPlayer.NexProperty.RE_BUFFERING_DURATION, 2000);
```    
		
?> Buffering will rarely occur, but the latency will be slightly longer than the initial buffering time you set up.
			
	
- **Case 3 :** Adjust latency for HLS. In the case of HLS, the player has a disadvantage in low latency perspective than DASH:
	- The player should reload the playlist in order to figure out the URL for the next segment.
	- According to the HLS spec., the player MUST wait for at least the duration of the last segment in the Playlist before attempting to reload the Playlist file again.
	- HLS does not have the availabilityStartTime of the segment that is defined in DASH. Therefore, the player does not know when the next segment becomes available. For this reason, we would recommend setting the buffering time to a little bit longer value than the target duration. If the target duration is 2 seconds, then we recommend setting the buffering time as below. Otherwise, buffering may occur frequently.

```java
mNexPlayer.setProperty(NexProperty.INITIAL_BUFFERING_DURATION, 4000);
mNexPlayer.setProperty(NexProperty.RE_BUFFERING_DURATION, 4000);
```

#### Buffering Option 2 

Auto Buffer Mode. The latency value is calculated by the player at runtime. During playback, the latency may increase or decrease because it may change depending on the network environment. Example :

```java
mNexPlayer.setProperty(NexProperty.LOW_LATENCY_BUFFER_OPTION, NexProperty. LOW_LATENCY_BUFFEROPTION_AUTO_BUFFER);
```

#### Buffering Option 3

Constant Buffer Mode. The latency value is calculated by the player at the beginning of playback and maintains the value unchanged during playback. The latency increases more than when using Auto Buffer Mode, but the rebuffering will be reduced and try to maintain constant latency after rebuffering. 

Example :

```java
mNexPlayer.setProperty(NexProperty.LOW_LATENCY_BUFFER_OPTION, NexProperty. LOW_LATENCY_BUFFEROPTION_CONST_BUFFER);
```

### Syncronization option

You can control the behaviour of the playback by setting the `LOW_LATENCY_SYNC_CONTROL_OPTION` property. By default it works in `LOW_LATENCY_CONTROL_SEEK` mode.

Example:

```java
mNexPlayer.setProperty(NexProperty.LOW_LATENCY_SYNC_CONTROL_OPTION, NexProperty. LOW_LATENCY_SYNC_CONTROL_SEEK);
```

- `LOW_LATENCY_SYNC_CONTROL_SEEK`: When the latency rate increases, the latency rate is reduced to the Seek function of the player.

- `LOW_LATENCY_SYNC_CONTROL_SPEEDCONTROL`: When the latency rate increases, it adjusts the playback rate at 1.1x playback speed or slowing down to 0.9x to keep the synchronization

## Properties

### LIVE_VIEW_OPTION

Live HLS playback option.

> Note: When EXT-X-PROGRAM-DATE-TIME exists, playback will start from the first segment that is matching with the current time. 

**Type**: unsigned integer

- **Default**: LIVE_VIEW_RECENT

- **Values:**

- **LIVE_VIEW_RECENT (0x00000000):** Starts playback from the 3rd segment from the last. For example, if manifest have 1.ts, 2.ts, 3.ts, 4.ts, 5.ts then playback will start from the beginning of 3.ts.

- **LIVE_VIEW_RECENT_BYTARGETDUR (0x00000001):** Start playback from the most recently received media segement (.ts) files, based on the value set for the EXT-X-TARGETDURATION tag in the HLS live playlist. (The player will begin playback at the media segment that immediately precedes the media segment that is three times (x3) the target duration before the latest media segment file loaded). As a concrete example, if the target duration is set to 12 seconds and the total duration of currently loaded media segments is 48 seconds, playback will begin at the media file that immediately precedes the media segment with the timestamp at 12 (48-36) seconds. If this example HLS playlist includes media segment files 1.ts (duration of 10 seconds), 2.ts (9 sec), 3.ts (11 sec), 4.ts (10 sec), and 5.ts (8 sec), then playback will begin at the first media segment, 1.ts, because it immediate precedes the 2.ts segment (where the timestamp at 12 seconds occurs).

- **LIVE_VIEW_FIRST (0x00000002):** Unconditionally start HLS playback from the first entry in the HLS playlist.

- **LIVE_VIEW_LOW_LATENCY (0x00000003):** Playback starts from a position close to real-time and frame skipping may occur during playback to maintain low latency.

### PARTIAL_PREFETCH

Sets whether or not to begin playback after a part of the TS file is downloaded.  
By default, this property is set to 0 to download the first TS file completely to play content.

**Type**: boolean

- **Default**: 0

**Values**:
- **0:** Partial prefetch ignored; playback will begin after downloading the first TS file completely.
- **1:** Partial prefetch enabled; playback will begin after a part of the TS file is downloaded.

### INITIAL_BUFFERING_DURATION

The number of milliseconds of media to buffer initially before beginning streaming playback (HLS, RTSP, etc.).  
This is the initial amount of audio and video that NexPlayer buffers when it begins playback. To set this property separately, it must be set by calling setProperty after calling open() and before start() is called.  
If further buffering is required later in the playback process, the value of the property `RE_BUFFERING_DURATION` will be used instead.

**Type**: unsigned integer

**Unit**: msec (1/1000 sec)

- **Default**: 5000 (5 seconds)

### RE_BUFFERING_DURATION

The number of milliseconds of media to buffer if additional buffering is required during playback.  
This is the amount of audio and video that NexPlayer buffers when the buffer becomes empty during playback (requiring additional buffering). After open() is called, this property can be set at any time during playback by calling setProperty.  
For the initial buffering, the value of the property `INITIAL_BUFFERING_DURATION` is used instead.

**Type**: unsigned integer

**Unit**: msec (1/1000 sec)

- **Default**: 5000 (5 seconds)

### LOW_LATENCY_SYNC_CONTROL_OPTION

Set a low latency playback control option.

**Type**: unsigned integer

- **Default**: LOW_LATENCY_CONTROL_SEEK

**Values**

- **LOW_LATENCY_SYNC_CONTROL_SEEK:** When the latency rate increases, the latency rate is reduced to the Seek function of the player.

- **LOW_LATENCY_SYNC_CONTROL_SPEEDCONTROL:** When the latency rate increases, it adjusts the regeneration rate at 1.1x playback speed, slowly reducing the latency rate.