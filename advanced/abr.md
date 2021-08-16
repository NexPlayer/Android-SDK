# Controlling the ABR

There are a wide array of properties that can be adjusted to control the behavior of various aspects of the player. Properties are identified with an integer identifier from the NexProperty enumeration.

## Properties

### SUPPORT_ABR (116)

If set to 1, enables Adaptive Bit Rate (ABR) support.

- **Type:** boolean

- **Default:** 1


### MAX_BW (117)

When usinG ABR, this is the maximum allowable bandwidth.

Any track with a bandwidth greater than this value will not be played back.

?> To take effect, this property should be set before calling `NexPlayer.open.NexPlayer.setProperty(MAX_BW)` can be used to set the bandwidth limit for initial segments of content, which are downloaded shortly after NexPlayer opens. To change the maximum allowable bandwidth dynamically while content is playing, please call the method changeMaxBandWidth instead.
 
This property should be set to zero for no maximum.

- **Unit:** bps (bits per second)

- **Default:** 0 (no maximum)

### MIN_BW (516)

When using ABR, this is the minimum allowable bandwidth.

Any track with a bandwidth smaller than this value will not be played back.

?> **Note** To dynamically set a minimum bandwidth allowed while content is playing, please call the method `NexABRController::changeMinBandWidth()` instead. This property should be set to zero for no minimum.
 
- **Unit:** bps (bits per second)

- **Default:** 0 (no minimum)

### MAX_HEIGHT (126)

Limits the maximum height (in pixels) of the video tracks that can be selected during streaming play.

This is used to prevent NexPlayer from attempting to play tracks that are encoded at too high a resolution for the device to handle effectively. NexPlayer will instead select a track with a lower resolution.

- **Unit:** pixels

- **Default:** 0x7FFFFFFF

### MAX_WIDTH (125)

Limits the maximum width (in pixels) of the video tracks that can be selected during streaming play.

This is used to prevent NexPlayer from attempting to play tracks that are encoded at too high a resolution for the device to handle effectively. NexPlayer will instead select a track with a lower resolution.

- **Unit:** pixels

- **Default:** 0x7FFFFFFF

### ENABLE_FRAMERATE\_RESTRICTION (588)

This makes sure that the currently playing track is not switched to another one with a lower frame rate when switching to a track with a higher Bitrate.

- **Default:** 0

- **Values:**

- **0:** Disable the frame rate restriction.
- **1:** Enable the frame rate restriction.

### ENABLE_HTTPABRTRACKCHANGE\_CALLBACK (583)

Indicates whether or not an ABR track switch callback is available.

- **Default:** 0

- **Values:**

- **0:** Disable an ABR track switch callback.
- **1:** Enable an ABR track switch callback.

### START\_NEARESTBW (555)

Sets a target bandwidth (before playing the content) when selecting which track to play as playback starts.

While NexPlayer automatically chooses an ideal track to play based on several factors including device capability and network conditions, there may be situations in which starting playback from a track with a bandwidth near a particular bandwidth is desired.

When this property is set, NexPlayer selects and starts playing the track in content that has the bandwidth closest to the set bandwidth value, initially ignoring other factors.

Note that as playback continues, the track played may change as NexPlayer judges all factors that influence streaming playback and chooses the best option.

This property should be called after init but before calling open.

- **Unit:** bps (bits per second)

- **Default:** null

- **Values:** The target bandwidth value, in bits per second (bps). Note that if `START_NEARESTBW` is set to 0, NexPlayer will play normally, as if this property has not been set.

### ENABLE_TRACKDOWN (131)

Allows NexPlayer to switch to a lower bandwidth track if the resolution or bitrate of the current track is too high for the device to play smoothly.

Under normal operation, NexPlayer switches tracks based only on current network conditions. When this property is enabled, NexPlayer will also switch to a lower bandwidth track if too many frames are skipped during playback.

This is useful for content that is targeted for a variety of devices, some of which may not be powerful enough to handle the higher quality streams.
 
The `TRACKDOWN_VIDEO_RATIO` property controls the threshold at which the track change will occur, if frames are being skipped.

- **Default:** 0

- **Values:**

- 0: Normal behavior (switch based on network conditions only)
- 1: Switch based on network conditions and device performance.

### TRACKDOWN_VIDEO\_RATIO (132)

