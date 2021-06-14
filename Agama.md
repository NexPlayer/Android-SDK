# Agama Integration with NexPlayer SDK for Android

### Legal Notices

**Disclaimer for Intellectual Property**

This product is designed for general purpose, and accordingly the customer is responsible for all or any of
intellectual property licenses required for actual application. NexStreaming. does not provide any indemnification for any intellectual properties owned by third party.

**Copyright**

Copyright for all documents, drawings and programs related with this specification are owned by NexStreaming. All or any part of the specification shall not be reproduced nor distributed without prior written approval
by NexStreaming. Content and configuration of all or any part of the specification shall not be modified
nor distributed without prior written approval by NexStreaming.

### Using the Agama Client Module

From version 6.10 of the NexPlayer SDK, a new module has been added to make it easier to integrate Agama
into applications with NexPlayer.
For more information on how to use the NexPlayer SDK with Agama, please see: NexAgamaClient.

## Class Documentation

### NexAgamaClient Class Reference

**Classes**

- `enum AGAMA_PROPERTY`

	This enumeration includes the properties that must be set to integrate Agama client module into NexPlayer.

**Static Public Member Functions**

- `static com.nexstreaming.nexplayerengine.NexAgamaClient getAgamaInstance ()`

**Public Attributes**

- `Boolean background = false`

**Static Public Attributes**

- `static final int EX_CONTENT_TITLE = 0`
- `static final int EX_CONTENT_DESCRIPTION = 1`
- `static final int EX_GENERIC_DESCRIPTION = 2`
- `static final int EX_SPECIFIED_DURATION = 3`
- `static final int EX_PLAYLIST_TYPE = 4`
- `static final int EX_CHANNEL_NAME = 5`
- `static final int EX_SERVICE_NAME = 6`
- `static final int EX_CONTENT_TYPE = 7`
- `static final int NOTIFY_CHANNEL_CHANGE = 0`
- `static final int NOTIFY_BACKGROUND = 1`
- `static final int NOTIFY_FOREGROUND = 2`
- `static final int NOTIFY_USER_LOGIN = 3`
- `static final int NOTIFY_USER_LOGOUT = 4`
- `static final int NOTIFY_NO_ACCESS = 5`
- `static final int PLAYLIST_TYPE_VOD = 0`
- `static final int PLAYLIST_TYPE_LIVE = 1`

**Protected Member Functions**

- `void openSession (Context context, NexPlayer player, String path)`
- `void startSession ()`
- `void stopSession ()`
- `void closeSession ()`
- `void releaseSession ()`
- `void pauseSession ()`
- `void resumeSession ()`
- `void seek (int msec)`
- `void onError (NexErrorCode errorcode)`
- `void onTime (int mSec)`
- `void onBuffering (int arg1)`
- `void onBufferingBegin ()`
- `void onBufferingEnd ()`
- `void onEndOfContent ()`
- `void onHttpRequest (NexPlayer mp, String msg)`
- `void onStateChanged (NexPlayer mp, int arg1, int arg2)`
- `void onAsyncCmdComplete (NexPlayer mp, int command, int result, int param1, int param2)`
- `void addEventReceiver ()`

**Detailed Description**

This enumeration includes the properties that must be set to integrate Agama client module into NexPlayer.

The values of the different properties can be set by calling the setProperty method of the relevant client class.

**Parameters**

| Parameter             | Description                                             |
|--------------------------------|-------------------------------------------------------------------------------------------|
| STR\_SERVER_IP                | The address of the client server as a *String*.                                             |
| STR\_CUSTOMER_KEY             | The customer key or operator ID needed to set up the client module session, as a  *String*. |
| STR\_CONFIGURATION\_SET_FROM | How the Agama EMP configuration is transferred to the STB.                                |
| INT\_PORT_NO                    | The port number, as an *integer*.                                                           |
| INT\_ID\_REPORT_INTERVAL       | The interval of ID report, as an *integer*.                                                 |
| INT\_REPORT_INTERVAL          | The interval of report, as an *integer*.                                                    |
| LONG\_APP\_STARTUP_TIME        | The startup time of the application.                                                      |

#### Example Code

**Main Activity**


```java
protected void onCreate(Bundle savedInstanceState) 
{
	...
	mAgamaClient = NexAgamaClient.getAgamaInstance();
	mAgamaClient.setProperty(AGAMA_PROPERTY.STR_SERVER_IP, "192.168.0.1");
	mAgamaClient.setProperty(AGAMA_PROPERTY.STR_CUSTOMER_KEY, "fooSoo");
	mAgamaClient.setProperty(AGAMA_PROPERTY.STR_CONFIGURATION_SET_FROM, "build in");
	mAgamaClient.setProperty(AGAMA_PROPERTY.INT_PORT_NO, 8050);
	mAgamaClient.setProperty(AGAMA_PROPERTY.INT_ID_REPORT_INTERVAL, 120);
	mAgamaClient.setProperty(AGAMA_PROPERTY.INT_REPORT_INTERVAL, 60);
	mAgamaClient.setProperty(AGAMA_PROPERTY.LONG_APP_STARTUP_TIME, 300);
	mAgamaClient.init(this);	
	...
}
```

