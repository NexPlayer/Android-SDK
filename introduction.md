# NexPlayer™ SDK for Android Documentation
*Last updated December 31, 2020*

### Legal Notices

**Disclaimer for Intellectual Property**

This product is designed for general purpose, and accordingly the customer is responsible for all or any of
intellectual property licenses required for actual application. NexStreaming Corp. does not provide any indemnification for any intellectual properties owned by third party.

**Copyright**

Copyright for all documents, drawings and programs related with this specification are owned by NexStreaming
Corp. All or any part of the specification shall not be reproduced nor distributed without prior written approval by NexStreaming Corp. Content and configuration of all or any part of the specification shall not be modified nor distributed without prior written approval by NexStreaming Corp.

### Abstract

NexPlayer™ provides audio and video decoding and playback services that application developers can use to build custom multimedia players rapidly and efficiently. NexPlayer™ has been built to be reliable and robust without any sacrifice in performance, and has proven compatibility with international standards.

Recent updates include `NexVideoView` class to use NexPlayer™ SDK easily on the application, `NexCaptionRenderView` class to manage caption rendering in `NexVideoView`, `NexCaptionAttribute` class to manage the caption properties, additional options for the client-side time shift feature, a new class (`NexNetAddrTable`) to allow an application to retrieve customized host information from a table set with the new API setNetAddrTable as well as new method (changeSubtitlePath) to change subtitle files during the playback, support for Storing Streaming Content for Offline Playback storage of HLS streaming content for later offline playback, a new class (`NexABRController`) to use ABR-related methods, support for current live position methods gotoCurrentLivePosition and gotoCurrentLivePosition(boolean exact), support for Dynamic Thumbnails in Smooth Streaming content with the methods `onDynamicThumbnailData`, `onDynamicThumbnailRecvEnd`, `enableDynamicThumbnail`, `disableDynamicThumbnail` and `setOptionDynamicThumbnail`, new support for setting audio pitch in content, in addition to a new method to release resources used by instances of `GLRenderer`, methods to set maximum and minimum bandwidth, or both, for streaming content, new APIs (`NexVideoRenderer.onPause`, `NexVideoRenderer.onResume` and `GLRenderer.setListener`) to improve performance on older devices, new properties to begin playback after a part of the TS file is downloaded, to disable the audio only track in HLS content, and to continue downloading streaming data in the pause state as well as the added library `libnexralbody_video_opengl.so`, new APIs for adding or removing a release listener to receive release events from NexPlayer™ , support for displaying raised captions (CEA 608, CEA 708, timed text, and WebVTT) and depressed captions (CEA 608, CEA 708, timed text, and WebVTT) in a set font color and opacity, new methods to handle license files included with the NexPlayer™ SDK, support for turning video on and off for example when an application goes into the background, and the method setDefaultFontSize to set a default font size to use for timed text captions and improvements to support for user selected caption styling with CEA 608 closed captions, WebVTT text cues, and colored shadows for timed text and WebVTT, new method, `setShadowWithColor`, to set colored shadows on CEA 608 closed captions, support for a preview of caption styles set by the user, new methods to set a margin around caption text in Timed Text and to set default text cue font size for WebVTT, a property `START_NEARESTBW` to set a target bandwidth before playing content, as well as a new property `WEBVTT_WAITOPEN` to avoid waiting for the first WebVTT segment to download when starting to play content, a new API `initCaptionStyle` to initialize the caption style attributes set by a user, a new APIs, `onHTTPRequest` and `onHTTPResponse`, to allow more flexibility when handling HTTP requests and responses (for example when handling user cookies), a new property, `TIMED_ID3_META_KEY`, and new methods, `getArrExtraData` and `setArrExtraData`, to allow customized ID3 tags and additional metadata in content to be handled, a new member, mCaptionType, to indicate the type of captions available in content, the property `ENABLE_WEBVTT`, to set whether WebVTT text tracks or CEA 708 closed captions should be displayed automatically when both are included in content, support for offline playback in HLS and Smooth Streaming content, a new property, `PREFER_LANGUAGE`, to set the preferred language for audio and text in multi-stream content, new APIs to change how CEA 608, CEA 708, and WebVTT captions are displayed, a method to select specific HLS tracks to play by track bitrates, a method to set CEA 608 closed caption font size when custom fonts are used, a new method for setting debugging log levels, basic support for Web Video Text Tracks (WebVTT) namely text as well as support for HTML tags, the method getProgramTime to retrieve current program time information from HLS content including `#EXT-X-PROGRAM-DATE-TIME` tags, support for Intel x86 chipsets, new properties (`USE_SYNCTASK` and `SW_DECODED_BUFFER_COUNT`) to improve decoding performance, a new API to set user cookies, support for H.264 main and high profiles, the method notifyHeadsetState to detect if a headset is plugged in, the method `getCurrentPosition` to check the current play position of NexPlayer™ in content, a new automatic render mode (`NEX_DEVICE_USE_AUTO`) and support for CEA 708 closed captions a new video renderer class NexVideoRenderer to automatically handle video rendering related tasks in an application, added support to handle  sample aspect ratio information in H.264 content, support for handling the comment and text frames in ID3 tags, several new properties (`IGNORE_CEA608_TEXTMODE_COMMAND`, `OPEN_MEDIA_FILE_FROM_SPECIFIED_TS`, `REQUEST_RADIO_METADATA_MODE`, etc.), and an updated renderer for timed text in NexCaptionRendererForTimedText.