This property controls the ratio of skipped frames that will be tolerated before a track change is forced, if `ENABLE_TRACKDOWN` is enabled.

The formula used to determine if a track switch is necessary is:

```
(^100) *(RenderedFrames / DecodedFrames) < TRACKDOWN_VIDEO_RATIO
```

In other words, if this property is set to 70, and `ENABLE_TRACKDOWN` is set to 1, NexPlayer will require that at least 70% of the decoded frames be displayed. If less than 70% can be displayed (greater than 30% skipped frames), then the next lower bandwidth track will be selected.

A performance-based track switch **permanently** limits the maximum bandwidth of tracks that are eligible for playback until the content is closed. For this reason, setting this ratio higher than the default value of 70 is strongly discouraged (This differs from the bandwidth-based algorithm, which continuously adapts to current network bandwidth).

**Range:** 0 to 100

- **Default:** 70

### HLS_RUNMODE (133)

Controls the algorithm used for bitrate switching when playing an HLS stream.

- **Default:** 0

- **Values:**

- **0:** Use a more aggressive algorithm: up-switching happens sooner.
- **1:** Use a more conservative algorithm: up-switching happens only if a significant amount of extra bandwidth is available beyond that required to support the given bitrate.

## APIs

### NexABRController.IABREventListener Interface

This interface must be implemented in order for the application to receiveABRControlevents from NexABRController.

NexABRController will call the methods provided in this interface automatically during playback to notify the application when various ABRControl events have occurred.

In most cases, the handling of these events is optional; NexPlayer will continue to play content back normally without the application doing anything special in response to the events received.
 
#### void onMinMaxBandWidthChanged (NexErrorCode result, int minBwBps,  int maxBwBps) 

This method will be called by the NexABRController when either the minimum or maximum bandwith allowed for streaming content is changed.

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

#### void onTargetBandWidthChanged (NexErrorCode result, int reqBwBps, int selBwBps)

This method will be called by the NexABRController when the target bandwidth for streaming content is changed.

For example, if content has three tracks at bandwidths of 500k, 900k, and 1200k and the applications calls set TargetBandwidth to set a target of 700k with the target option `BELOW`, `reqBwBps` will be 700,000 and `selBwBps` will be 500,000.

**Parameters**

| Name  | Description  | 
|---|---|
| result | NexErrorCode object for the specified error code.|
| reqBwBps | The requested target bandwidth to select a track, in bps (bits per second)|
| selBwBps | The actual bandwidth of the track selected, in bps (bits per second)|

### NexPlayer.IHTTPABRTrackChangeListener Interface

This interface must be implemented in order for the application to receive an ABR Track switch event from NexPlayer.

NexPlayer will call the methods provided in this interface automatically during playback to notify the application when an ABR Track switch event has occurred.

In most cases, the handling of this event is optional; NexPlayer will continue to play content normally without the application doing anything special in response to the event received.

> **Note** To use the method defined by this interface, NexProperty.ENABLE\_HTTPABRTRACKCHANGE\_CALLBACK should be enabled before calling open.

#### int onHTTPABRTrackChange (NexPlayer mp, int param1, int param2, int param3)

This method will be called by the NexPlayer engine when the ABR track is switched.

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object generating the event.|
| param1 | The current network bandwidth.|
| param2 | The current track bandwidth.|
| param3 | The target track bandwidth.|

**Returns**

The exact track bandwidth that the user wants to set to forcibly.

### NexABRController Class

This class allows applications to control and use ABR-related methods within the NexPlayer SDK.

An instance of *NexABRController* can be called once NexPlayer has been created and initialized.

**Classes**

- `interface IABREventListener`    
    This interface must be implemented in order for the application to receiveABRControlevents from *NexABRController*.
- `enum SegmentOption`    
    This enum defines the options possible for how NexPlayer should handle existing buffered content as a track
    changes (due to a set target bandwidth).
- `enum TargetOption`    
    This enumeration defines the possible options for how an application should use a target bandwidth set.


#### NexABRController(NexPlayer mp)

Sole constructor for *NexABRController*.

The application must create an instance of the *NexABRController* class to control ABR-related methods which for example change the minimum/maximum allowed bandwidths or the target bandwidth for streaming content with multiple tracks.

 
#### NexErrorCode changeMaxBandWidth(int maxBwBps)

