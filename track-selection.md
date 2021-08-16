# Track Selection

Certain streaming protocols provide multiple audio and video streams of the same content which are generally intended to be selected by the user. NexPlayer provides the `setMediaStream` API to allow these streams to be selected from the User Interface while content is being played.

The full list of available streams (if any) for particular content can be found in the **mArrStreamInformation** array in NexContentInformation.

There are three possible use cases available:

1. **A variant playlist with alternative audio** : Audio and video are delivered in separate streams or groups of tracks. In this case, video and audio can be selected independently. For example, there could be two different audio tracks (different languages) for video stream A, which includes multiple tracks to be selected internally by the player by adaptive bitrate streaming. The audio tracks should be selected by the user while the player will display the appropriate video track based on network conditions and the device.

2. **A variant playlist with alternative video** : Each track contains both audio and video, but alternative video streams are available (for example different camera angles or views of the same content). In this case, the same audio is included in each track, and the user chooses which video stream to display. Tracks within a stream are selected internally based on network conditions and the device but the user can change video streams from the UI.

3. **A combination of a variant playlist with alternative video and audio** : This use case is a combination of cases 1 and 2, where the main video stream provides video tracks at different bitrates but INCLUDING the same audio, and separate audio tracks are available for optional language selection. To play the alternative audio tracks, the user selects them from the UI.

This information is presented in the following format:

* NexContentInformation
	* NexStreamInformation
		* NexTrackInformation

**Selecting track using setTargetBandWidth**
		
Alternatively you can use the setTargetBandWidth API to change the track:

```java
int targetBW = streamInfo.mArrTrackInformation[selectedTrack].mBandWidth;
mABRController.setTargetBandWidth(targetBW, NexABRController.SegmentOption.DEFAULT, NexABRController.TargetOption.MATCH);
```

The different params you can use in method *mABRController.setTargetBandWidth(targetBW, segOption, targetOption)* are the following:

* **targetBW** - the target bandwidth in bps (bits per second)
* NexABRController.SegmentOption - This option will indicate how to handle buffered content when the track changes:
	* - **Default**: NexPlayer will decide between Quickmix (changing tracks quickly) and LateMix (playing buffered content and changing tracks more slowly).
	* **QUICKMIX**: NexPlayer will clear the buffer as much as possible and will start to download new track so the user can see a new track faster.
	* **LATEMIX**: NexPlayer will preserve and play the content segments already buffered and will download a new track.
* NexABRController.TargetOption:
	* - **Default**: Default target option (BELOW).
	* **BELOW**: Select a track with a bandwidth below the target bandwidth.
	* **ABOVE**: Select a track with a bandwidth above the target bandwidth.
	* **MATCH**: Select the track that has a bandwidth that matches the target set; otherwise send an error and no new target bandwidth is selected.


## API Reference

### NexPlayer.setMediaStream

```java
int setMediaStream (int iAudioStreamId, int iTextStreamId, int iVideoStreamId, int iVideoCustomAttrId)
```

For media with multiple streams, this method selects the streams that will be presented to the user.

This method should be called to set a specific media stream (video, audio, or text) while NexPlayer is playing content with multiple streams. To have NexPlayer prefer text streams in a particular language before playing content, the property `PREFER_LANGUAGE` should be set instead.

The full list of available streams (if any) can be found in the mArrStreamInformation array in NexContentInformation. Each stream is either an audio stream or a video stream, and one of each may be selected for presentation to the user. Please see Multi-Audio and Multi-Video Stream Playback for more explanation.

Some streams, for example in Smooth Streaming, may, in turn, have associated custom attributes. Custom attributes limit playback to a subset of tracks within the stream. Custom attributes are key/value pairs. Each possible pairing (from all the tracks in a stream) is listed in mArrCustomAttribInformation along with an associated integer ID. Specifying that particular integer ID causes only tracks with that particular key/value pairing to be used. Only one ID may be specified at any given time.

