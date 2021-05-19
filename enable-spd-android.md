# ENABLED SPD ON ANDROID

## How SPD Feature works?

NexPlayer SPD feature technology allows you to play a video stream synchronously
on different devices using the DASH SPD value. This is also possible for HLS
streams by controlling the SPD value from the client-side.

## HOW TO ENABLE SPD IN THE SAMPLE APPLICATION

To get started we need an apk and at least two devices.
Steps to enable SPD:


- Go to the three dots → Settings → SPD Settings.

Here we have several fields that depending on our needs we will have to configure.

**SPD:** Enabled (this field is used to enable and disable SPD).

- *Note:* The other fields will be enabled when you enable the SPD option.

**SPD Delay Time:** value between 500.0 ms and 20,000.0ms (default 2000.0ms).

**SPD Sync Range:** value between 100.0 ms and 2000.0ms (default 300.0ms).

**SPD Too Much Difference Time:** value between 2000.0and 10,000.0 ms (default
5000.0ms).

**Sync to Device UTC:** Enable or disable. This field takes as reference the UTC time
(disabled by default).

![](1.JPG)


Once we have configured what we need, we will play the content with SPD in the
section.

Streaming → GO TO URL (at the bottom) → put the URL in the “Stream URL

SPD is highly dependent on the internet speed and the configuration of the manifest.

It is important to know that we have to make sure that we have SPD activated. On
the other hand, to check that the content that we use has SPD it has to have the
following tag in the manifest:

**_suggestedPresentationDelay="PT5S"_**

This means that it will have a delay of 5 seconds.

Example:

![](2.JPG)

### Limitations


- Only works with live content.
- Device time should be adjusted correctly, incorrect device time or setting it
manually might break the logic. This can be handledby using server time but
the synchronisation won’t be precise as device time as server time is given in
seconds, not in milliseconds as device time.
- Setting a very low SPD value for the stream might affect smooth playback
experience as it won’t allow the player to create enough buffer.

TEST LINK:

[https://akamaibroadcasteruseast.akamaized.net/cmaf/live/657078/akasource/out.mpd]()


#### *To configure SPD from the code we have to add the next properties:

# NexPlayer Synchronization Feature

## How to enable synchronization feature?


NexPlayer synchronization can be enabled by setting the following property:


`mNexPlayer.setProperty(NexPlayer.NexProperty.ENABLE_SPD_SYNC_TO_GLOBAL_TIME, 1);`


To set the SPD value from the client side for both DASH and HLS you can set the
SPD value per property ( `SET_PRESENTATION_DELAY` or 590) as shown below:


`mNexPlayer.setProperty (NexProperty.SET_PRESENTATION_DELAY,mPrefData.mSPDValue);`

Note that if the value of `SET_PRESENTATION_DELAY `is too large, the player may not
find the delayed segment provided by the live content server.

### Advanced configuration


You can control the synchronization behaviour further by adjusting the below
properties.

#### `ENABLE_SPD_SYNC_TO_DEVICE_TIME`


Enables synchronization to device UTC for more accurate behaviour.

`mNexPlayer.setProperty(NexPlayer.NexProperty.ENABLE_SPD_SYNC_TO_DEVICE_TIME, 1);`

Default: 0

Values:

- 0: Disabled device UTC
- 1: Enabled device UTC


#### `SET_SPD_SYNC_DIFF_TIME`

If the current playback is not more synchronized than this value, the player will speed
up playback and make sync.

`mNexPlayer.setProperty(NexPlayer.NexProperty.SET_SPD_SYNC_DIFF_TIME, 100);`

Unit: msec (1/1000 sec)

Default: 300 (300 msec)

#### `SET_SPD_TOO_MUCH_DIFF_TIME`

If playback is out of sync than this value, the player will jump to synchronize the
video rather than make it by speeding.

`mNexPlayer.setProperty(NexPlayer.NexProperty.SET_SPD_TOO_MUCH_DIFF_TIME,5000);`

Unit: msec (1/1000 sec)

Default: 5000 (5 seconds)

## Things to consider


- You should make sure suggestedPresentationDelay ispresent in DASH
manifest otherwise synchronisation won't work.
- For HLS, you should set `SET_PRESENTATION_DELAY` property as mentioned
above.
- You should make sure there is enough distance from the live edge to provide
a smooth playback which should be adjusted with
*suggestedPresentationDelay* and `SET_PRESENTATION_DELAY` properties. If
there is not enough space to buffer from the live edge, playback might be
effected.

**You can find our updated documentation on our Github page:**

[Updated SPD documentation](https://github.com/NexPlayer/Android-SDK/blob/master/synchronization.md)

