# NexPlayer Error Codes

Possible error codes that NexPlayer can return. This is a Java enum so each error constant is an object, but you can convert to or from a numerical code using instance and class methods.

To get the error constant for a given code, call `fromIntegerValue(int)`.

To get the error code given an error constant, call `getIntegerCode()`.

Because this is a Java enum, it is very easy to include the name of the error constant in an error message instead of just the number. For example, the following code logs the errors that are received from the NexPlayer engine:

```java
void onError( NexPlayer mp, NexErrorCode errorCode ) {
    NexLog.d( "onError",
        "Received the error: "
            + errorCode.name()
            + " (0x"
            + Integer.toHexString(
                errorCode.getIntegerCode())
            + ")."
        );
```

### `HAS_NO_EFFECT` 
`0x00000001`

Method has no effect. The same command has been called already in the same state or the command is invalid.

### `INVALID_PARAMETER` 
`0x00000002`

Parameter is invalid. This error will be called if the UI has wrong parameters such as NULL.

### `INVALID_STATE` 
`0x00000004`

State is invalid. The command is invalid at the current state. E.g. pause() is called when the current state is `NEXPLAYER_STATE_STOP`.

### `INVALID_MEDIA`
`0x00000007`

File contains invalid syntax. The content file contains invalid syntax. It should be checked whether or not the content is a normal DRM file.

### `NOT_SUPPORT_AUDIO_CODEC` 
`0x00000009`

The audio codec is not supported. NexPlayer does not support the audio codec of the content. E.g. The content is not yet supported by NexPlayer or a customer could not include codecs of NexPlayer SDK due to licensing issues.


### `NOT_SUPPORT_VIDEO_CODEC` 
`0x0000000A`

The video codec is not supported. NexPlayer does not support the video codec of the content. E.g. The content is not yet supported by NexPlayer or the customer did not include codecs of NexPlayer SDK due to licensing issues.

### `NOT_SUPPORT_VIDEO_RESOLUTION` 
`0x0000000B`

The video resolution is not supported. The resolution of the content is too high to play back. E.g. The device has a resolution limit of 1080P but the content is 4K.

### `NOT_SUPPORT_MEDIA` 
`0x0000000C`

The content format is not supported or is not playable A/V track. The format of the content is not supported. The content has unavailable protocol(HLS,DASH, etc) or no playable A/V track which has audio or video codecs that are not supported.

### `CODEC_DECODING_ERROR` 
`0x0000000E`

The codec reported an error. Audio or video decoding error. E.g.  NexPlayer get a failure during parsing the content for playback or during decoding the audio or video bitstreams.

### `UNKNOWN` 
`0x00000017`

Unknown error. This error is a kind of internal error such as "system failure". E.g. NexPlayer returns this when memory allocation is failed for unknown reasons. It's mostly an error that the user can not handle. Please contact a NexPlayer developer for more details.

### `NOT_SUPPORT_TO_SEEK` 
`0x00000018`

The media source does not support seeking. The only Iframe content(Content is composed of I, B, and P frames), chunked mode based PD content, or live content with an wide interval between each Iframe cannot be seeked.


### `NOT_SUPPORT_TEXT ` 
`0x0000001E`

The text is not supported. The content has an unsupported text type. 

### `SOURCE_OPEN_TIMEOUT` 
`0x00000023`

The media source open timed out. There is no response from the server within the set time of SOURCE_OPEN_TIMEOUT property while calling open(). The default value of the SOURCE_OPEN_TIMEOUT property is 300 seconds.

### `DATA_INACTIVITY_TIMEOUT` 
`0x00000026`

The response timed out. There is no response from the server within the set time of DATA_INACTIVITY_TIMEOUT property. The default value of the DATA_INACTIVITY_TIMEOUT property is 60 seconds.

### `ERROR_NETWORK_PROTOCOL` 
`0x00000029`

Network or protocol error. Network related error such as socket errors. Ex. socket open fail, connect fail, bind fail etc.

### `ERROR_MEDIA_NOT_FOUND` 
`0x0000002A`

The content media was not found. The content media was not found on the server. Ex. 403 forbidden, 404 not found etc.      

### `DRM_DECRYPT_FAILED` 
`0x00000022`

The content DRM decrypt fail. The default error of content DRM Decrypt Fail

### `DRM_INIT_FAILED` 
`0x0000002C`

The content DRM initialization fail. Ex. Invalid License URL.

### `DRM_INSUFFICIENT_HDCP_LEVEL` 
`0x0000002D`

HDCP levels are insufficient to meet the requirements. 

### `DRM_NOT_SUPPORT_HDCP` 
`0x0000002E`

HDCP is not supported on the device.

### `DRM_DECRYPT_NO_KEY` 
`0x00000031`

Crypto key not available.

### `DRM_DECRYPT_NO_KEY` 
`0x00000032`

DRM license expired.

### `DRM_DECRYPT_RESOURCE_BUSY` 
`0x00000033`