**Turning Video On/Off** This method may also be used to turn the video off, for example if it is desirable that content continue to play when an application using NexPlayer moves into the background.

Setting any of the streams to -2 will disable it or turn it off. There are some restrictions though when using this setting:

- The content must include both audio and video. This means it is not possible to set all of the parameters (iAudioStreamId, iTextStreamId, iVideoStreamId, iVideoCustomAttrId) equal to -2 at once.
- If the player goes into the background, the UImustcall video off (set iVideoStreamId= -2) immediately to provide the audio only stream while the player is in the background.

?> To make it possible for an application to switch content tracks while in the background, it is necessary to make the Application Activity a service and it is recommended that the service be registered with the Android operating system to help ensure it won’t be closed when device resources are managed.
 
Please also see the sample code for more details on how to turn the video on and off.

**Parameters**

| Name | Description | 
|---|---| 
|iAudioStreamId| The ID of the stream to use for audio. If this is MEDIA\_STREAM\_DEFAULT\_ID, the initial audio stream played will continue to be used.|
|iTextStreamId| The ID of the stream to use for text (subtitles, captions, and so on). If this is MEDIA\_STREAM\_DEFAULT\_ID, the initial text stream played will continue to be used.|
|iVideoStreamId| The ID of the stream to use for video. If this is MEDIA\_STREAM\_DEFAULT\_ID , the initial video stream played will continue to be used.|
|iVideoCustomAttrId|The ID of the custom attribute to use. If this is MEDIA\_STREAM\_DEFAULT\_ID , the default custom attribute will be used. If no custom attributes are associated with a stream, this will be undefined.|

**Returns**

Zero if successful, non-zero if there was an error.
 
### NexPlayer.setMediaStreamTrack

```java
int setMediaStreamTrack ( int iAudioStreamId, int iTextStreamId, int iVideoStreamId, int iVideoCustomAttrId, int iMediaType, int iAudioTrackId)
```

For media with multiple streams, this method selects the streams that will be presented to the user.

This method should be called to set a specific media stream (video, audio, or text) while NexPlayer is playing content with multiple streams. To have NexPlayer prefer text streams in a particular language before playing content, the property `PREFER_LANGUAGE` should be set instead.

The full list of available streams (if any) can be found in the mArrStreamInformation array in NexContentInformation. Each stream is either an audio stream or a video stream, and one of each may be selected for presentation to the user. Please see Multi-Audio and Multi-Video Stream Playback for more explanation.

In the case of DASH streaming service, the user can set the audioTrackID in the corresponding audioStreamID. This API is the same as setMediaStream(), but it supports the setting of audioTrackID at the same time when using DASH streamming service.

Some streams, for example in Smooth Streaming, may, in turn, have associated custom attributes. Custom attributes limit playback to a subset of tracks within the stream. Custom attributes are key/value pairs. Each possible pairing (from all the tracks in a stream) is listed in mArrCustomAttribInformation along with an associated integer ID. Specifying that particular integer ID causes only tracks with that particular key/value pairing to be used. Only one ID may be specified at any given time.

**Turning Video On/Off** This method may also be used to turn the video off, for example if it is desirable that content continue to play when an application using NexPlayer moves into the background.

Setting any of the streams to -2 will disable it or turn it off. There are some restrictions though when using this setting:

- The content must include both audio and video. This means it is not possible to set all of the parameters (iAudioStreamId,iTextStreamId,iVideoStreamId,iVideoCustomAttrId) equal to -2 at once. 
- If the player goes into the background, the UImustcall video off (setiVideoStreamId= -2) immediately to provide the audio only stream while the player is in the background.

?> To make it possible for an application to switch content tracks while in the background, it is necessary to make the Application Activity a service and it is recommended that the service be registered with the Android operating system to help ensure it won’t be closed when device resources are managed.
 
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
 
### NexPlayer.setMediaTrack