This method sets the maximum bandwidth for streaming playback dynamically during playback.

This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track over the maximum bandwidth when determining whether a track change is appropriate, even if it detects more bandwidth available.

**Parameters**

| Name     | Description                                 |
|----------|-------------------------|
| maxBwBps | Maximum bandwidth in bps (bits per second). |

**Returns**

NexErrorCode

#### NexErrorCode changeMinBandWidth(int minBwBps)

This method sets the minimum bandwidth for streaming playback dynamically during playback.

This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum bandwidth when determining whether a track change is appropriate, even if it detects less bandwidth available.

**Parameters**

| Name     | Description                                 |
|----------|-------------------------|
| minBwBps | Minimum bandwidth in bps (bits per second). |

**Returns**

NexErrorCode

 
#### NexErrorCode changeMinMaxBandWidth(int minBwBps, int maxBwBps)

This method sets the minimum and maximum bandwidth for streaming playback dynamically during playback.

This applies in cases where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum, and over the maximum bandwidth when determining whether a track change is appropriate, even if it detects less, and more bandwidth available.

**Parameters**
 
| Name     | Description                                 |
|----------|-------------------------|
| minBwBps | Minimum bandwidth in bps (bits per second). |
| maxBwBps | Maximum bandwidth in bps (bits per second). |

**Returns**

NexErrorCode

#### NexErrorCode setABREnabled(boolean enabled)

This method sets whether ABR methods should be used or not.

In general, NexPlayer plays streaming content, including content with multiple tracks at different bandwidths such as HLS, by choosing the optimal track according to network conditions and device performance. This is the default behavior of NexPlayer and this occurs when ABR is enabled (or calling *setABREnabled* with the parameter enabledset to *TRUE*).

However, there may be instances when an application may want to set limits on which tracks should be selected and played by NexPlayer in order to provide a specific user experience, and to force NexPlayerto stay on a particular bandwidth track, regardless of network conditions. In cases like this, in order to keep playing a track at a target bandwidth (set with *setTargetBandWidth*) this method must be called to disable NexPlayer’s ABR behavior (with the parameter *enabled* set to *FALSE*).

?> This method must be called with *enabled* set to *FALSE* before calling *setTargetBandWidth* if the application should continue playing the target bandwidth regardless of network conditions.
 
**Parameters**

| Name    | Description                                                                                                                                                                                                      |
|---------|--------------------------|
| enabled | `TRUE` : ABR enabled. NexPlayer will handle track changes automatically. <br/>`FALSE` : ABR disabled. NexPlayer will continue playing the target bandwidth track set, regardless of network conditions. |

**Returns**

NexErrorCode

#### void setIABREventListener(IABREventListener listener)

This method sets and registers an *IABREventListener* listener for the application playing content with NexPlayer.

**Parameters**

 
| Name     | Description           |
|----------|-----------------------|
| listener | `IABREventListener` |


#### NexErrorCode setTargetBandWidth(int targetBwBps, SegmentOption segOption, TargetOption targetOption)

This method sets the target bandwidth for streaming playback dynamically during playback.

This method should be called after `NexPlayer.open()`. This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the target bandwidth and over the target bandwidth when determining whether a track change is appropriate, even if it detects less and more bandwidth available.

**Parameters**

| Name         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|--------------|----------------|
| targetBwBps  | Target bandwidth in bps (bits per second).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 
| segOption    | One of the following SegmentOption values, indicating how to handle buffered content when the track changes: <br/> - **Default** : Default (NexPlayer will decide between QUICKMIX (changing tracks     quickly) and LATEMIX (playing buffered content and changing tracks more slowly)). <br/> **QUICKMIX** : NexPlayer will clear the buffer as much as possible and will start to download new track so user can see a new track faster. <br/> **LATEMIX** : NexPlayer will preserve and play the content segments already buffered and will download a new track. |
| targetOption | How to use the target bandwidth value set. One of the following TargetOption options: <br/> - **Default** : Default target option (BELOW)<br/> **BELOW** : Select a track with a bandwidth below the target bandwidth. <br/> **ABOVE** : Select a track with a bandwidth above the target bandwidth. <br/> **MATCH** : Select the track that has a bandwidth that matches the target set; otherwise send an error and no new target bandwidth is selected.                                                                                                                          |

