## NexPlayer SDK for Android Release Notes

### version 6.72.0.850 (26/08/2021)
- [Add] New listener for trackdown property, when a track down happens
- [Add] AV1 Codec Support
- [Improve] Offline Playback improvements for FAT32 formatted SD Cards
- [Improve] Improve setTargetBandwidth API with QUICK_MIX option for faster track changes

### version 6.72.0.849 (12/08/2021)
- [Fix] Fixed video stuttering problem for certain devices

### version 6.72.0.848 (22/07/2021)
- [Update] Improvements for NexRecovery with SWDRM fallback
- [Add] Expose license server response to application layer when there is a DRM error
- [Add] Deliver EMSG events with TimedMetadata callback

### version 6.72.0.846 (23/06/2021)
- [Fix] Fixed an issue with SET_PRESENTATION_DELAY property
- [Update] Updated settings organization from the sample application

### version 6.72.0.844 (28/05/2021)
- [Add] EMSG events for HLS/fMP4

### version 6.72.0.843 (18/05/2021)
- [Update] ViewRight WebClient updated to version 4.3.8.0
- [Improve] Improvements with Dolby passthrough

### version 6.72.0.841 (16/04/2021)
- [Add] New API to enable SW DRM recovery
- [Add] Implemented new property to disable video vendor codec
- [Add] Possibility to enable UDS logging before
- [Add] Added new properties in order to get current A/V codec
- [Update] ViewRight WebClient updated to version 4.3.7.2

### version 6.72.0.840 (26/03/2021)
- [Update] Migrate sample application to AndroidX
- [Update] Update gradle version of the sample application
- [Update] Automatically fallback to HW DRM when SW DRM fails
- [Update] Provide an API to use socket logging
- [Improve] Improve multiple player instance stability
- [Fix] Fixed an issue for specific type of DRM contents

### version 6.72.0.838 (11/02/2021)
- [Optimization] Removed unnecessary permissions from sample
- [Add] HTTP/2 Support

### version 6.72.0.836 (12/01/2021)
- [Optimization] Improve multiple player instance performance
- [Add] Dolby SW decoding support for 64bit devices
- [Add] Allow setting offset for SPD Device Time
- [Add] Implemented a new callback for data inactivity

### version 6.72.0.835 (17/12/2020)
- [Add] Dolby Vision support for STBs
- [Add] Fast downloads. Download speed has increased up to 2x.
- [Add] Implemented a new callback to receive logs from application side
- [Add] Added support for PSSH version 1
- [Add] Setting SPD value from client-side
- [Add] Widevine reprovisioning API 

### version 6.72.0.833 (30/10/2020)
- [Add] Dolby Passthrough support
- [Add] Dolby Atmos support

### version 6.71.0.831 (21/10/2020)
- [Fix] Avoid java.util.Collections exception in NexCaptionPainter.
- [Fix] Force to Media DRM security level L3 in case of Pixel C device
- [Fix] Setting Z order for NexVideoView
- [Fix] Changed android version when SDK is a current development Build to SDK 21
- [Fix] Avoid app crashing when types array is empty
- [Fix] Allow <a href="https://nexplayer.github.io/Android-SDK/api/log2file.html">Log2File</a> if Android Version is major than Lollipop
- [Fix] Implemented a new property to save logs to the file.
- [Fix] Fixed speed up issue on SPD when paused and resumed
- [Fix] Matched audio renderer usage between iOS and Android
- [Fix] Fixed SPD pixelisation issue when pause and resume
- [Fix] Fixed SPD buffering issue when pause and resume
- [Fix] Fixed the issue that causes Unknown Error Code 0x000006
- [Fix] Fixed returning value when contents is eac3 Dolby
- [Fix] Modified payload parsing when payload is equal to number of rbsp for closed caption
- [Fix] Fixed an issue happens during the audio track change
- [Fix] Added a logic considering wrap around of timestamp in case of enabling a partial prefetch

### version 6.71.0.830 (29/09/2020)
- [Fix] Fixed the display issue when the current timestamp is not updated from initial position.
  
### version 6.71.0.828 (14/09/2020)
- [Fix] Fixed AV sync issue in Android & Amazon TV
- [Update] Updated to check minimum resolution routine 
- [Update] Updated to convert html entities in @messageData on DASH 
- [Update] Optimised AV synchronisation after seek
- [Add] Added parsing @frameRate attribute on DASH

### version 6.71.0.826 (10/08/2020)
- [Update] Updated to check query syntax on absolute URL path.
- [Fix] Fixed an error when checking platform information of Android devices.
- [Fix] Enable to download the Widevine key only when playing Widevine contents in offline playback mode.
- [Update] Updated Verimatrix library for supporting Android 64bit devices.
- [Fix] Fixed Dolby codec initialization error.
- [Update] Updated exception handling when the latest segment is missing on mpd.
- [Update] Updated downloading step when stop downloading and download again.
- [Fix] Fixed transparent PiP when the player is still buffering.
- [Fix] Fixed error stopOfflineStore() api is not working.
- [Add] Added support to get the video resolution of each video track.
- [Fix] Fixed to change Pixel Format on specific devices.
- [Add] Added new setProperty to synchronize based on device UTC time.

### version 6.70.0.823 (28/05/2020)
- [Fix] Fixed internal issues
- [Fix] Fixed socket error issue when redirected contents unsupported offline playback
- [Fix] Fixed a stored offline playback issue with long url
- [Fix] Fixed a rebuffing rate issue after long playback
* [Added] Added error codes for crypto errors
* [Updated] Agama EMPClient updated to the latest
* [Fixed] Fixed the order of library when using under Android 4.3 devices
* [Added] Added Http header field on sample UI
- [Update] Update to skip the IODSParsing function
- [Fix] Fixed Video Freeze AV sync Issue when setting by SPD

### version 6.69.2.818 (03/04/2020)
- [Fix] Fixed slow motion when setMediaStream is called
- [Fix] Fixed crash issue on multi thread access of audio renderer

### version 6.69.2.817 (27/03/2020)
- [Update] Updated content format support on K85 ZTE
- [Update] Updated error code description when decrypt failed
- [Update] Updated redirect url when ‘@‘ character included
- [Update] Updated Segment Guessing condition

### version 6.69.2.816 (19/03/2020)
- [Update] Updated Agama Integration
- [Update] Updated the setting SystemUTCOffset
- [Update] Updated leap year check routine  
- [Fix] Fixed Jerky playback by optimizing audio task
- [Fix] Fixed audio glitch by optimizing audio task
- [Optimization] Improvement of A/V sync performance on SPD

### version 6.69.2.815 (14/02/2020)
* [Upgrade] Support of AdaptationSet removal in multi-period streaming sessions. Previously giving error 0x00015 (unknown)

### version 6.69.2.814 (10/02/2020)
- [Optimization] Reduced starting time when playing Widevine contents
- [Update] Optimized ABR algorithm for low latency streaming.
- [Update] Updated DASH SegmentTimeline parser to support more manifest formats
- [Update] drmSessionManager is released in close (no impact in Widevine app usage)
- [Fix] Fixed crash issue while changing WebVTT to TTML.

### version 6.69.2.812 (05/02/2020)
- [Fix] Fixed crash issue while parsing for incorrect ID3 tag ### version by implementing of defensive code.

### version 6.69.1.811 (11/12/2019)
- [Optimization] Improvement of EMSG data callback
- [Optimization] Improvement of TimedText CaptionRenderer
- [Update] Upgrade OpenSSL ver from 1.0.2r to 1.1.1d

### version 6.69.0.810 (04/12/2019)
* [Added] Added callback for getting Widevine Level (L1,L3)
* [Improvement] Improved Widevine policy for offline playback to HW->SW policy
* [Added] Added the possibility to go to SW Widevine if (enableWVSW && !enableMediaDRM)
* [Added] New API updateHTTPheaderFields
- [Add] Added explanation of init() API.
- [Fix] Fixed Dash WebVTT alignment in fragmented mp4
- [Fix] NPDS-6291 Fixed WebVTT
* [Improvement] Improved audio renderer library for better seek and AV synch at some devices
- [Fix] Fixed buffering issue for A/V interleaved content
* [Improvement] NPDS-6286 Hiccup effect when skipping through content improved

### version 6.68.0.807 (18/11/2019)
- [Optimization] Improvement of A/V sync performance on specific live contents
- [Optimization] Optimized video performance for low end devices SM-T280, SM-T285 and Oppo A37f
- [Fix] Fixed and issue when pausing a live stream that caused frequent error 23.
- [Fix] Fixed and issue when playing a video only stream first that caused frequent error 14.
- [Fix] Fixed an issue with live stream: If we pause and resume the sound and video were off-synch.
- [Fix] Fixed hiccup on pause and seek during playback.
- [Fix] Fixed issue: DRM stream could not play if starting position was not 0.
- [Add] Added NXPROTOCOL_PROPERTY_LIVE_OFFSET_TIME property.
- [Add] Added NEXPLAYER_PROPERTY_HTTP_FAILOVER_DURATION property.