```java
int setMediaTrack (int iMediaType, int iTrackId)
```

For a stream with multiple tracks, this method selects the track that will be presented to the user.

This method should be called to set a specific media track (audio only) while NexPlayer is playing content with multiple tracks.

**Parameters**

| Name | Description | 
|---|---|
|iMediaType| The type of media stream to change the track (it supports MEDIA\_STREAM\_TYPE\_AUDIO).|
|iTrackId| The ID of the track.. `mTrackID`.|

**Returns**

Zero if successful, non-zero if there was an error.

### NexContentInformation Class

This class stores and provides information about an individual codec used by the NexPlayer engine. The information of the content is provided by the following method.

```java
NexContentInfo contentInfo = NexPlayer.getContentInfo()
```

This method provides all the information included in class NexContentInformation, check the API Documentation for deeper information about what NexContentInformation provides.

#### String getMediaCodecMimeType (int mediaType, int codecType) [static]

This method converts codec information to mime type.
 
Returns mime type of the given codec type
 
- `H264_BASELINE_PROFILE` `66`
- `H264_HIGH_PROFILE` `100`
- `H264_MAIN_PROFILE` `77`

#### NexStreamInformation[] mArrStreamInformation

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

#### int mAudioCodecClass

Classification of audio codec.

Possible **Values:**

- 0 : SW codec
- 1 : HW code

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

Currently, the safest way is to check only the first two letters of the class name to find the language and assume the most common encoding for that language.

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

#### NexID3TagInformationm ID3Tag

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

Possible **Values:**

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

Possible **Values:**

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

### NexStreamInformation Class


This class provides information on a content stream.  
Content streams are listed in the *NexContentInformation.mArrStreamInformation*

```java
for (NexStreamInformation streamInfo : contentInformation.mArrStreamInformation) {
	if (streamInfo.mType == NexPlayer.MEDIA_STREAM_TYPE_TEXT) {
		...
	}
	else if (streamInfo.mType == NexPlayer.MEDIA_STREAM_TYPE_AUDIO) {
		...
	}
	else if ...
}
```

Check API documentation for more information about what NexStreamInformation provides.

 
#### NexStreamInformation( int iID, int iType, int currCustomAttrId, int currTrackId, int isIFrameTrack, int isDisabled, NexID3TagText name, NexID3TagText language, String strInStreamID, int representCodecType)

This is the sole constructor for NexStreamInformation.

The parameters match the members of the class one-to-one. Generally, it is not necessary to call the constructor; rather, objects of this class are created by NexPlayer internally and made available through mArrStream-
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

#### NexTrackInformation[] mArrTrackInformation

For formats such as HLS that support multiple tracks for a given stream, this is an array containing information on each track associated with the stream.

This may be an empty array for formats that don’t have track information.

#### int mCurrCustomAttrID

The ID of the custom attribute within this stream that is currently active, or -1 if no custom attribute in this stream is currently active.

This ID matches a value in NexCustomAttribInformation[].mID. If the NexCustomAttrib-
Information array is empty, this value is undefined.

#### int mCurrTrackID

This is the ID of the track within the stream that is currently playing, or -1 if no track in this stream is currently playing.

This ID matches a value in mArrTrackInformation[].mTrackID. If the mArrTrackInformation array is empty, this value is undefined.

#### int mID

This is a unique integer used to identify the current stream in API calls.

For example, this is used when calling setMediaStream.

#### String mInStreamID

This is the INSTREAM-ID TAG of the media stream.

This is an arbitrary value set by the author, and is intended for user displaying (to allow users to select among different alternative streams).

For HLS content, this value is filled when the TYPE attribute is CLOSED-CAPTIONS. In this case, this value must be one of the following **Values:** "CC1", "CC2", "CC3", "CC4" or "SERVICEn", where n must be an integer between 1 and 63.
 
#### int mIsIframeTrack

For HLS content, this indicates whether the track is a normal audio video track or a track of only I-frames.

