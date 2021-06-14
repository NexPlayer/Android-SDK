<a href="https://nexplayersdk.com/html5-player/"><img text src="./assets/logo5.png" alt="Nexplayer"></a>

***

# NexPlayer™ SDK for Android Documentation

### Capabilities and Limitations

#### Operating Systems

- Android 4.4 and above

#### Functionalities

- Basic video controls: start, seek, stop
- H.264 aspect-ratio
- H.264 Picture Timing SEI Parsing
- Eye-pleaser (seamless frame skipping method) 
- ID3 Tags (including Private Frame Data)
- EMSG Events
- Set Video Output Position
- Adjust Audio Output Volume
- Set subtitle display property
- Generate playback statistics information 
- Multiple Instance
- Chromecast Pre-integrated
- Android TV Input
- Calculate Average Audio Roundnes
- Select Media Stream (Multi-Audio/Video/Subtitle) Turn on/off Media Stream

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
- Dolby SW Codecs
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
_Subject to additional and/or 3rd party licenses_

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

- NexPlayer SDK for iOS
- NexPlayer SDK for Web
- NexPlayer STB SDK (to be customized for each for Android Set-Top Box/Android TV) 
- NexPlayer Unity Plugin
- NexPlayer Nintendo Plugin

***

### Legal Notices

**Disclaimer for Intellectual Property**

This product is designed for general purpose, and accordingly the customer is responsible for all or any of
intellectual property licenses required for actual application. NexStreaming. does not provide any indemnification for any intellectual properties owned by third party.

**Copyright**

Copyright for all documents, drawings and programs related with this specification are owned by NexStreaming. All or any part of the specification shall not be reproduced nor distributed without prior written approval by NexStreaming. Content and configuration of all or any part of the specification shall not be modified nor distributed without prior written approval by NexStreaming.