### version 6.67.0.800 (31/10/2019)
- [Optimization] Improvement of HEVC performance on Amazon device Cube

### version 6.66.1.798
- [Update] Optimization for Samsung Gakaxy tab model T280
- [Update] Optimizations for phone model Oppo A37f

### version 6.66.0.797
- [Update] Changed default Widevine policy: Try HW Widevine first and apply SW Widevine only if HW fails
- [Update] Fixed an issue when pausing and resuming
- [Update] Added SEND_ALL_DASH_MPD_EVENTS property
- [Update] Support optional header fields of HW DRM
- [Add] Added EMSG data callback
- [Add] Added Connecting Proxy Server automatically
- [Add] Added DRM content download with optional header
- [Update] Fixed error of incorrect processing when trying to activate the audio in one particular case
- [Update] Fixed closed caption problem in one particular case
- [Add] Added NXPROTOCOL_PROPERTY_HTTP_IMMEDIATE_FAIL_OVER property
- [Update] Added API to force WebVTT alignment from app layer
- [Update] Updated Agama optional library (support Android 64 bit and fixed Gradle build for Agama)
- [Update] Fixed a crash issue on dynamic thumbnails (HLS)
- [Update] Fixed a problem where the CTS was incorrect when synchronizing sessions with ProgramDateTime(HLS)
- [Update] Updated to pass _dwCencSessionId value in FrameInfo
- [Add] Added LIVE_OFFSET_SEGMENT_COUNT property(Java Side)
- [Update] Improved caption renderer

### version 6.65.5.792
- [Update] Fixed an issue that Video off-sync after pause

### version 6.65.5.791
- [Add] Added latest unity sdk

### version 6.65.5.788
- [Update] Downgrade OpenSSL ver from 1.0.2s to 1.0.2r
- [Update] Fixed an issue where player is failed to connect content on android 64bit
- [Add] Support SW Widevine on 64bit
- [Update] Fixed an crash issue where player is crashed on some devices
- [Update] Fixed an issue where Nexplayer is occur to be crash if source type is 'local' and content path is null
- [Update] Fixed wrong type casting in the nex audio renderer

### version 6.65.4.786
- [Update] Improved performance of the caption renderer
- [Update] Changed default user-agent based on websetting of device
- [Update] Fixed an issue where player is crashed when NexPlayer read a big size of WebVTT Caption 
- [Update] Updated OpenSSL from ver1.0.2k to ver1.0.2s
- [Update] Fixed an issue where player falls in ANR when player is stopped with some close caption contents
- [Update] Implemented to switch clear to encrypted frames
- [Update] Fixed to reset decoder information when codec is released
- [Update] Fixed an issue where player is not able to switch clear and encryption segment on SW widevine
- [Update] Fixed that player don't wait text segment in DASH if player is not set to "CaptionWaitOpen" property
- [Update] Fixed an issue where player is not able to change stream in multi-period content
- [Add] Added the Constant Buffer Management for Low Latency
- [Update] Chnaged to play from the live position instead of playing from disconnected position, when the network connection is reconnected(HLS, DASH)
- [Add] Added to conver HTML Entities in URL to ASCII charactes
- [Update] fixed to fmp4 webvtt timescale issue


### version 6.65.3.782
- [Update] Improved seeking routine.

### version 6.65.3.780
- [Update] Improved stability of playback 
- [Update] Improved stability for widevine key rotated content. 
- [Update] Support fmp4 mutti track in HLS 
- [Update] Improved a MPD reload for SegmentTimeline in DASH. 

### version 6.65.1.765
- [Update] Improved stability of playback

### version 6.65.0.763
- [Update] Improved to correctly support HLS master playlist with multiple codecs.
- [Add] Supports PlayReady DRM with common encryption(cenc) in Smooth Streaming.
- [Update] Improved video synchronization routine.

### version 6.64.7.764                           
- [Update] Improved stability of PIFF DRM     

### version 6.64.6.761
- [Add] Add a property of NexCaptionSetting to replace the desired color by specifying the color to be replaced.

### version 6.64.5.760
- [Add] Added new error code (ERROR_AES_KEY_RECV_FAIL).

### version 6.64.4.759
- [Update] Improved client time shift feature
- [Update] Optimized default initial buffering time.

### version 6.64.4.757
- [Update] Improved failover policy
- [Update] Improved stability of subtitle routine.

### version 6.64.4.756
- [Update] Improved Video ChunkPaser routine.
- [Update] Supported SCTE35 events in DASH.
- [Update] Improved subtitles performance.
- [Update] Supported License Renewal in Widevine.
- [Update] Improved stability of video init routine.
- [Add] Added new error codes (DRM_NOT_SUPPORT_HDCP).

### version 6.64.3.750
- [Update] Improved stability of widevine DRM.

### version 6.64.2.749
- [Update] improved compatibility for old jdk.

### version 6.64.1.748
- [Update] Improved stability of widevine DRM.

### version 6.64.0.746
- [Update] Improved client time shift feature
- [Add] Added new error codes (DRM_INSUFFICIENT_HDCP_LEVEL).

### version 6.63.2.7405
- [Update] Improved Video ChunkPaser routine.

### version 6.63.2.740
- [Update] Improved audio processing routine.
- [Update] Improved Mpeg-TS Parser.

### version 6.63.2.739
- [Update] Improved client time shift feature.
- [Update] Improved stability of the http downloader.

### version 6.63.1.735
- [Add] Supported IMA(VAST) SDK.

### version 6.63.0.732
- [Update] Supported DASH SPD(Suggested Presentation Delay) feature.
- [Update] Improved fastPlay feature.
- [Add] Added new API getTimeCode in NexID3TagInformation to get the timestamp of timed metadata.
- [Add] Added onHlsFirstProgramDateTime() listener to reports the HLS first program date time information.
- [Add] Supported EMSG(SCTE-35) events.
- [Update] Fixed AV synchronization issue for certain TS file.
- [Add] Supported AC4 Elementry stream.
- [Update] Improved the Mpeg-TS & MP4MF frame generate routine

### version 6.62.12.728
- [Update] Improved the Mpeg-TS parser.

### version 6.62.11.722
- [Update] Improved stability of the subtitle parser.

### version 6.62.10.721
- [Update] Improved NexStreamInformation for multiple subtitle stream.

### version 6.62.9.719
- [Optimization] Improved codec libraries search routine.

### version 6.62.8.718
- [Optimization] Improved video performances.

### version 6.62.7.715
- [Update] Improved stack smashing protection

### version 6.62.6.714
- [Update] added Android armeabi-v7a ABI.

### version 6.62.5.712
- [Update] set max width/height to input format(for Nexus 7 / SM-T560* Samsung Tab E)
- [Update] Added exception handling for the case where the system time of the client is incorrect.

### version 6.62.4.702
- [Update] Modified sending a message for service certificate through the registered listener.

### version 6.62.3.701
- [Update] Supported key rotation of widevine DRM
	
### version 6.62.1.692
- [Add] Add INexDRMLicenseListener for delegator of Widevine License Request.

### version 6.62.0.691
- [Add] Added the new setMediaStreamTrack API to set audioStreamID and audioTrackID.
- [Update] Improved NexOfflineStoreController processing routine.

### version 6.61.1.688
- [Update] Support Android x86_64 ABI.

### version 6.61.0.686
- [Update] Improved HTTP User Header add routine
- [Update] Supported pass public time in DASH.
- [Optimization] Improved video performances.
- [Optimization] Improved WideVine DRM performances.

### version 6.60.1.684
- [Update] Improved dynamic thumbnails performance.
- [Update] Improved subtitles performance.

### version 6.60.0.682
- [Add] Added the new setMediaTrack API to set audioTrack.
- [Update] Improved the AAC ADTS header check routine.
- [Update] Supported HW Widevine (HLS with fMP4).
- [Optimization] Improved video performance.
- [Update] Improved dynamic thumbnail performance.

### version 6.59.1.679
- [Add] Added -fstack-protector-strong compile option.
- [Update] Improved stability of the subtitle parser.
- [Update] Improved stability of playback in the offline mode.
- [Update] Improved error handling the AudioRenderer routine. 
- [Update] Improved stability of playback using Widevine DRM.

### version 6.59.0.677
- [Update] Improved audio codec init routine.
- [Update] Supported ABR using SpeedControl.
- [Update] Improved start-up time for PD(progressive download) content.
- [Update] Improved file parser.
- [Update] Updated the surfaceHolder's Callback message using openGL renderer.
- [Add] Added new API getTTMLTimeData2Array in NexClosedCaption, to get time information of TTML.
- [Update] Improved video performances.