**Returns**

NexErrorCode

#### int changeMaxBandWidth (int iMaxBandWidth)

This method sets the maximum bandwidth for streaming playback dynamically during playback.

?> It is recommended that the method `NexABRController::changeMaxBandWidth()` be used to set maximum bandwidth allowed instead of using this method.

?> To dynamically change the maximum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the maximum bandwith can also be set before play begins by setting the `NexProperty,MAX_BW`, with `NexPlayer.setProperty(MAX_BW)`.
 
This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track over the maximum bandwidth when determining whether a track change is appropriate, even if it detects more bandwidth available.

If this method returns successfully, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED` Then, if the method `onStatusReport()` returns successfully, the maximum bandwidth will be changed.

Note that to remove a maximum that has been set with this method (so that NexPlayer will again consider all tracks regardless of bandwidth), set iMaxBandWidth to 0x00000000.

**Parameters**

| Name | Description | 
|---|---|
| iMaxBandWidth | Maximum bandwidth in kbps (kilobits per second). To reset to no maximum bandwidth, set iMaxBandWidth = 0x00000000.| 

**Returns**

Zero if successful, otherwise non-zero if there was an error.

#### native int changeMaxBandWidthBps (int maxBwBps)

This method sets the maximum bandwidth for streaming playback dynamically during playback.

?> It is recommended that the method `NexABRController::changeMaxBandWidth()` be used to set maximum bandwidth allowed instead of using this method.
 
?> To dynamically change the maximum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the maximum bandwith can also be set before play begins by setting the `NexProperty,MAX_BW`, with `NexPlayer.setProperty(MAX_BW)`.
 
This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track over the maximum bandwidth when determining whether a track change is appropriate, even if it detects more bandwidth available.

If this method returns successfully, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED` Then, if the method `onStatusReport()`
returns successfully, the maximum bandwidth will be changed.

Note that to remove a maximum that has been set with this method (so that NexPlayer will again consider all
tracks regardless of bandwidth), set `maxBwBps` to `0x00000000`.

**Parameters**

| Name | Description | 
|---|---|
| maxBwBps | Maximum bandwidth in bps (bits per second). To reset to no maximum bandwidth, set maxBwBps = 0x00000000.| 

**Returns**

Zero if successful, otherwise non-zero if there was an error.

  
#### native int changeMaxResolution (int maxWidth, int maxHeight)

This method changes the maxWidth and maxHeight while playing content.

This only works on HLS content, and switching to a track with bigger maxWidth and maxHeight will not be possible. If the currently playing track has width and height values bigger than maxWidth and maxHeight, it will switch to a track with smaller than those.

**Parameters**
 
| Name | Description | 
|---|---|
| maxWidth | Maximum width.| 
| maxHeight | Maximum height.| 

**Returns**

Zero for success, or a non-zero NexPlayer error code in the event of a failure.

#### int changeMinBandWidth (int iMinBandWidth)

This method sets the minimum bandwidth for streaming playback dynamically during playback.

?> It is recommended that the method `NexABRController::changeMinBandWidth()` be used to set
minimum bandwidth allowed instead of using this method.
 
?> To dynamically change the minimum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the minimum bandwith can also be set before play begins by setting the `NexProperty,MIN_BW`, with `NexPlayer.setProperty(MIN_BW)`.
 
This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum bandwidth when determining whether a track change is appropriate, even if it detects less bandwidth available.

If this method returns successfully, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED`. Then, if the method `onStatusReport()` returns successfully, the minimum bandwidth will be changed.

Note that to remove a minimum that has been set with this method (so that NexPlayer will again consider all tracks regardless of bandwidth), set `iMinBandWidth` to `0x00000000`.

**Parameters**

| Name | Description | 
|---|---|
| iMinBandWidth | Minimum bandwidth in kbps (kilobits per second). To reset to no minimum bandwidth, set iMinBandWidth = 0x00000000.| 

**Returns**

Zero if successful, otherwise non-zero if there was an error.

 
#### native int changeMinBandWidthBps(int minBwBps)

This method sets the minimum bandwidth for streaming playback dynamically during playback.

?> It is recommended that the method NexABRController::changeMinBandWidth() be used to set
minimum bandwidth allowed instead of using this method.
 
?> To dynamically change the minimum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the minimum bandwith can also be set before play begins by setting the `NexProperty.MIN_BW`, with `NexPlayer.setProperty(MIN_BW)`.
 
This applies in cases with content where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum bandwidth when determining whether a track change is appropriate, even if it detects less bandwidth available.

If this method returns successfully, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED`. Then, if the method `onStatusReport()` returns successfully, the minimum bandwidth will be changed.