**Player Activity**

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
	...
	mAgamaClient = NexAgamaClient.getAgamaInstance();
	
	if( mAgamaClient.isInitialized() == true ) {
		...
	
		mAgamaClient.setExternalParams( NexAgamaClient.EX_CHANNEL_NAME, ChannelName);
		mAgamaClient.setExternalParams( NexAgamaClient.EX_GENERIC_DESCRIPTION, Channeldesc);
		mAgamaClient.setExternalParams( NexAgamaClient.EX_CONTENT_TITLE, ContentTitle);
		mAgamaClient.setExternalParams( NexAgamaClient.EX_CONTENT_DESCRIPTION, ContentDesc);
		mAgamaClient.setExternalParams( NexAgamaClient.EX_PLAYLIST_TYPE, NexAgamaClient.PLAYLIST_TYPE_VOD);
		mAgamaClient.setExternalParams( NexAgamaClient.EX_SPECIFIED_DURATION, Duration)
		
		int ret = mNexPlayer.open(url, null, null,
		NexPlayer.NEXPLAYER_SOURCE_TYPE_STREAMING, NexPlayer.NEXPLAYER_TRANSPORT_TYPE_TCP);
		
		...
	}
	...
}
```

**See Also**


- NexPlayer.addNexClient in the NexPlayer SDK

- NexPlayer.removeNexClient in the NexPlayer SDK

- NexPlayer.getClientStatus in the NexPlayer SDK

#### Object getProperty (com.nexstreaming.nexplayerengine.NexAgamaClient.AGAMA_PROPERTY key)

This method gets the value of any property of the Agama client module.

**Parameters**

<table>
	<tr>
  <th>Parameter</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="7">Key</th>
</tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_PORT_NO</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_REPORT_INTERVAL</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_ID_REPORT_INTERVAL</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.STR_SERVER_IP</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.STR_CUSTOMER_KEY</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.STR_CONFIGURATION_SET_FROM</td></tr>
</table>
						

**Returns**

The Agama client property requested.

#### boolean init (Activity activity)

This initializes the Agama client module.

**Parameters**

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| activity  | The first activity to start when the application is opened for the first time. |

#### boolean isInitialized ()

Determines if Agama client module is currently initialized.

If this method returns *true*, Agama client module has successfully initialized.

#### void notify (int event)

This method is called to notify the Agama client module of any event that occurs within the application.

**Parameters**

<table>
	<tr>
  <th>Parameter</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="7">Key</th>
</tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.NOTIFY_CHANNEL_CHANGE</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.NOTIFY_BACKGROUND</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.NOTIFY_FOREGROUND</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.NOTIFY_USER_LOGOUT</td></tr>
</table>

#### void notify (int event, String param)

This method is called to notify the Agama client module of any event that occurs within the application.

**Parameters**

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| event  | *NexAgamaClient.AGAMA\_PROPERTY.NOTIFY\_CHANNEL_CHANGE*|
| param         | The current user ID as a string.                                                                              |

#### void release ()

This method releases resources associated with the Agama client Module.

This method should be called before exiting the application.

#### void setExternalParams (int key, String value)

This method sets the value of any *string* external parameter for the Agama client module in NexPlayer.

**Parameters**

<table>
<tr>
  <th>Parameter</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="5">Key</th>
</tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.EX_CONTENT_TITLE - Content title</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.EX_CONTENT_DESCRIPTION - Content description</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.EX_GENERIC_DESCRIPTION - A generic description of the state. Can be any relevant information related with the state</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.EX_CHANNEL_NAME - Channel name</td></tr>
	
<tr>
  <th>value</th>
  <td>The string value to set for the external parameters</td>
</tr> 
</table>

#### void setExternalParams (int key, int value)

This method sets the value of any *integer* external parameter for the Agama client module in NexPlayer.

<table>
<tr>
  <th>Parameter</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="3">Key</th>
</tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.EX_SPECIFIED_DURATION - Duration of the content in seconds</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.EX_PLAYLIST_TYPE - The type of the current content</td></tr>
	
<tr>
  <th>value</th>
  <td>The int value to set for the external parameters</td>
</tr> 
</table>

#### void setProperty (com.nexstreaming.nexplayerengine.NexAgamaClient.AGAMA_PROPERTY key,int value) throws IllegalArgumentException

This method sets the value of any *integer* property for the Agama client module in NexPlayer.

**Parameters**

<table>
<tr>
  <th>Parameter</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="5">Key</th>
</tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_PORT_NO</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_REPORT_INTERVAL</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_ID_REPORT_INTERVAL</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.LONG_APP_STARTUP_TIME</td></tr>
	
<tr>
  <th>value</th>
  <td>The integer value to set or the Agama client property</td>
</tr> 
</table>

#### void setProperty (com.nexstreaming.nexplayerengine.NexAgamaClient.AGAMA_PROPERTY key,String value) throws IllegalArgumentException

This method sets the value of any *integer* property for the Agama client module in NexPlayer.

**Parameters**

<table>
<tr>
  <th>Parameter</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="5">Key</th>
</tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_PORT_NO</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_REPORT_INTERVAL</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.INT_ID_REPORT_INTERVAL</td></tr>
  <tr><td>NexAgamaClient.AGAMA_PROPERTY.LONG_APP_STARTUP_TIME</td></tr>
	
<tr>
  <th>value</th>
  <td>The string value to set or the Agama client property</td>
</tr> 
</table>

#### void setProperty (com.nexstreaming.nexplayerengine.NexAgamaClient.AGAMA_PROPERTY key,long value) throws IllegalArgumentException

This method sets the value of any *long* property for the Agama client module in NexPlayer.

**Parameters**

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| key  | *NexAgamaClient.AGAMA\_PROPERTY.LONG\_APP\_STARTUP_TIME*
| value         | The *long* value to set for the external parameters.|