### version 6.58.2.670
- [Update] Improved video rendering routine on ONEPLUS A3003 device.
- [Update] Improved DASH redirection routine.
- [Update] Improved seamless decoder routine on AFTA device.
- [Optimization] Improved statistics performance

### version 6.58.1.666
- [Update] Improved A/V sync routine.

### version 6.58.0.665
- [Update] Supported HW PlayReady DRM with DASH.
- [Update] Improved ABR algorithm.
- [Update] Improved subtitle file checking routine.
- [Optimization] Improved video performances.
- [Optimization] Improved video rendering performances.

### version 6.57.3.659
* [Updated] Improved audio frame lost routine.

### version 6.57.2.657
* [Updated] Supported HDR (High Dynamic Range) on Galaxy S7 and S8.
* [Updated] Supported SW Widevine for CMAF HLS contents.

### version 6.57.0.652
* [Updated] Improved the parsing routine of ID3 TTML.
* [Updated] Supported for the #EXT-X-DATERANGE tag in HLS.
* [Updated] Improved the changing routine of a/v stream.
* [Updated] Improved playback when the duration of the dash segment is very small (eg. 200ms).
* [Updated] Supported SW Widevine for DASH contents.
	* Fixed jira issue [DSTS-1970].

### version 6.56.10.659
- [Update] improved the seamless decoder routine in AFTN device.
- [Add] Property added to enable getting detail error.
	NexProperty.ENABLE_DETAIL_ERROR
- [Add] Added new API getDetailedError in NexPlayer, to get detailed error when NexProperty.ENABLE_DETAIL_ERROR is enabled.

### version 6.56.8.657
- [Optimization] Improved video performances.

### version 6.56.7.654
- [Update] improved performance and A/V sync for FireTV generation 2.

### version 6.56.5.649
- [Update] improved performance and A/V sync for FireTV devices.

### version 6.56.4.646
- [Update] Supported Hw AC3 codec for FireTV generation 2.
- [Update] Improved seek routine for FireTV.
- [Update] Improve setMediaStream routine.

### version 6.56.3.644
* [Updated] Improved memory management for timedmeta content in 64bit
- [Optimization] Improved video performances.
- [Add] Added the new scale mode "SCALE_ASPECT_FILL".

### version 6.56.2.639
- [Update] Improved stop routine on Android O.
- [Update] Improved error code handling.
- [Update] Improved video performances on HEVC.
- [Update] Improved Conviva module.
- [Update] Improved the TTML decoder.
- [Add] Added new API getUnknownSubCode in NexErrorCode, to get the sub error code when unknown error occurs.

### version 6.56.1.633
* [Fixed]Improved behaviour of the buffering when the content uses CC and subtitles.

### version 6.56.0.631
- [Add] Added enableTrack API to enable disabled tracks.
- [Optimization] Improved parsing routine of PIFF DRM contents
- [Add] Supported below features of HLS V7.
	* #EXT-X-SESSION-DATA, #EXT-X-START tags and INSTREAM-ID
- [Update] Updated selection of embedded closed captions along with other captions.
- [Optimization] Improved A/V synchronization during playback.
- [Add] Added new API, NexClosedCaption::getCaptionType, to get the caption type.

### version 6.55.3.627
- [Update] Improved audio performances.
- [Update] Improved 404 error handling routine for live streams.
- [Update] Improved performance and A/V sync for HUAWEI M2-A01W device.
- [Update] Improved TTML renderer.
- [Optimization] Improved video performances.

### version 6.55.2.620
- [Update] Improved TTML renderer
* [Fixed] Added missing parameters of statistic monitor in Smooth Streaming.
- [Update] Improved changing text stream routine. 
- [Update] Improved the routine to check that player is initialized.
- [Update] Improved CTS adjustment routine in live streams.
- [Update] Supported WebVTT format in mp4.

### version 6.55.1.619
- [Update] Support StatisticsMonitor on SmoothStreaming.
- [Optimization] Improved video performances.
- [Update] Improved WebVTT subtitles renderer.
- [Update] Support HEVC with WideVine encrypted content
- [Update] Improved AC3 performance for FireTV.

### version 6.55.0.615
- [Add] Property added to enable TTML text tracks in ID3 tags.
	NexProperty.ENABLE_ID3_TTML.
- [Update] Supported role scheme in DASH.
- [Update] Improved redirection processing for MSS.
- [Update] Support of custom caption attributes.
- [Update] Improved TTML renderer
- [Update] Improved stability of the WebVTT subtitle renderer
-[Fix] Improved behaviour of the setVideoBitrates API on 64bit SDK package.
-[Fix] Improved behaviour of the WideVine DRM.
- [Update] Applied Verimatrix-ViewRight-Web-4.1.2.0-PI7.6-2-web_android-linux

### version 6.54.4.607
- [Update] Improved TimedMeta processing routine.
- [Update] Improved Video performance and A/V Sync for LeTV devices.

### version 6.54.3.602
- [Optimization] Improved video performances.
- [Optimization] Improved A/V synchronization during playback.
- [Update] Improved Audio Performance for LeTV.

### version 6.54.2.601
- [Update] Improved time calculation routine in TTML.
-[Fix] Improved SPS Data processing routine in HEVC.

### version 6.54.1.597
- [Update] Updated to OpenSSL ### version 1.0.2k.

### version 6.54.0.596
- [Update] Improved method to show the name and language in audio/subtitle tracks.
- [Fix] Improved DRM callback registration routine in 64bits.
- [Fix] Fixed not called DOWN_START event in statistics monitor.
- [Optimization] Improved track change routine when occurring network error.
- [Optimization] Improved gotoCurrentLivePosition API routine.
- [Optimization] Improved webvtt renderer.
- [Add] Support custom attributes of captions,
	Added a new class, "NexCaptionPainter", to render captions as WEBVTT, TTML, CEA608, CEA708, SMI, SRT, SUB more easily.
	Added a new class, "NexCaptionSetting", to set caption styles such as color, size, bold, italic, underline, a position of caption and edge style effects to NexCaptionPainter.
	Added a new class, "NexCaptionWindowRect", to set the position of caption window.

### version 6.53.3.589
- [Optimization] Improved base timestamp calculation routine.

### version 6.53.2.587
- [Optimization] Improved video performances.
- [Optimization] Supported start time of live contents in DASH and SS.
- [Optimization] Improved TTML renderer.

### version 6.53.1.582
- [Optimization] Improved TTML renderer.

### version 6.53.0.581
- [Add] Property added for checking HTTP Response and Request header length.
	NexProperty.CHECK_HTTP_HEADER_LENGTH.
- [Optimization] Improved TTML renderer.
	NexPlayer.NexUniqueIDVer.### version_3.

### version 6.52.6.576
- [Optimization] Improved TTML renderer.

### version 6.52.5.569
- [Update] Improve Audio Performance for FireTV when AC3 streams are includeded.

### version 6.52.4.567
- [Update] Improve stream selection routine.
- [Update] Improve setMediaStream routine.

### version 6.52.3.565
- [Optimization] Improved #EXT-X-PROGRAM-DATE-TIME tag handling routine.
- [Update] Support of NexStatisticsMonitor for DASH.
- [Fix] Fixed an issue related to wrong parsing of TS segments.
- [Fix] Fixed an issue where the parser recognized as valid a file that doesn't support video TS segment.
- [Fix] Fixed an error that made some webvtt subtitles be displayed in the wrong position.
- [Update] Support of TLS v1.2 in OPENSSL.
- [Optimization] Improved Text Decoder.
- [Optimization] Improved general video performances.

### version 6.52.2.558
- [Optimization] Improved the TTML Caption rendering routine.

### version 6.52.1.555
- [Optimization] Changed the return values of 'NEXPLAYERHLSAES128DescrambleCallbackFunc' and 'NEXPLAYERHLSAES128DescrambleWithByteRangeCallbackFunc' to match with other callbacks.

### version 6.52.0.554
- [Optimization] Improved TTML caption rendering routine.
- [Add] Added HLSAES128DRMManager class to support different kinds of DRM schedules simultaneously.
- [Fix] Fixed an error where WebVTT subtitle rendering stopped when playing content for a long time(more than 13 hours) in HLS live stream.

### version 6.51.4.552
- [Optimization] Improved the playback routine when there is a "lost frame".
	
### version 6.51.3.548
- [Optimization] Improve setMediaStream() routine for FireTV when AC3 streams are includeded.

 ### version 6.51.2.546
- [Fix] Improved the WebVTT rendering routine.
- [Fix] Fixed the memory leak issue when playing CEA 608 multi-channel content.