There are still some methods of `NexEIA708Struct`, `NexEIA708CaptionView`, the `IListenerinterface`
and `NexThumbnail` that are not fully documented. However, the key methods needed for playback and for
displaying CEA 708 closed captions are documented, and combined with the example code, this should provide
enough information to implement this features and interface. More detailed documentation will be added in the future.

Please also be aware that for testing and development purposes, the Android emulator should not be used with
the NexPlayer™ as there are known differences and issues between the emulator and actual Android devices,
including the fact that the OpenGL renderer does not run properly within the emulator environment.

Frequent testing on actual devices is strongly recommended during development and all apps should be tested on actual devices prior to release.

### NexPlayer™ Capabilities and Limitations

#### Operating Systems

- Android 1.6 and above

#### Basic Functionalities

- Start (from beginning or anywhere) Pause/Resume

- Seek

- Select Media Stream (Multi-Audio/Video/Subtitle) Turn on/off Media Stream

#### Advanced Functionalities

- H.264 aspect-ratio

- H.264 Picture Timing SEI Parsing

- Eye-pleaser (seamless frame skipping method) 

- ID3 Tags (including Private Frame Data)

- Set Video Output Position

- Adjust Audio Output Volume

	- Volume range  31 to -11 for Dolby

- Set subtitle display property

- Generate playback statistics information 

- Multiple Instance

- Chromecast Pre-integrated

- Android TV Input

- Calculate Average Audio Roundness

#### Streaming Protocols

- HTTP Live Streaming
    - Supported Playlist Tags
    	- Basic Tags
    		- EXTM3U
    		- EXT-X-VERSION
		- Media Segment Tags
			- EXTINF
			- EXT-X-BYTERANGE
			- EXT-X-MAP
			- EXT-X-PROGRAM-DATE-TIME
			- EXT-X-DATERANGE
		- Media Playlist Tags
			- EXT-X-TARGETDURATION
			- EXT-X-MEDIA-SEQUENCE
			- EXT-X-DISCONTINUITY-SEQUENCE
			- EXT-X-ENDLIST
			- EXT-X-PLAYLIST-TYPE
			- EXT-X-I-FRAMES-ONLY
		- Master Playlist Tags
			- EXT-X-MEDIA
			- EXT-X-STREAM-INF
			- EXT-X-I-FRAME-STREAM-INF
			- EXT-X-SESSION-DATA
			- EXT-X-SESSION-KEY
		- Media or Master Playlist Tags
			- EXT-X-INDEPENDENT-SEGMENTS
			- EXT-X-START	
- MPEG-DASH

- HLSv06

- VoD

- Live

- fMP4

- Rate Adaptation

- CEA-608 Subtitle

- CES-708 Subtitle

- WebVTT Subtitle

- AES-128 Decryption Multi-Video/Audio Track (HLSv04) 

- I-Frame only Track (HLSv04)

- Fast Play using I-Frame only Track 

- Offline Playback

- Offline Store without Playback 

- Timed Meta

- Server-Side TimeShift 

- Client-Side TimeShift

- Specify Start Track

- Restrict maximum bandwidth 

- Restrict minimum bandwidth 

- External ABR Control 

- Dynamic Thumbnail

- Dolby Passthrough

- Dolby SW Codecs for 32 & 64 bits

- HTTP redirection

- HTTP digest authentication 

- HTTP/2 

- Cookie Manipulation 

- Backup Track

- GZip

- Generate Streaming Statistics Information 

- Proxy

- PSSH version 1

- Log2 file

- Progressive Download

- Streaming Mode

- Download (Store) and Play mode 

	- Fast downloads. Download speed x2

	- Download with Android Service

- Chunked Transfer Encoding (CTE)

- HTTP Redirection

- Cookie Manipulation 

- GZip

- Local Playback

- MP4/PIFF/3GPP/3GP2 AVI

- AMR

- ACC

- MPEG-TS 

- MKV

- CFF

- Low Latency

- DASH SPD (Suggested Presentation Delay) 

	- Allow setting offset for SPD Device Time

	- Setting SPD value from client-side

#### Video Codecs

- H.264

- HEVC (H.265) 

- H.263

- MPEG-4 

- MPEG-2

- VP9

- Dolby Vision SW Codecs

#### Audio Codecs

- AAC-LC

- HE AAC (ACC LC+SBR)

- HE AAC v2 (AAC-LC+SBR+PS)

- AC3/ EC3/ AC4/ Atmos/ Passthrough

- MP3/ MP4

#### Subtitles

- External Subtitles (smi, srt, sub, dfxp) 

- 3gpp Timed Text (3GPP file format)

- TTML

- Image based closed caption at TTML 

- DXFP

- CEA-608

- CEA-708

- WebVTT

- Support Remote subtitle file

- Replace external subtitle while playback

#### Optional Modules 

- Widevine DRM (L1, L3)

	- The possibility to go to SW Widevine if (enableWVSW && !enableMediaDRM)

	- Widevine reprovisioning API

	- Key Renewal

- PlayReady

- Verimatrix (32 & 64 bits)

#### Verified compatibility with external modules
**Subject to additional and/or 3rd party licenses**

- Analytics

	- Conviva 

	- Agama

- Ad Insertion 

	- Yospace 

	- Freewheel 

	- VAST

- Sound

	- Dolby 

#### Other Products from NexPlayer

- NexPlayer STB SDK (to be customized for each for Android Set-Top Box/Android TV) 

- NexPlayer360 SDK

- NexPlayer Unity Plugin