For an I-frame-only track, this value will be 1, and for other kinds of tracks, it will be 0. Since other kinds of content do not include any I-frame-only tracks, this value will always be 0 for content other than HLS.
 
#### NexID3TagTextmLanguage

This is the language of the media stream, for streaming formats that include language data.

This is an arbitrary value set by the author, and is intended for user display (to allow users to select among different alternative streams). Applications should NOT rely on this being any particular format; it is most likely to be the display name of the language, but may be any string.

#### NexID3TagTextmName

The name of the media stream, for streaming formats that have named streams.

This is an arbitrary value set by the author, and is generally intended for user display (to allow the user to select among different alternative streams).

#### int mRepresentCodecType

The type of codec available in the stream.

It will be set to 0 until the stream is downloaded. If this is for CEA 608/708 captions embedded in the content, it will be represented as NexContentInformation.NEX\_TEXT\_CEA.

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

### NexTrackInformation Class

Stores and provides information about an individual content track.  

```java
for (int i = 0; i < contentInfo.mStreamNum; i++) {
	NexStreamInformation streamInfo = contentInfo.mArrStreamInformation[i];
		for(int trackIndex = 0; trackIndex < streamInfo.mTrackCount; trackIndex++) {
			NexTrackInformation trackInfo = streamInfo.mArrTrackInformation[trackIndex];
		}
}
```

#### int mTrackID

The ID of the track.

This is an arbitrary value, not an index, but can be matched to the currently playing track as indicated by mCurrTrackID. Second parameter of the setMediaTrack.

#### int mCustomAttribID

The Custom Attribute ID of the track.

In some cases, a stream may have multiple equivalent tracks. Setting a custom attribute ID in setMediaStream causes only tracks with a matching custom attribute ID to be selected. A custom attribute ID represents a particular key/value attribute pair. The full list of available pairs and their associated ID values can be found in mArrCustomAttribInformation.

Please keep in mind that this is an arbitrary value, not an index into the custom attribute array.

#### int mBandWidth

Bandwidth of the track in bits per second (bps).

#### int mType

This indicates the type of track:

- `1` : Audio Only
- `2` : Video Only
- `3` : AV For local playback, the type will be Audio(1) or Video(2). For streaming playback, the type can be Audio(1) ,Video(2), or AV(3).
 
#### int mCodecType

This indicates the codec used for the given track.

?> Do not trust this value in HLS and MS Smooth Streaming mode, as invalid values are sometimes provided.
 
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

#### int mValid

Indicates if this track is valid (that is, if the codecs, bitrates, and so on are supported by NexPlayer).

- `0` : Unsupported or invalid track
- `1` : Valid and supported track

#### boolean mIFrameTrack

Indicates if the track is a track of IFrames for the video content or not.

Possible **Values:**

- `0` : FALSE. Not a track of IFrames.
- `1` : TRUE. A track of IFrames.

#### int mWidth/mHeight

This indicates if track includes video track, native passes its Width and Height.

#### int mAVCProfile/mAVCLevel

This indicates if track includes video track and AVC, native passes its Profile and Level.

#### int mReason

For invalid tracks, this variable indicates the reason they are not currently valid.

This may be any of the following **Values:**

- `REASON_TRACK_NOT_SUPPORT_VIDEO_CODEC` if the player doesn’t support the video codec used for this content.
- `REASON_TRACK_NOT_SUPPORT_AUDIO_CODEC `if the player doesn’t support the audio video codec used for this content.
- `REASON_TRACK_NOT_SUPPORT_VIDEO_RESOLUTION` if the track is locked out because the video resolution is too high to play, as determined by the settings of the MAX\_HEIGHT and MAX\_WIDTH properties.
- `REASON_TRACK_NOT_SUPPORT_VIDEO_RENDER` if the track was locked out because the video renderer wasn’t capable of playing it smoothly (the resolution and/or bit rate too high).