### version 6.51.1.540
- [Optimization] Improved video performances.

### version 6.51.0.538
- [Add] Support NEXPLAYERHLSAES128DescrambleWithByteRangeCallbackFunc.
	typedef int (*NEXPLAYERHLSAES128DescrambleWithByteRangeCallbackFunc)
- [Fix] Fixed the issue where pauseAfterReady did not work in certain conditions..
- [Fix] Improved the NexPlayer playback routine in IPV6 network.
- [Fix] Fixed the error where ABR track switching did not work when playing certain SS content.
- [Add] Support multiple listeners
	public boolean addEventReceiver(NexEventReceiver receiver)
	public boolean removeEventReceiver(NexEventReceiver receiver)
- [Add] Support Http redirection in DASH protocol.
- [Update] Support HLS + fMP4.
- [Update] Support Android 64-bits.

### version 6.50.1.533
- [Fix] Added an exception handler for destroying surface while seeking.

### version 6.50.0.529
- [Optimization] Improved video performances.
- [Fix] Added an exception routine that does not send http response data to the UI when the received data from the server is bigger than 2KB.
- [Fix] Fixed the function which gets texts from webvtt subtitles as a string through API NexClosedCaption.getTextStringForWebVTT().
- [Fix] Added an exception handler for destroying surface while seeking.

### version 6.49.11.526
- [Fix] Fixed the issue where closed caption, WebVTT and TTML, was flickering.
- [Fix] Added a security exception handling for AgamaClient.

### version 6.49.10.524
- [Fix] Fixed the issue where closed caption was flickering.

### version 6.49.9.522
- [Optimization] Improved video performances.
- [Fix] Improved the close routine which can stop NexPlayer before the UI receives an event of asynchronous open completion.
- [Fix] Fixed a crash issue where the surface is destroyed.
- [Fix] Fix the issue where audio did not play in encrypted DASH content.
- [Optimization] Improved TTML renderer. Implemented some missed tags.
- [Fix] Fixed the issue where certain live DASH content could not play properly.
- [Fix] Fixed the issue where certain content played audio only.
- [Update] Updateed the Sample App to work in Android Studio 2.2.x.
- [Fix] Fixed an issue where a green screen was rendered during playback on a specific device.

### version 6.49.8.519
* [Improve] Improved the interlaced content detection algorithm.
- [Fix] Fixed an error where NexPlayer notified onStatusReport with a wrong value "NEXPLAYER_ERROR_INVALID_RESPONSE(0x10002)" instead of "eNEXPLAYER_HTTP_INVALID_RESPONSE(0xb)".
- [Fix] Improved the performance of playback while switching text streams.
- [Add] Added ENABLE_DECODER_SEAMLESS property which can improve the video playback performance while switching tracks.

### version 6.49.7.512
- [Optimization] Improved video performances.
- [Optimization] Improved ABR algorithms.
- [Fix] Fixed an issue where the TTML subtitles were not displayed in Smooth Streaming mode.
- [Optimization] Improved audio and video sync logic.

### version 6.49.6.508
- [Update] Updated OpenSSL to 1.0.2h.

### version 6.49.5.506
- [Optimization] Improved video performances.
- [Fix] Improved the checking routine of ADTS AAC header.

### version 6.49.4.503

### version 6.49.3.501
- [Optimization] Improved ​the ​error handling when receiving ​a ​503 error from the Server.
- [Fix] Fixed ​the i​ssue where the player could not totally parse content description​s​ when parsing ​an ​ID3 tag.

### version 6.49.2.499
​​- [Optimization] Improved ​the ​checking ​routine of ​seekable frame​s in HEVC.
- [Fix] ​​Fixed​ the​ issue where the player ​could not start playback​ when ​the content's​ playlist media type is audio.
- [Fix] Fixed the issue​ ​where ​an audio renderer timestamp is not calculated correctly in some devices.
- [Fix] Fixed​ the​ issue where the subtitle couldn't be displayed norma​llywhen changeSubtitlePath() is called.

### version 6.49.1.494
- [Optimization] Removed ​the DNS cache routine.
- [Update] Support subtitle in DASH.

### version 6.49.0.492
- [Optimization] Improved i-frame check routine.
- [Fix] Fixed the issue​ of the​ Start->Stop routine ​during ​offline playback.
- [Fix] ​​Fixed the issue where ​the engine did not parse timed metadata​ successfully.​
- [Add] ​​Added a callback ​that verifies ​whether or not a key attribute is support​ed ​by the DRM module.
	NEXPLAYERHLSIsSupportKeyCallbackFunc()
- [Optimization] Increase​d the​ ​DNS ​cache stack size.
- [Fix] Disable​d​ partial prefetch if any DRMs are registered.

### version 6.48.2.487
- [Optimization] Improved a socket API.

### version 6.48.1.486
- [Optimization] Improved a socket API.

### version 6.48.0.484
- [Optimization] Improved video performances.
- [Update] Set the Codec type based on each track's information (Now supports Smooth Streaming and DASH.)
- [Fix] Fixed incorrect time stamps in some Smooth Streaming content.

### version 6.47.0.481
- [Optimization] Improved video performances.
- [Add] Support IPv6.
- [Add] Support offline playback on DASH.
- [Add] Support VAST Ads playback.
- [Add] Support TV input service.
- [Fix] Improved webvtt caption newline process routine.

### version 6.46.0.478
- [Add] ​​Added a new DRM callback to parse​​ ​​enveloped header​s of ​a ​PD block​.​
	DRM callback: NEXPLAYERPDEnvelopHeaderParsingCallbackFunc().
- [Update] ​Set ​the ​Codec type ​based on ​each track's information (This is only available on HLS).
- [Add] Support Dynamic Thumbnail on HLS.

### version 6.45.0.476
- [Add] Added APIs to support File Descriptor ​in the​ assets folder.
	public int openFD(AssetFileDescriptor afd)
	public int openFD(FileDescriptor fd, long offset, long length)
	public int changeSubtitleFD(AssetFileDescriptor afd)
	public int changeSubtitleFD(FileDescriptor fd, long offset, long length)

### version 6.44.4.474
- [Fix] Improved​video decoder stability.
- [Fix] ​​Fixed an issue ​where playback of https content via proxy server​ failed​.
- [Optimization] ​​Improved​​​ ​the ​library search routine within the library path.

### version 6.44.3.472
- [Optimization] Improved video performances.
* [Fixed] Fixed an issue where a green screen was rendered during playback on a specific device.
	Device : HTC HTC Sensation XL with Beats Audio X315e.

### version 6.44.2.471
- [Optimization] ​​Improved​ library search routine within the library path.

​​### version 6.44.1.470
- [Update] ​Added ​support ​for ​the onDemand profile ​in​ DASH.
​​- [Fix] Fixed ​the ​issue where HLS ​​content ​that ​included webvtt caption was not downloaded when ​'​storing​'​.
- [Optimization] Improved​​ ABR algorithm.
- [Optimization] Improved playback ​on the ​set​ start time.
- [Fix] Fixed ​an ​issue where ​a ​caption was displayed before playback.

​​### version 6.44.0.468
- [Optimization] Improved video performances.
- [Optimization] Removed ​the ​text-relocation and dependency from OpenSSL.
- [Add] Added ​the keepScreenOn API ​that can​​ control sleep mode.
- [Fix] Fixed an issue where the player ​pauses when​ the player goes to​ the​ background in video disabled mode.
- [Add] Supported CONTINUE_DOWNLOAD_AT_PAUSE property for VOD ​​content.
- [Add] Supported ​the ​onHTTPABRTrackChange​ ​callback to ​​control ABR.

### version 6.43.3.466

​​### version 6.43.1.463
​​- [Optimization] Improved A/V synchronization during playback.
- [Fix] Fixed ​the ​​issue of H/W Codec initialization ​on​ specific devices.
- [Optimization] Improved 'START_WITH_AV' property.

### version 6.43.0.461
- [Fix] Fixed an issue where the total playtime was not displayed.
- [Fix] Fixed an issue where the Audio and Video CTSand PTS weren't sequentially increased in specific DASH content.

### version 6.42.6.459
- [Fix] Improved ​stability : Fixed​ an​ issue where the player was in ​an ​infinite loop while parsing timed metadata for specific content.

### version 6.42.5.458
- [Fix] Improved robustness: AAC decoder initialization failed when the first AAC frame included wrong data, now the player overcomes the error and continues playback.

### version 6.42.4.457

### version 6.42.3.456
- [Optimization] Improved video performances.
- [Add] Added a new class NexVideoView to make NexPlayer sample app more easily.
- [Fix] Fixed an issue where the "#EXT-X-START" tag was not calculated correctly.
- [Fix] Fixed an issue where the first I-Frame data was missing if the data was not located at the beginning of the HLS TS segments.
- [Fix] Fixed an issue where the player could not seek to 0 second position if a MP4 file contains "moof" and "trun" box.