DRM Resource busy or unavailable

### `DRM_DECRYPT_SESSION_NOT_OPENED` 
`0x00000034`

Attempted to use a closed drm session

### `DRM_DECRYPT_SESSION_NOT_OPENED` 
`0x00000035`

Drm Operation not supported in this configuration, The content DRM Decrypt Failed.

### `DRM_DECRYPT_INSUFFICIENT_SECURITY` `0x00000036`

Required security level is not met.

### `DRM_DECRYPT_FRAME_TOO_LARGE ` `0x00000037`

Decrytped frame exceeds size of output buffer.

### `DRM_DECRYPT_LOST_STATE` `0x00000038`

DRM Session state was lost.

### `MEDIACODEC_INSUFFICIENT_RESOURCE` 
`0x00000039`

Required resource was not able to be allocated.

### `MEDIACODEC_RECLAIMED` 
`0x0000003A`

Resource manager reclaimed the media resource used by the codec.

### `ERROR_INVALID_URL` 
`0x00010001`

The URL is invalid.

### `ERROR_INVALID_RESPONSE` 
`0x00010002`

The syntax of the response is invalid. Ex. Mandatory header is missed in the response.

### `ERROR_CONTENTINFO_PARSING_FAIL` 
`0x00010003`

ContentInfo parse fail. (SDP, ASF Header, Playlist...)

### `ERROR_NET_CONNECTION_CLOSED` 
`0x0001000A`

Socket connection closed.

### `ERROR_NET_REQUEST_TIMEOUT` 
`0x0001000D`

Response is not arrived until timeout.

### `ERROR_INVALID_SERVER_STATUSCODE` 
`0x00020000`

The HTTP response data recevied from the Server is error. It's not 200 in HTTP response. Ex. 500, 503 etc

### `ERROR_DISABLED_MEDIA` 
`0x00010010 `

No track to play due to a bitrate/resolution limit. E.g. The MIN_BW property is set to 2 Mbps and the playlist of playing contain has only 500 Kbps and 1 Mbps tracks.


### `ERROR_AES_KEY_RECV_FAIL` 
`0x00010011`

Failed to download the key file to decrypt the file that has been encrypted with AES.
		

### `HTTPDOWNLOADER_ERROR_FAIL` 
`0x00100001`

NexPlayer met some errors when creating HTTP Downloader.


### `HTTPDOWNLOADER_ERROR_UNINIT_ERROR` 
`0x00100002`

The user called a part of HTTP Downloader before creating or initializing.


### `HTTPDOWNLOADER_ERROR_INVALID_PARAMETER` 
`0x00100003`

A parameter from the UI is null or an incorrect value when HTTP downloader sends the message.

### `HTTPDOWNLOADER_ERROR_MEMORY_FAIL` 
`0x00100004`

Http downloader failed to allocate or free memory.
            
### `HTTPDOWNLOADER_ERROR_SYSTEM_FAIL` 
`0x00100005`

System related error.            

### `HTTPDOWNLOADER_ERROR_WRITE_FAIL` 
`0x00100006`

Http downloader writing failure.

### `HTTPDOWNLOADER_ERROR_HAS_NO_EFFEECT` 
`0x00100007`

The user attempted to call the same method many times. All duplicates (except the first one) will be regarded as an error.

### `HTTPDOWNLOADER_ERROR_EVENT_FULL` 
`0x00100009`

Http downloader event is full

### `HTTPDOWNLOADER_ERROR_NETWORK` 
`0x00120000`

Http downloader failed to connect to a network.

### `HTTPDOWNLOADER_ERROR_NETWORK_RECV_FAIL` 
`0x00120001`

Http downloader received an invalid response from the server.

### `HTTPDOWNLOADER_ERROR_NETWORK_INVALID_RESPONSE`
`0x00120002`

Http downloader received an invalid response from the server.

### `HTTPDOWNLOADER_ERROR_PARSE_URL` 
`0x00120003`

Http downloader detected an incorrect URL.

### `HTTPDOWNLOADER_ERROR_ALREADY_DOWNLOADED ` 
`0x00130000`

Http downloader requested an already downloaded content file.

### `UNSUPPORTED_SDK_FEATURE` 
`0x70000001`

NexPlayer detected an unsupported feature(i.e. recording or timeshift) or called a specific feature.

### `PLAYER_ERROR_NO_LICENSE_FILE` 
`0x800000C0`

NexPlayer initialization failed by License File.

### `PLAYER_ERROR_INVALID_SDK` 
`0x8000000D`

NexPlayer initialization failed by the invalid SDK. Error while creating or initializing NexPlayer.

### `PLAYER_ERROR_INIT` 
`0x80000011`

Error while creating or initializing NexPlayer.

### `PLAYER_ERROR_NOT_ACTIVATED_APP_ID` 
`0x80000011`

Error while creating or initializing NexPlayer. The current app id is not activated

### `PLAYER_ERROR_TIME_LOCKED` 
`0x80000012`

SDK has expired