Note that to remove a minimum that has been set with this method (so that NexPlayer will again consider all tracks regardless of bandwidth), set `minBwBps` to `0x00000000`.

**Parameters**

| Name | Description | 
|---|---|
| minBwBps | Minimum bandwidth in bps (bits per second). To reset to no minimum bandwidth, set minBwBps = 0x00000000| 

**Returns**

Zero if successful, otherwise non-zero if there was an error.

#### int changeMinMaxBandWidth (int iMinBandWidth, int iMaxBandWidth)

This method sets the minimum and maximum bandwidth for streaming playback dynamically during playback.

?> It is recommended that the method `NexABRController::changeMinMaxBandWidth()` be used to set minimum and maximum bandwidths allowed instead of using this method. To dynamically change the minimum and maximum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the minimum, and maximum bandwith can also be set before play begins by setting the NexProperty `MAX_BW`, with `NexPlayer.setProperty(MAX_BW)`. `MIN_BW`, with `NexPlayer.setProperty(MIN_BW)`.
 
This applies in cases where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum, and over the maximum bandwidth when determining whether a track change is appropriate, even if it detects less, and more bandwidth available.

If this method returns success, the method `onStatusReport()` will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED` Then, if the method `onStatusReport()` returns success, the minimum and maximum bandwidth will be changed.

Note that to remove a minimum and maximum that has been set with this method (so that NexPlayer will
again consider all tracks regardless of bandwidth), set both of iMinBandWidth, and iMaxBandWidthto
0x00000000.

**Parameters**

| Name | Description | 
|---|---|
| iMinBandWidth | Minimum bandwidth in kbps (kilobits per second). To reset to no minimum bandwidth, iMinBandWidth= 0x00000000|
| iMaxBandWidth | Maximum bandwidth in kbps (kilobits per second). To reset to no maximum bandwidth, iMaxBandWidth= 0x00000000| 

**Returns**

Zero if successful, otherwise non-zero if there was an error.

#### native int changeMinMaxBandWidthBps (int minBwBps, int maxBwBps)

This method sets the minimum and maximum bandwidth for streaming playback dynamically during playback.

?> It is recommended that the method `NexABRController::changeMinMaxBandWidth()` be used to
set minimum and maximum bandwidth values instead of using this method.
 
?> To dynamically change the minimum and maximum bandwidth in the middle of playback, please use this method. To take effect, this method should be called after calling NexPlayer.open. Note that the minimum, and maximum bandwith can also be set before play begins by setting the NexProperty, `MAX_BW`, with `NexPlayer.setProperty(MAX_BW)`. `MIN_BW`, with `NexPlayer.setProperty(MIN_BW)`.
 
This applies in cases where there are multiple tracks at different bandwidths (such as in the case of HLS). The player will not consider any track under the minimum, and over the maximum bandwidth when determining whether a track change is appropriate, even if it detects less, and more bandwidth available.

If this method returns success, the method onStatusReport() will be called with a msg parameter `NEXPLAYER_STATUS_REPORT_MINMAX_BANDWIDTH_CHANGED` Then, if the method `onStatusReport()` returns success, the minimum and maximum bandwidth will be changed.

Note that to remove a minimum and maximum that has been set with this method (so that NexPlayer will again
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
 
#### native int enableTrack (int enableoption)

This method enables the disabled tracks due to temporary content and performance issues. It enables the disabled tracks due to temporary content issues (download fail (ex. 404, 502 error), playlist or response data from the server parsing failing ) and performance issues (decoding & rendering performances).

!> This is only supported in HLS and DASH contents.
 
**Parameters**

| Name | Description | 
|---|---|
| enableoption | `NEXPLAYER_TRACK_ENABLE_OPTION_DISABLED_TEMPORARY` <br/> `NEXPLAYER_TRACK_ENABLE_OPTION_DISABLED_PERFORMANCE`|

**Returns**

Zero if successful or a non-zero error code.