### version 6.42.2.452
- [Optimization] Improved video performances.
- [Fix] Removed blank characters in TTML timed text.

### version 6.42.1.449
- [Optimization] Improved process when calculating video resolution without the crop flag.
- [Optimization] Improved Agama integration with view state management and error report.
- [Optimization] Modified process to retry connection when NexPlayer cant receive fragments while opening a content.


### version 6.42.0.444
- [Add] Supports Proxy server.
	Added the property 'PROXY_ADDRESS' to set proxy address.
	Added the property 'PROXY_PORT' to set proxy port.

### version 6.41.0.440
- [Add] Added a new DRM callback to handles HLS DRM content with a byte range. 
	DRM callback: NEXPLAYERHLSTSDescrambleWithByteRangeCallbackFunc().
- [Fix] Fixed issue with missing ID3 tags.

### version 6.40.7.436
- [Optimization] Improved video performances.

### version 6.40.6.435
- [Fix] Improved management of prefetch buffer.
- [Fix] Fixed issue with unstable video rendering after playback was paused and resumed by pressing the home button.
- [Fix] Fixed issue where the player started playback from 0 seconds again if the start time was set to a value bigger than end of seekable range.

### version 6.40.5.431
- [Optimization] Improved video performances.
- [Update] Improved audio playback performances.
- [Update] Support for HLS Sample Encryption added.
- [Fix] Fixed issue where timed metadata was duplicated.
- [Update] Updated video renderer library files.
	* 'libnexralbody_video_ics', 'libnexralbody_video_jb' have been merged into 'libnexralbody_video_nw'. Although the old libraries have been retained for backward compatibility, please replace these old libraries with 'libnexralbody_video_nw'.
	* 'libnexralbody_video_hc' has been removed, and merged into 'libnexralbody_video_opengl'.
- [Fix] Improved exception handling of consecutive calls of NexALFactory release.

### version 6.40.4.425
- [Optimization] Improved video performances.

### version 6.40.3.423
- [Optimization] Adjusted TTML caption text area when using a custom font.

### version 6.40.2.422
- [Optimization] Improved video performances.

### version 6.40.1.420

### version 6.40.0.419
- [Optimization] Improved video performances.
- [Optimization] 'Start time' is applied during HLS live content.
- [Add] Added a new 'open' API for opening content.
		public int open(String path, String smiPath, String externalPDPath, int type, int transportType);
	Existing 'open' API with the 'bufferingTime' parameter will be deprecated.
- [Optimization] Removed 'getSMIClassInfo()' API that is not used anymore.
- [Optimization] Improved Client-Side TimeShift performance.


### version 6.39.0.413
- [Optimization] Add support for remote external subtitle files.
- [Fix] Improved performance when starting video. 
- [Add] Add new API 'setClientTimeShift' to set backward buffer duration for client-side timeshift in live content.
		public native int setClientTimeShift(boolean bEnable, String strFileBufferPath, int uiTimeShiftBufferSize, int uiTimeShiftDuration, int uiMaxBackwardDuration);
- [Optimization] Changed android.util.FloatMath to java.lang.Math due to deprecation of that API.

### version 6.38.0.408
- [Add] Added a new API 'setNetAddrTable' to set a custom IP address based on the hostname.
		public int setNetAddrTable(NexNetAddrTable table, int nNetAddrTableType);
- [Fix] Added exception handling for LivePlaybackController.
- [Fix] Fixed an issue caused by an invalid AudioTrack state.
- [Fix] Added exception handling to prevent a crash from occurring when parsing ID3Tag.
- [Fix] Fixed an issue with start time calculation.

### version 6.37.0.404
- [Optimization] Improved video performances.
- [Optimization] Improved Offline Store feature. Content is not downloaded again if it has already been downloaded.
- [Fix] Fixed issue where the player couldn't set a starting position for playback of HLS content where audio and video are provided in different ts files respectively.
- [Optimization] Improved startup time when starting playback of PD (progressive download) content.
- [Add] Added a new API 'changeSubtitlePath' to allow subtitles to be changed during playback.
		public native int changeSubtitlePath(String path);
- [Optimization] Improved A/V sync performance.

### version 6.36.0.398
- [Fix] Fixed issue where AAC codec crashed when reset was called during decoding.
- [Update] Improved progressive download start time when network throughput is low.
		public String getUniqueID(Object appContext, NexUniqueIDVer ver);
		public String getUniqueID(Object appContext, String key, NexUniqueIDVer ver);
		public int setUniqueIDVer(NexUniqueIDVer ver);

### version 6.35.0.393
- [Add] Added new "Store offline" feature (content can be stored for offline play, without having to play the content when storing).
- [Fix] Fixed issue where video render was freezing when setOutputPos API was called.
- [Update] Added support for multi-language tracks in TTML timed text.

### version 6.34.2.390
- [Fix] Fixed issue where a pointer was referencing the wrong object when trying to delete a cookie.

### version 6.34.1.388
- [Optimization] Improved video performances.
- [Optimization] Changed NexPlayer logs to be concealed ONLY when the log level is set to -1.
	Removed additional logs.
- [Fix] Fixed issue where, after seeking forward during HLS playback, it was no longer possible to seek back to the beginning of the HLS content.
- [Fix] Fixed issue where timed metadata was being dropped after an ad was played back.
- [Fix] Fixed issue where the player buffered twice after seeking to an arbitrary time during playback of certain content.

### version 6.34.0.383
- [Optimization] Changed to conceal NexPlayer logs when the log level is set -1.
- [Fix] Fixed issue where PTS was skipped because of DSI information changing incorrectly.
- [Fix] Fixed an issue where the player didn't get an ERROR callback when the network or server was disconnected.
- [Add] Added 'NexABRController' to provide the application with ABR related methods.

### version 6.33.0.377
- [Optimization] Improved video performances.
- [Fix] Fixed issue of noise being heard when using speed control.
- [Fix] Fixed issue where the player crashed when closed with an invalid sequence.
- [Add] Added support for the client-side time-shift feature to allow seeking and pausing while playing live content.
- [Fix] Fixed issue where the player made an invalid byte range when the byte range wasn't specified, .
- [Fix] Fixed issue where timed metadata was being dropped.
- [Optimization] Re-inclusion of async task 'NEXPLAYER_ASYNC_CMD_NONE'.

### version 6.32.1.372
- [Optimization] Added an exception handler to avoid calling register functions before NexPlayer is released.

### version 6.32.1.371
- [Optimization] Improved video performances.
- [Fix] Fixed the issue where audio was silenced when starting some PD content randomly.

### version 6.32.0.370
- [Optimization] Improved video performances.
- [Add] Added FastPlay feature for HLSv04 I-Frame only track.
- [Fix] Fixed issue where the player didn't send END_OF_CONTENT event on 'Kindle Fire HD' devices.
- [Optimization] Removed unnecessary logs.
- [Fix] Fixed issue where the player, using openGL renderer, was rewinding slightly when a track was changed.
- [Fix] Fixed an issue where the audio track crashed when it failed to get some Android resources (by adding exception).
- [Optimization] Redesigned NexPlayer for more stable stop/start in Live play.
- [Fix] Improved audio track selection algorithm when there are more than 2 audio streams (AAC, AC-3) in 1 TS segment.
- [Optimization] Removed mention of unused listeners in documentation, in chapter "1.12. Support for Time Shift in Live Content".
- [Fix] Fixed network protocol error when streaming HLS content by improving handling routine when generating DSI data.
- [Fix] Fixed issue where video wasn't displayed for specific cases.
- [Fix] Fixed issue with playback of content that includes 2 DTS audio frames in one PES packet.
- [Optimization] Removed unclear error codes.

### version 6.31.3.364

### version 6.31.3.361
- [Optimization] Improved video performances.
- [Fix] Fixed video parsing error for H.265 content.
- [Fix] Fixed issue where the player was blocked for a 60 second timeout in SSL_Socket API.
- [Fix] Fixed issue where the player couldn't find group-IDs in HLS audio-only content with multiple group-IDs.
- [Fix] Improved the algorithm that shortens buffering time when an HLS track is changed during playback.
- [Fix] Improved decoding and rendering of WebVTT captions.
- [Optimization] Added exception handling when audio decoder output configuration has been changed.
- [Fix] Improved the algorithm for calculating timestamps in Smooth Streaming content.

### version 6.31.2.360

### version 6.31.1.354
- [Optimization] Improved video performances.
- [Fix] Fixed issue where SMI caption couldn't be displayed during playback.
- [Fix] Improved playback stability in HLS.

### version 6.31.0.350
- [Optimization] Improved video performances.
- [Fix] Improved H.265 playback stability.
- [Optimization] Improved support for multiple audio group-IDs in HLS content.

