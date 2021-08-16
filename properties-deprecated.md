# Deprecated Options

#### AS_CINEMA\_SOUND\_AVAILABILITY (0x00050006)

Indicates whether or not the NexSound audio solution component, Cinema Sound, is available on this device.

As audio solution components are optional, this property can be checked for availability.

- **Type:** unsigned integer(read-only)

- **Values:**

- **0:** Device does not support Cinema Sound component.
- **1:** Device supports Cinema Sound component.

#### AS_EARCOMFORT\_AVAILABILITY (0x00050002)

Indicates whether or not the NexSound audio solution component, EarComfort, is available on this device.

As audio solution components are optional, this property can be checked for availability.

- **Type:** unsigned integer(read-only)

- **Values:**

- **0:** Device does not support EarComfort component.
- **1:** Device supports EarComfort component.

#### AS_MUSIC\_ENHANCER\_AVAILABILITY (0x00050005)

Indicates whether or not the NexSound audio solution component, Music Enhancer, is available on this device.

As audio solution components are optional, this property can be checked for availability.

- **Type:** unsigned integer(read-only)

- **Values:**

- **0:** Device does not support Music Enhancer component.
- **1:** Device supports Music Enhancer component.

#### AS_REVERB\_AVAILABILITY (0x00050003)

Indicates whether or not the NexSound audio solution component, Reverb, is available on this device.

As audio solution components are optional, this property can be checked for availability.

- **Type:** unsigned integer(read-only)

- **Values:**

- **0:** Device does not support Reverb component.
- **1:** Device supports Reverb component.

#### AS_STEREO\_CHORUS\_AVAILABILITY (0x00050004)

Indicates whether or not the NexSound audio solution component, Stereo Chorus, is available on this device.

As audio solution components are optional, this property can be checked for availability.

- **Type:** unsigned integer(read-only)

- **Values:**

- **0:** Device does not support Stereo Chorus component.
- **1:** Device supports Stereo Chorus component.
 
#### ENHANCED_SOUND\_AVAILABILITY (0x00050008)

Indicates whether or not the NexSound audio solution, speed control component, DTS audio solution headphoneX, and head tracking are available on this device.

As audio solutions components are optional in the NexPlayer SDK, this property can be used to check their availability.

- When this property is set equal to 1 (enabled), NexPlayer uses NexSound audio solution and speed control.
- When this property is set equal to 2 (enabled), NexPlayer uses DTS audio solution and headphone X.
- When this property is set equal to 4 (enabled), NexPlayer uses DTS audio solution and head tracking.

This property is related to the `notifyHeadsetState` method.

- **Type:** unsigned integer

- **Default:** 0 (Disabled/Not Available)

- **Values:**

- **0:** Disabled/Not Available. NexPlayer does not support any other sound effects.
- **1:** NexSound Speed Control/Available. NexPlayer supports NexSound audio solution and speed control.
- **2:** DTS Headphone X/Available. NexPlayer supports DTS audio solution and headphone X.
- **4:** DTS Head Tracking/Available. NexPlayer supports DTS audio solution and head tracking.

**See Also**
 
NexPlayer.notifyHeadsetState


#### NEW_TRACK\_SELECTION\_MODE (510)

Sets the track selection mode NexPlayer will use when playing content.

This property determines how a new track is selected when starting to play new Smooth Streaming content. Based on the mode set here, NexPlayer will prefer the specified range of tracks when selecting which to play first.

While the default setting of selecting high bitrate tracks will be acceptable generally, there may be certain circumstances in which it is preferable that a lower bitrate track be selected first, and this property offers that flexibility.

- **Type:** unsigned integer

- **Values:**

- 0: Based on the estimated bitrate when receiving the manifest file, NexPlayer selects a lower bitrate track than the estimated bitrate. For example, for track bitrates of 1, 2, 3, and 4Mbps, NexPlayer calculates a bitrate of 3.2Mbps, and thus selects the 3Mbps bitrate track.
- 1: Prefer high bitrate tracks.
- 2: Prefer mid-range bitrate tracks.
- 3: Prefer low bitrate tracks.

- **Default:** 1: Prefer high bitrate tracks.

#### SET_LIVEBACKOFF (504)

Sets the SmoothStreamingLiveBackOff property when playing Smooth Streaming content.

This property sets the duration of content (closest to live) that cannot yet be accessed or downloaded by the player.

It is like setting how long to wait before asking for the latest fragment in a live presentation, and thus basically set the played "live" point back from the actual live content available on the server.

The end-to-end latency of the player (what is being played "live" in the player compared to what is available live on the server) is at least the duration of LiveBackOff added to the duration set for LivePlaybackOffset with `SET_LIVEPLAYBACKOFFSET`.

- **Type:** unsigned int

- **Units:** milliseconds (ms)

- **Default:** 6000 (ms)

 
#### SET_LIVEPLAYBACKOFFSET (505)

Sets the `SmoothStreamingLivePlaybackOffset` property when playing Smooth Streaming content.

This property sets the duration away from the live position to start playback when joining a live presentation when the LiveView option is set to "Recent", but excludes theLiveBackOffduration (set by SET\_LIVEBACKOFF).

As a result, live content will be played behind the actual live position by a duration determined by both LiveBackOff and the value for LivePlaybackOffset set here.

Setting this property enables faster startup because it allows a buffer to be built up as fast as bandwidth will support (potentially faster than real-time), which creates a buffer against network jitter. It does however also increase end-to-end latency, which means what is played "live" in the player is farther behind the actual live playing point of the content.

- **Type:** unsigned int

- **Units:** milliseconds (ms)

- **Default:** 7000 (ms)


#### SUPPORT_APPLE\_HTTP (115)

If set to 1, enables Apple HTTP Live Streaming (HLS) support.

- **Type:** boolean

- **Default:** 1


#### SUPPORT_LOCAL (110)

If set to 1, enables local file playback support.

- **Type:** boolean

- **Default:** 1

#### SUPPORT_MS\_SMOOTH\_STREAMING (123)

If set to 1, this enables MS Smooth Streaming support.

- **Type:** boolean

- **Default:** 1

#### SUPPORT_PD (112)

If set to 1, enables progressive download support.

- **Type:** boolean

- **Default:** 1

#### SUPPORT_RDT (114)

If set to 1, enables Real Media Streaming support.

- **Type:** boolean

- **Default:** 0

#### SUPPORT_RTSP (111)

If set to 1, enables RTSP streaming support.

- **Type:** boolean

- **Default:** 0

> **Warning** This property is not supported in this API version.
 
#### SUPPORT_WMS (113)

If set to 1, enables Microsoft Windows Media Streaming support.

- **Type:** boolean

- **Default:** 0