### version 6.30.1.347

### version 6.30.0.346
- [Optimization] Improved HEVC performance.
- [Fix] Improved rendering stability.
- [Fix] Improved playback stability.

### version 6.29.0.342
- [Optimization] Improved video performance.
- [Optimization] Improved playback stability in HLS.
- [Update] Updated AC3 2.0 codec library.
- [Add] Added setAudioPitch() API to adjust the pitch of audio in content.
- [Add] Added support for "Dynamic Thumbnail Preview" feature in Smooth Streaming.

### version 6.28.4.338

### version 6.28.3.337

### version 6.28.2.336
- [Optimization] Improved video performances.
- [Fix] Improved video playback stability.

### version 6.28.1.334
- [Optimization] Improved video playback stability.

### version 6.28.0.333
- [Fix] Improved playback stability during Live streaming.
- [Add] Added new API changeMinBandWidth(), changeMinMaxBandWidth().
- [Optimization] Improved Video renderer stability.
- [Fix] Improved seek operation. 
- [Fix] Improved video playback stability in PD streaming.

### version 6.27.0.329
- [Optimization] Improved video performances.
- [Update]	Added support for HEVC codec in HLS.
- [Add] Added support for client-side time-shift feature to seek and pause while playing live contents.

### version 6.26.1.324
- [Optimization] Improved SW CODEC DOWNLOAD module to download SW-codec in normal.

### version 6.26.0.323
- [Fix] Added SSL_set_tlsext_host_name() function which sets TLS host name and address in case of SSL connection failures.
- [Add] Added HTTP downloader callback. 
	NEXHD_CALLBACK_PARAM_CONNECT, NEXHD_CALLBACK_SETINFO_CONNECT, NEXHD_CALLBACK_PARAM_CONNECTED, NEXHD_CALLBACK_SETINFO_CONNECTED, NEXHD_CALLBACK_PARAM_MSG_SENT, NEXHD_CALLBACK_ERRCODE are added.
- [Update] Improved ABR algorithm.
- [Add] Added new APIs to NexVideoRenderer and GLRenderer to resolve memory issues with older devices.
	NexVideoRenderer.onPause, NexVideoRenderer.onResume, GLRenderer.setListener are added.
- [Add] Added the property, 'isLive', to NexClient.
	PREF_BOOL_IS_LIVE is added.
- [Optimization] Improved HLS stability.

### version 6.25.1.311
- [Optimization] Improved video performances.

### version 6.25.0.310
- [Add] Added new property to disable the Audio Only track in HLS content.
	NexProperty.ENABLE_AUDIOONLY_TRACK : Sets whether to enable or disable Audio Only track in HLS. 
- [Add] Added new property for better sync between the audio and video tracks when playing content with wrong time stamps.
	NexProperty.SEGMENT_TS_RELIABLE : Sets whether to trust content's timestamps.
- [Add] Added new property to continue downloading data in pause state with HLS content. 
	NexProperty.CONTINUE_DOWNLOAD_AT_PAUSE : Sets whether to continue downloading HLS data when playback has paused.

### version 6.24.3.306
- [Optimization] Improved video performances.
- [Update] Added support for #EXT-X-DISCONTINUITY tag in HLS.
- [Optimization] Fixed finilizer error at Android 5.0

### version 6.24.2.302
- [Optimization] Improved video performances.
- [Update] Fixed an issue with crashes when using the Conviva library.
- [Update] Removed HTTP range header in HLS requests. Certain servers didn't reply correctly if the range header is included.
- [Update] Updated device security checking module for Android 5.0 devices.

### version 6.24.1.300
- [Add] Added a new API for VM callback (for KeyRetrievalStatus, ConfigureOutputControlSettings, OperatorData)
- [Optimization] Improved video performances.
- [Update] Added exception handling for when the system returns a wrong profile length.
- [Update] Improved TimeStamp calculation at HLS.

### version 6.23.6.292
- [Optimization] Improved video performances.

### version 6.23.6.291
- [Update] Improved the A/V sync on Kindle Fire.

### version 6.23.5.288
- [Optimization] Improved video performances.

### version 6.23.4.287
- [Update] Added support for rendering HTML symbols in TTML timed text.
- [Update] Improved stability of Progressive Download. 

### version 6.23.3.283
- [Update] Improved HLS algorithm when transfer encoding mode is chunked.
- [Update] Added support for text alignment in TTML timed text captions.
- [Update] Improved stability for HLS.
- [Update] Improved A/V sync on Samsung devices running Kitkat.
	
### version 6.23.2.279
- [Update] Updated the sample code for NexHD callback.
- [Update] Added support for caption styling of TTML timed text in Smooth Streaming content.
- [Update] Added support for the "line" tag in WebVTT text tracks.

### version 6.23.1.277
- [Update] Improved CEA 608 CEA 708 closed caption performance.

### version 6.23.0.274
- [Add] Added new a API, NexVideoRenderer::release(). Please see doc section 5.54.3.11 for more information. This can be ignored if this new API is not useful to you.
- [Add] Added new APIs, NexPlayer::IReleaseListener, NexPlayer::addReleaseListener(), NexPlayer::removeReleaseListener() to handle release events. Please see doc section 5.23 for more information. These can be ignored if the new APIs are not needed.
- [Update] Added support for "#EXT-X-START" tag in HLS.
- [Update] Improved playback with large playlists in HLS.
- [Optimization] Improved video performances.

### version 6.22.4.269
- [Update] Improved stability of audio renderer.

### version 6.22.3.267
- [Optimization] Improved video performances.
- [Update] Improved algorithm for changing audio tracks.
- [Update] Improved redundant stream selection algorithm in HLS streaming.

### version 6.22.2.263
- [Update] Improved text track selection algorithm.

### version 6.22.1.259
- [Optimization] Improved video performances.

### version 6.22.0.258
- [Optimization] Improved video performances.
* [Optimizaion] Improved stability for HLS
- [Add] Added new property NexProperty.PREFER_LANGUAGE_AUDIO to set the language of audio played in multistream content.
- [Add] Added new property NexProperty.PREFER_LANGUAGE_TEXT to set the language of text played in multistream content.
- [Optimization] Improved handling of timed metadata.

### version 6.21.1.254
- [Optimization] Improved A/V sync on Kindle Fire HDX

### version 6.21.0.249
- [Optimization] Improved TimedMeta A/V sync module.
- [Optimization] Improved video performances.
- [Add] Added new API, NexCaptionRenderer::setDefaultTextSize, to change default text size.
- [Add] Added new API, NexCaptionRenderer::setLineSpacingRate, to change space size between lines.

### version 6.20.1.245
- [Optimization] Support MP4 container contents in external progressive dowonload.

### version 6.20.0.240
- [Optimization] Improved CEA 708 closed caption renderer.
- [Add] Added support for image-based captions.

### version 6.19.1.239
- [Optimization] Improved playback of CFF contents.
- [Optimization] Improved CEA 708 closed caption renderer.

### version 6.19.0.235
- [Optimization] "VideoOnOff" feature optimized by stopping decoding when Audio or Video are stopped to reduce battery consumption.
- [Optimization] Improved video performances.

### version 6.18.2.231
- [Optimization] Improved video performances.
- [Add] Added "Start Seconds" property in the Sample APP.
- [Optimization] Improved ID3 metadata events.
- [Optimization] Improved playlist parsing.
- [Optimization] Improved HLS protocol.
- [Optimization] Improved WebVTT parser.

### version 6.18.1.226
- [Optimization] Improved video performances.
- [Optimization] Improved CEA 608 and WebVTT closed caption renderer.

### version 6.18.0.221
- [Optimization] Improved handling of ID3 metadata events.
- [Optimization] Improved calculation of Presentation Timestamp (PTS).
- [Optimization] Improved Timeout behavior when seeking.
- [Optimization] Improved CEA 608 closed caption renderer.

### version 6.17.1.217
- [Optimization] Improved WebVTT renderer.

### version 6.17.0.216
- [Optimization] Support using only the Android HW codec with H264 content.
- [Optimization] Changed the Android target SDK ### version of the Sample app (from 9 to 19).
- [Optimization] Improved frame error handling when using AAC decoder.
- [Optimization] Improved WebVTT renderer.
- [Optimization] Improved CEA 708 closed caption renderer and caption preview.
* [Optimizaion] Improved stability of A/V sync when changing audio streams in live content.

### version 6.16.0.211
- [Optimization] Improved video performances.
- [Add] Added new API, NexClosedCaption::setShadowWithColor, to set whether CEA 608 closed captions should be displayed with a colored shadow.
- [Add] Added new class, "NexCodecInformation", to store and provide information about an individual codec.
* Added NexCodecInformation.java file.

### version 6.15.0.207
- [Optimization] Improved stability of property, "HLS_RUNMODE"
- [Optimization] Improved closed caption renderer.
- [Add] Added new API, NexCaptionRendererForWebVTT::setDefaultTextSize(), to set default text size for WebVTT caption text.
- [Add] Added new API, NexCaptionRendererForTimedText::setWindowMargin(), to set a margin around caption text to the edge of the caption window for TimedText.
- [Add] Added new class, "NexCaptionPreview", to preview the look of captions when users set caption styles such as color, size, and edge style effects. * Added NexCaptionPreview.java file.
- [Fix] Fixed an issue where specific content with DFXP closed captions did not play properly.

### version 6.14.0.204
- [Optimization] Extended support for all ID3 Tags formats.
- [Add] New functionality added: NexProperty.START_NEARESTBW, to start playing HLS content with the track nearest to a specified bandwidth.
- [Add] Added new API,"setWindowMargin", to set a margin around caption text to the edge of the caption window in WebVTT text tracks.
- [Fix] Fixed WebVTT text track rendering so that captions are displayed in parallel when more than one string frame is displayed at the same time.
- [Fix] Fixed an issue where unnecessary calls were made to unrelated methods when playing captions.

### version 6.13.0.199
- [Fix] Fixed an issue with improper parsing of the HTTP response header.
- [Fix] Fixed AAC channel management when He-AACv2 audio profile is used. 
- [Add] Added a new property, NexProperty.WEBVTT_WAITOPEN, to avoid waiting for the first WebVTT segment to download when starting to play content.
- [Optimization] Improved video performances.

### version 6.12.2.195
- [Fix] setVolume functionality improved. 
- [Optimization] Improved CEA708 rendering.
- [Optimization] Improved video performances.
- [Optimization] Memory and security warning messages in KitKat OS are removed now.
* [Folder copied] Following folder has been copied from "Sample/NexPlayerSample_for_Android/" to "SDK/" for easier access. 
    Folder : jni_sample

### version 6.12.1.189
- [Optimization] Improved HLS/SmoothStreaming track change performance.

### version 6.12.0.187
- [Add] Added new API, NexPlayer::onHTTPResponse(), to allows responses from an HTTP server to be received and handled in a more customized way.
- [Add] Added new API, NexPlayer::onHTTPRequest(),to pass HTTP request messages to an application.
- [Optimization] Improved VMDRM deinitialization.
- [Optimization] Support added for Smooth Streaming content in non-standard mp4 container.
- [Optimization] Improved fast start feature in HLS.
- [Optimization] Support for ts files that don't include PAT/PMT(in HLS content).
- [Optimization] Improved CEA708 renderer.
- [Optimization] Improved WebVTT text track parser.
- [Optimization] Improved video performances.

### version 6.11.0.182
- [Add] Added static audio renderer library for KitKat OS.
- [Optimization] Improved buffering performance for mp4 files with 3GPP timed text tracks.
- [Fix] Improved connection algorithm for streaming content.
- [Optimization] Improved video performance.

### version 6.10.0.174
- [Update] Improved stability of the HW renderer.

### version 6.10.0.172
- [Add] Conviva/Agama library.
- [Add] Added support for side-loaded TTML subtitles.
- [Update] Improved video performance (v6.71).

### version 6.9.0.166
- [Update] Improved video performance (v6.69).
- [Add] Added new functionality to extract all ID3 metadata in content, including from customized tags.
- [Add] Added new variable, NexContentInformation::mCaptionType to indicate the type of captions in content.
- [Fix] Fixed an issue playing multiple audio-only tracks in multi track content.
- [Fix] Fixed an issue with font corruption at UI on specific device and OS ### version.
- [Fix] Fixed an issue with memory leaks.

### version 6.8.3.161
-[Fix] Fixed an issue with audio decoding error when the track is being changed.

### version 6.8.2.160
- [Fix] Improved WebVTT decoding performance.
- [Fix] Improved Timed Metadata rendering performance.

### version 6.8.1.157
- [Fix] Improved opacity rendering of 3GPP timed text when changing window and background color.
- [Fix] Improved stability of the audio renderer.

### version 6.8.0.154
- [Add] Added new property NexProperty.PREFER_LANGUAGE to set the language of both audio and text played in multistream content.
- [Add] Added support for offline playback in HLS/Smooth Streaming(when network connection is lost).

### version 6.7.1.148
- [Fix] Fixed an issue when the DRM callback is registered.

### version 6.7.0.143
- [Update] Improved video performance (v6.47).
- [Add] Added a parameter in the setVideoBitrates method to set video bitrate selection options for HLS content.
- [Add] Added an API, setSurfaceSecure, to prevent screen recording on devices running KitKat OS.

[NexCaptionRenderer Class]
- [Add] Added an API, setWindowColor, to allow the window color of CEA 608 closed captions to be set.
- [Add] Added an API, setUniform, to indicate whether or not CEA 608 closed captions should be displayed with a uniform black outline.

[NexCaptionRendererForTimedText Class]
- [Add] Added an API, setFGCaptionColor, to set the foreground (text) color of 3GPP/TTML timed text captions.
- [Add] Added an API, setBGCaptionColor, to set the background color of 3GPP/TTML timed text captions.
- [Add] Added an API, setCaptionStroke, to set the renderer stroke color and width of 3GPP/TTML timed text captions.
- [Add] Added an API, setCaptionWindowColor, to set the window color of 3GPP/TTML timed text captions.
- [Add] Added an API, setFontSize, to change the font size of 3GPP/TTML timed text captions.
- [Add] Added an API, setShadow,to display 3GPP/TTML timed text captions with a drop shadow.
- [Add] Added an API, setFonts, to set the fonts to be used for 3GPP/TTML timed text captions.
- [Add] Added an API, setRaise, to indicate whether or not 3GPP/TTML timed text captions should be displayed as if "raised".
- [Add] Added an API, setDepressed, to indicate whether or not 3GPP/TTML timed text captions should be displayed as if "depressed".
- [Add] Added an API, setUniform, to indicate whether or not 3GPP/TTML timed text captions should be displayed with a uniform black outline.
- [Add] Added an API, setEmbossSpecular, to set the specular level of the Emboss Mask filter used when a user sets 3GPP/TTML timed text to be 'Raised' or 'Depressed' in the UI.
- [Add] Added an API, setEmbossBlurRadius, to sets the blur radius of the Emboss Mask filter used when a user sets 3GPP/TTML timed text to be 'Raised' or 'Depressed' in the UI.

[NexCaptionRendererForWebVTT Class]
- [Add] Added an API, setFGCaptionColor, to set the foreground (text) color of WebVTT text cue captions.
- [Add] Added an API, setBGCaptionColor, to set the background color of WebVTT text cue captions.
- [Add] Added an API, setCaptionStroke, to set the renderer stroke color and width of WebVTT text cue captions.
- [Add] Added an API, setCaptionWindowColor, to set the window color of WebVTT text cue captions.
- [Add] Added an API, setTextSize, to change the font size of WebVTT text cue captions.
- [Add] Added an API, setShadow, to display WebVTT text cue captions with a drop shadow.
- [Add] Added an API, setFonts, to set the fonts to be used for WebVTT text cue captions.
- [Add] Added an API, setRaise, to indicate whether or not WebVTT text cue captions should be displayed as if "raised".
- [Add] Added an API, setDepressed, to indicate whether or not WebVTT text cue captions should be displayed as if "depressed".
- [Add] Added an API, setUniform, to indicate whether or not WebVTT text cue captions should be displayed with a uniform black outline.
- [Add] Added an API, setEmbossSpecular, to set the specular level of the Emboss Mask filter used when a user sets WebVTT text cues to be 'Raised' or 'Depressed' in the UI.
- [Add] Added an API, setEmbossBlurRadius, to sets the blur radius of the Emboss Mask filter used when a user sets WebVTT text cues to be 'Raised' or 'Depressed' in the UI.

- [Fix] Improved WebVTT text cue caption rendering performance.
- [Fix] Cut down the buffering time when starting streaming content.

### version 6.6.5.132
- [Update] Improved video performance (v6.0).
- [Fix] Improved how the renderer is loaded.
- [Fix] Improved track change performance when audio or video DSI changes.

### version 6.6.4.128
- [Update] Improved video performance (v5.88).
- [Fix] Improved how the SW codec library is loaded.

### version 6.6.3.127
- [Update] Improved video performance (v5.84).
- [Update] Sample app UI updated.
- [Fix] Added caption display time information & attributes in NexCaptionRenderer, NexCaptionRendererForTimedText, NexCaptionRendererForWebVTT and NexEIA708CaptionView.
- [Add] Added APIs, getM_border_X, setM_border_X, getM_border_Y, and setM_border_Y to set where CEA 608 closed captions will be displayed relative to content.
- [Add] Added APIs, getStartTimeStampForWebVTT and getEndTimeStampForWebVTT to return the starting and ending timestamps of WebVTT text cues.
- [Fix] Improved track change performance * player waits to re-initiate audio renderer if data remains in buffer.
- [Fix] Improved CEA 708 closed caption support * if called Reset, SetPenAttribute, clearing captions, setTextSize, roll-up, SetPenLocation.
- [Fix] Improved WebVTT rendering performance.

### version 6.5.2.124
- [Update] Improved video performance (v5.28).
- [Add] Added a new API, setVideoBitrates, to play specific subtracks in HLS.

### version 6.5.1.117
- [Update] Improved video performance (v4.86).
- [Fix] Improved performance of PTS calculation.

### version 6.5.0.113
- [Update] Improved video performance (v4.80).
- [Add] Added API setDebugLogs to get more detailed logs.
- [Fix] Improved caption support (CEA 708 and support for WebVTT HTML tags)
- [Fix] Improved track down performance to minimize delay.
- [Fix] Improved track change performance while seeking when both Audio and Video DSI change.

### version 6.4.1.106
- [Update] Improved video performance (v4.12).
- [Update] Optimizations for Android 4.4.

### version 6.4.0.100
- [Update] Improved video performance (v3.89).
- [Add] Support for HLS V5.
- [Add] Support for WebVTT.

### version 6.3.8.90
- [Fix] Improved H264 bitstream parsing.

### version 6.3.7.89
- [Update] Improved video performance (v3.86).
- [Fix] Improved B-frame reordering.
- [Fix] Fixed an issue with time stamp detection when using multi-channel content or when tracking down.

### version 6.3.6.83
- [Update] Improved video performance (v3.82).
- [Fix] Fixed SW video codec structure for AVC.

### version 6.3.5.81
- [Update] Improved video performance (v3.74)
- [Update] Further optimizations for Android ### version 4.3

### version 6.3.4.78
- [Update] Improved video performance (v3.68)
- [Update] Optimizations for Android 4.3.

### version 6.3.3.72
- [Update] Improved video performance (v3.62).
- [Update] Support for Android Jellybean, ### version 4.3.
- [Fix] Improved track down performance so that all tracks of content may be selected/played.

### version 6.3.2.63
- [Update] Improved video performance (v3.51).
- [Fix] Improved the renderer to avoid an issue when attempting to play content and then immediately exiting.
- [Fix] Added exception handling when playing HLS Live streaming.

### version 6.3.1.60
- [Update] Improved buffering performance for Live links.
- [Fix] Added exception handling when closing NexPlayer.
- [Fix] Added exception handling when drawing logo.

### version 6.3.0.56
- [Update] Improved video performance (v3.50).
- [Add] Added libnexralbody_video_jb.so for certain devices.
- [Add] Added a descramble callback for AES128 encrypted HLS content: HLSAES128Descramble Callback.
- [Add] Added a new API, setUserCookie, to set user cookies while content is playing.
- [Add] Added support for registering DL functions (dlopen , dlclose, dlsym, dlerror).
- [Add] Added support for gzip in HLS.

### version 6.2.2.46
- [Update] Improved video performance (v3.42).
- [Optimization] Changed AVC profile from baseline to main/high.
- [Fix] Improved srt subtitle renderer.
- [Fix] Fixed an issue with an ANR (Application Not Responding) error occurring in STOP state.
- [Fix] Fixed a decoding error when using specific contents.
- [Fix] Fixed an infinite buffering issue when trying to seek.
- [Fix] Fixed an issue with NexPlayer running on Donut or Eclair.
- [Fix] Fixed an issue with the OpenGL renderer not working properly with Gingerbread OS.

### version 6.2.1.44
- [Add] Added a seekbar in the sample application.
- [Fix] Improved playlist parsing.

### version 6.2.0.43
* [COMMON][Update] Further optimizations for better video performance (v3.31).
- [Fix] An issue with an invalid PTS value.
- [Fix] An issue with an infinite loop in the case of audio-only content.
- [Update] Improved changing between video tracks.
- [Fix] Fixed an issue with NEXPLAYERMPDDescrambleCallbackFunc being called when it was only the Top level index/manifest.
- [Fix] Added track codec type information in the NexTrackInformation class, with the member mCodecType.
- [Fix] An issue with socket connection.
- [Add] Added a check for Listener before opening player.
- [Add] Added API getCurrentPosition() to get current play time position in content.

### version 6.1.3.37
- [Fix] Fixed an issue crashing in Smooth Streaming captions.
- [Fix] Fixed an issue using 2 channel audio.
- [Update] Updated list of HW-supportable devices.

### version 6.1.2.31
- [COMMON][Update] Updated list of HW-supportable devices.
- [Add] Added support for CEA 708 closed captions.
    Added Property: NexProperty.ENABLE_CEA708
    Added Classes: NexEIA708CaptionView.java, NexEIA708Struct.java, NexLogStringQueue.java
- [Fix] An issue with captions not clearing in Smooth Streaming content.
- [Add] A new Render mode : Added auto mode, which selects which renderer to use automatically.
- [Fix] An issue with Galaxy S4 crashing.
- [Fix] Improved performance with MP/HP content by improving the way of PTS calculation.

### version 6.1.1
- [Fix] An "invalid file format" message that occurred when playing certain content.
- [Add] Added support for the API, videoOnOff, when using HW renderer.
- [Fix] An issue with a codec error message appearing.
- [Fix] An issue with the value of audioDts being reset to 0 after seeking.
- [Add] Added the new API, getAudioSessionId().
- [Update] Updated list of HW-supportable devices.

### version 6.1.0
- [Fix] An issue with CEA 608 closed captions failing to be displayed when a seek command completed. * mantis 5726
- [Add] Added a new API for H.264 SAR (sample aspect ratio) information (NexPlayer.getSARInfo()).
- [Add] Added a new render mode to support all devices automatically(NexVideoRenderer, IVideoRendererListener).
- [Add] Added new property NexProperty.MIN_BW to set the minimum bandwidth to be played in HLS content.
- [Fix] An issue with H/W decoder libraries failing to load with JB devices.
- [Add] Added support for CEA608 closed captions in PD content.
- [Fix] An issue with the local subtitles(SRT, SMI files) being skipped when a seek command completed.
- [Fix] An issue with the proxy server address failing to be set from the NexPlayer.setProperties() API.

### version 6.0.5
- [Add] Added new TimedMeta parameters(Text and Comment) for HLS/IceCast content.
- [Fix] An issue where CEA 608 closed captions were being displayed in a jumble in H264 high profile content.
- [Add] Added a new API NexPlayer.reconnectNetwork().
- [Add] Added a new buffer monitoring API, NexPlayer.getBufferInfo().
* [Note] NexPlayer automatically detects the devices where HD and Main/High H.264 profiles can be supported, so there is no need to indicate any device model to the player.
- [Add] Added new property NexProperty.SOURCE_OPEN_TIMEOUT
- [Add] Added new property NexProperty.PREFETCH_BUFFER_SIZE
- [Add] Added new property NexProperty.MIN_BUFFER_RATE
- [Add] Added new property NexProperty.MAX_BUFFER_RATE
- [Add] Added new property NexProperty.MIN_BUFFER_DURATION
- [Add] Added new property NexProperty.MAX_BUFFER_DURATION
- [Add] Added new property NexProperty.SEEK_RANGE_FROM_RA_POINT
- [Add] Added new property NexProperty.IGNORE_CARRIAGERETURN_WHEN_RECEIVE_ROLLUP
- [Add] Added new property NexProperty.ENABLE_MODIFY_HTTP_REQUEST
- [Add] Added a new method in IListener of the JAVA layer in order to enable modified HTTP requests. An application should implement 'onModifyHttpRequest()'.
- [Add] Added support for SEI Picture Timing information in HLS with NexPictureTimingInfo class.
- [Update] HW decoder libraries were renamed(libnexcal_oc_dec_xx.so --> libnexcal_oc_xx.so)

### version 6.0.4
- [Update] This SDK ### version is upgraded but is combined with the features and APIs of the latest SDK ### version 5.14.1.7653.
- [Update] Changes between this ### version of the SDK and the last ### version are explained in the included Differences document.
- [Fix] An issue where I-Frames were not found in PIFF DRM content was resolved.
- [Fix] An issue with track jittering (when the track changed in HLS and Smooth Streaming) was resolved.
- [Fix] An issue with tracks not changing during buffering (when starting and seeking in Smooth Streaming content) was resolved.
- [Fix] An issue with green frames appearing during playback with the OpenGLRenderer (when devices running Jelly Bean were rotated) was resolved.
