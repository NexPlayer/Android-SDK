# WV DRM Integration with NexPlayerSDK for Android

Widevine DRM (as known as WV DRM) is a DRM technique compatible with MediaDrm, made by Google. MediaDrm is supported from Android JellyBean 4.3 and up, and it supports DASH only. To use the same technique on lower version of Android devices such as Ice Cream Sandwich, or apply to HLS, use this DRM module. The Widevine
DRM module of the NexPlayer SDK uses the common encryption (cenc) algorithm to receive the encrypted media
file from the media server and to receive and decrypt the decryptable key from the Widevine server. Therefore, you
have to enter the URL where you can get the content and key to the NexPlayer SDK. In addition, for the offline store
function provided by NexPlayer SDK, Widevine DRM authentication information and the path and mode for storing
and reading contents should be input. This document describes the APIs that can control it.

## Components

1. NexWVDRM.java
	- Provides API to specify information for playing Widevine DRM contents by SW decryption module.
	
		```java
		NexWVDRM nexWVDRM = new NexWVDRM();
		```
	
	- Provides API for selecting the offline playback mode.
		- If you don’t use offline playback mode.
		
			```java
			offlineMode = 0;
			nexWVDRM.initDRMManager(EnginePath, CertificatePath, KeyServerURL, offlineMode)
			```
		- If you use offline store mode.
	
			```java
			offlineMode = 1;
			nexWVDRM.initDRMManager(EnginePath, CertificatePath, KeyServerURL, offlineMode)
			```
		
		- If you use retrieve playback mode.
	
			```java
			offlineMode = 2;
			nexWVDRM.initDRMManager(EnginePath, CertificatePath, KeyServerURL, offlineMode)
			```
		
		- If you use offline store and retrieve mode.
	
			```java
			offlineMode = 3;
			nexWVDRM.initDRMManager(EnginePath, CertificatePath, KeyServerURL, offlineMode)
			```
		
		- This API should only be used before the NexWVDRM.initDRMManager function call.
		
	- Provides an API that specifies event listener to provide license request data.
		- If you want to get license data instead of NexPlayer. Use below code
		
			```java
			INexDRMLicenseListener licenseRequestListener = new INexDRMLicenseListener() {
					@Override
					public byte[] onLicenseRequest(byte[] requestData) {
						final String LicenseServer = mCurrentExtraData;
						Object response = null;
						try {
							response = NexHTTPUtil.executePost(LicenseServer, requestData, null);
						} catch (IOException e) {
						
						}
						return (byte[]) response;
					}
			};
			nexWVDRM.setLicenseRequestListener(licenseRequestListener);
			```
			
		- This API should only be used before the NexWVDRM.initDRMManager function call.

	- Provides an API that specifies an event listener for when the key is modified.
		- You can insert and register code that can modify the key as shown below.
		
			```java
			NexWVDRM.IWVDrmListener listener = new NexWVDRM.IWVDrmListener() {
					@Override
					public String onModifyKeyAttribute(String strKeyAttr) {
						String strAttr = strKeyAttr;
						String strRet = strKeyAttr;
						//modify here;
						List<String> keyAttrArray = new ArrayList<String>();
						String strKeyElem = "";
						String strKeyRemain = "";
						int end = 0;
						while (true) {
							end = strAttr.indexOf("\n");
							if (end != -1 && end != 0) {
								strKeyElem = strAttr.substring(0, end);
								keyAttrArray.add(strKeyElem);
								strKeyRemain = strAttr.substring(end, strAttr.length());
								strAttr = strKeyRemain;
							} else if ((end == -1 || end == 0) && strKeyElem.isEmpty() == false) {
								keyAttrArray.add(strAttr.substring(0, strAttr.length()));
								break;
							} else {
								keyAttrArray.add(strAttr);
								break;
							}
						}
						for (int i = 0; i < keyAttrArray.size(); i++) {
							strKeyElem = keyAttrArray.get(i);
							if (strKeyElem.indexOf("com.widevine") != -1) {
								Log.d(LOG_TAG, "Found Key!");
								strRet = strKeyElem;
								break;
							}
						}
						return strRet;
					}
			};
			nexWVDRM.setListener(listener);
			```
			
		- This API should only be used after a successful NexWVDRM.initDRMManager function call.

	- Provides API to specify HTTP optional header
		- API name is setNexWVDrmOptionalHeaderFields. This is an API that adds an HTTP header to attach when requesting key to Widevine license server.
		
			```java
			HashMap<String, String> optionalHeaders = new HashMap<>();
			Intent intent = getIntent();
			ArrayList<String> optionalHeadersList = intent.getStringArrayListExtra("WVDRMOptionalHeaders");
			if (optionalHeadersList != null ){
				for (String optionalHeader : optionalHeadersList) {
					String[] item = optionalHeader.split(":");
					optionalHeaders.put(item[0], item[1]);
				}
				if (optionalHeaders != null) {
					nexWVDRM.setNexWVDrmOptionalHeaderFields(optionalHeaders);
				}
			}
			```
			
		- This API should only be used before the NexWVDRM.initDRMManager function call.
		
	- To play DRM contents using NexWVDRM, you have to implement the following.
		- After creating the NexWVDRM object described above, specify the required information and call nexWVDRM.initDRMManager.
		
			```java
			nexWVDRM.initDRMManager(EnginePath, CertificatePath, keyServer, offlineMode);
			```
			
		- Specify the SW decryption module forNexPlayeras follows. 2 means to use SW decryption module
		
			```java
			mNexPlayer.setProperties(NEXPLAYER_PROPERTY_ENABLE_MEDIA_DRM, 2);
			```
		- Open the NexPlayer
		
			```java
			mNexPlayer.open()
			```

2. If you want to play using the HW decryption module, you can do as follows.

	- Enter the DRM key server URL using NexPlayer.setNexMediaDrmKeyServerUri

		```java
		mNexPlayer.setNexMediaDrmKeyServerUri(keyServer);
		```

	- Enter the HTTP optional header using NexPlayer.setNexMediaDrmOptionalHeaderFields
	
		```java
		HashMap<String, String> optionalHeaders = new HashMap<>();
		Intent intent = getIntent();
		ArrayList<String> optionalHeadersList = intent.getStringArrayListExtra("WVDRMOptionalHeaders");
		if (optionalHeadersList != null ){
			for (String optionalHeader : optionalHeadersList) {
				String[] item = optionalHeader.split(":");
				optionalHeaders.put(item[0], item[1]);
			}
			if (optionalHeaders != null) {
				mNexPlayer.setNexMediaDrmOptionalHeaderFields(optionalHeaders);
			}
		}

		```

	- You can insert and register code that can modify the key as shown below.
	
		```java
		NexWVDRM.IWVDrmListener listener = new NexWVDRM.IWVDrmListener() {
			@Override
			public String onModifyKeyAttribute(String strKeyAttr) {
				String strAttr = strKeyAttr;
				String strRet = strKeyAttr;
				//modify here;
				List<String> keyAttrArray = new ArrayList<String>();
				String strKeyElem = "";
				String strKeyRemain = "";
				int end = 0;
				while (true) {
					end = strAttr.indexOf("\n");
					if (end != -1 && end != 0) {
						strKeyElem = strAttr.substring(0, end);
						keyAttrArray.add(strKeyElem);
						strKeyRemain = strAttr.substring(end, strAttr.length());
						strAttr = strKeyRemain;
					} else if ((end == -1 || end == 0) && strKeyElem.isEmpty() == false) {
						keyAttrArray.add(strAttr.substring(0, strAttr.length()));
						break;
					} else {
						keyAttrArray.add(strAttr);
						break;
					}
				}
				for (int i = 0; i < keyAttrArray.size(); i++) {
					strKeyElem = keyAttrArray.get(i);
					if (strKeyElem.indexOf("com.widevine") != -1) {
						Log.d(LOG_TAG, "Found Key!");
						strRet = strKeyElem;
						break;
					}
				}
				return strRet;
			}
		};
		mNexPlayer.setLicenseRequestListener(listener);
		```
	
	- Specify the HW decryption module for NexPlayer as follows. 1 means to use HW decryption module

		```java
		mNexPlayer.setProperties(NEXPLAYER_PROPERTY_ENABLE_MEDIA_DRM, 1);
		```
		
	- Open the NexPlayer

		```java
		mNexPlayer.open()
		```

3. libnexwvdrm.so

	- This binary file contains WV DRM module, so it MUST be in the libs folder.
	- Software module that decrypts through the information specified through the NexWVDRM class in NexWVDRM.java.


(a) This binary file contains WV DRM module, so it MUST be in thelibsfolder.
(b) Software module that decrypts through the information specified through the NexWVDRM class in Nex-
WVDRM.java.

**See Also**


section `Storing Streaming Content for Offline Playback` in the default edition.


## Class Documentation

### NexWVDRM.IWVDrmListener Interface Reference

####  String onModifyKeyAttribute ( String strKeyAttr )

This method provides the key attribute that will be used by NexWVDRM when the key attribute is modified.

By overriding this function, you can modify the # EXT-X-KEY tag data in the HLS Playlist. The corresponding data
is passed as a string to the strKeyAttr parameter. You can refer to the example code setListener.

**Parameters**

| Name                   | Description                                                                                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| strKeyAttr | strKeyAttr is the key attribute(#EXT-X-KEY) that is written in the HLS playlist file. |

**Returns**

A string with modified key attribute. NexWVDRM will send this \c string without any modification. If modification is not needed, then the UI should return the input parameter: strKeyAttr.

### NexWVDRM Class Reference

This class allows NexPlayer™ to handle and descramble Widevine HLS content.

NexWVDRM provides an API for assigning information to NexPlayer to play Widevine DRM applied content.
Widevine DRM applied content must receive the key required for descrambling from the specified license server. The license server sends the key only to the authenticated user. So NexPlayer must know the information that can be authenticated from the license server and the URL of the license server. NexPlayer also offers offline playback for Widevine content. To do this, select On (store / retrieve / store & retrieve) / OFF. NexWVDRM provides an API to specify such information and applies the specified information to Widevine module so that Widevine DRM contents can be played back stably.

**Classes**

- `interface IWVDrmListener`
    
    The application must implement this interface in order to receive events from NexWVDrm.

**Protected Attributes**

- `IWVDrmListener m_listener`


#### int initDRMManager ( String strEnginePath, String strFilePath, String   strKeyServerURL, int offlineMode )

This method initializes the minimum necessary information for playing Widevine DRM contents and registers it in Widevine DRM module.

When this API was called service certification will be retrieved automatically internally. This method registers the
function pointer of the NexPlayer SDK Engine as a callback function of the Widevine DRM module and requests
and receives the authentication information to the license server to descramble the content. And, this information
immediately uses or store to the specified path by offline mode

**Parameters**

| Name                   | Description                                                                                                                                                                                          |
|------------------------|-------------------------------------------------------------------------------------------|
| strEngineLibName | The relevant engine library name as a string. Register for communication between NexPlayer SDK Engine and Widevine DRM module. |
| strFilePath | This is the path to store the key and authentication information received from the License server when Store / Retrieve play is performed. In the Offline state, it can not connect to the License Server and stores the received authentication information to a file. This information should be used only Widevine DRM module of the certified player inside because it is encrypted. |
| strKeyServerURL | This is a license server URL that can receive information for descrambling WidevineDRM contens |
| offlineMode | Select the offline playback mode to use. 0: On-line mode. NexPlayer will open a temporary DRM session, which does not store any session handles. Network connection is required. 1: Storing mode. NexPlayer will open a permanent DRM session, and store it after opening it. Network connection is required. 2: Retrieving mode. NexPlayer will find a stored DRM session, and then restore it. 3: Storing + Retrieving mode. NexPlayer will find a stored DRM session. If it exists, then NexPlayer will restore it; if not, the engine will create a new session and then store it. Network connection is required. |

```java
NexWVDRM nexWVDRM = new NexWVDRM();
String strEngineLibName = Context.getApplicationInfo().dataDir + "/lib/libnexplayerengine.so";
String strFilePath = Context.getFilesDir().getAbsolutePath() + "/wvcert";
String strKeyServerURL = "http://wv-ref-eme-player.appspot.com/proxy";
int offlineMode = 0;
nexWVDRM.initDRMManager(strEngineLibName, strFilePath, strKeyServerURL, offlineMode);
```

#### int initDRMManagerMulti ( Object nexplayerInstance, String strEnginePath, String strFilePath, String strKeyServerURL, int offlineMode)

The minimum necessary information for playing a plurality of Widevine DRM contents is initialized and registered in
the Widevine DRM module.

When this API was called service certification will be retrieved automatically internally. This method is for using multi
instances For multiple instances, the function pointer of NexPlayer SDK Engine is registered as a callback function
of Widevine DRM module, and authentication information is requested and received from the license server for
descrambling of contents. And, this information immediately uses or store to the specified path by offline mode

**Parameters**

| Name                   | Description                                                                                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| nexplayerInstance | Update the callbacks registered in the previously created NexPlayer SDK Engine. |
| strEngineLibName | The relevant engine library name as a string. Register for communication between NexPlayer SDK Engine and Widevine DRM module. |
| strFilePath | This is the path to store the key and authentication information received from the License server when Store / Retrieve play is performed. In the Offline state, it can not connect to the License Server and stores the received authentication information to a file. This informa- tion should be used only Widevine DRM module of the certified player inside because it is encrypted. |
| strKeyServerURL | This is a license server URL that can receive information for descrambling Widevine DRM contents. |
| offlineMode                   | Select the offline playback mode to use. 0: On-line mode. NexPlayer will open a temporary DRM session, which does not store any session handles. Network connection is required. 1: Storing mode. NexPlayer will open a permanent DRM session, and store it after opening it. Network connection is required. 2: Retrieving mode. NexPlayer will find a stored DRM session, and then restore it. 3: Storing + Retrieving mode. NexPlayer will find a stored DRM session. If it exists, then NexPlayer will restore it; if not, the engine will create a new session and then store it. Network connection is required.                                                                                                                                                                                          |

```java
NexPlayer mNexPlayer = new NexPlayer();
NexWVDRM nexWVDRM = new NexWVDRM();
String strEngineLibName = Context.getApplicationInfo().dataDir + "/lib/libnexplayerengine.so";
String strFilePath = Context.getFilesDir().getAbsolutePath() + "/wvcert";
String strKeyServerURL = "http://wv-ref-eme-player.appspot.com/proxy";
int offlineMode = 0;

nexWVDRM.initDRMManagerMulti(mNexPlayer, strEngineLibName, strFilePath, strKeyServerURL, offlineMode);
```


#### void setLicenseRequestListener ( INexDRMLicenseListener listener )

When sending http request messages or receiving http response messages to the license server (key server URL) specified through the NexWVDRM.initDRMManager / NexWVDRM.initDRMManagerMulti function, register a
callback function to control this from outside the NexPlayer SDK.

**Parameters**

| Name                   | Description                                                                                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| listener | INexDRMLicenseListener: the object on which methods will be called when new events occur. This must implement the INexDRMLicenseListenerinterface. |

```java
INexDRMLicenseListener licenseRequestListener = new INexDRMLicenseListener() {
	@Override
	public byte[] onLicenseRequest(byte[] requestData) {
		final String LicenseServer = mCurrentExtraData;
		Log.d(LOG_TAG, "onLicenseRequest data length : " + requestData.length);
		Object response = null;
		try {
			response = NexHTTPUtil.executePost(LicenseServer, requestData, null);
			Log.d(LOG_TAG, "[getLicense ] license resonse: length:" + ((byte[])response).length);
		} catch (IOException e) {
		
		}
		return (byte[]) response;
	}
};
nexWVDRM.setLicenseRequestListener(licenseRequestListener);
```

#### void setLicenseRequestTimeout ( int timeout )

Sets a specified timeout value for conntection and waiting for a server response, in milliseconds.

**Parameters**

| Name                   | Description                                                                                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| timeout | an int that specifies the timeout value in milliseconds |

#### void setListener ( IWVDrmListener listener )

Registers a callback that will be invoked when new events occur.

Create and register a listener using NexWVDRM.IWVDrmListener. NexWVDRM.IWVDrmListener currently has an onModifyKeyAttribute, which can be overridden to receive and modify HLS # EXT-X-KEY tag data.

**Parameters**

| Name                   | Description                                                                                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| listener | IWVDrmListener: the object on which methods will be called when new events occur. This must implement the IWVDrmListener interface. |

```java
NexWVDRM.IWVDrmListener wvDrmListener = new NexWVDRM.IWVDrmListener() {
	@Override
	public String onModifyKeyAttribute(String strKeyAttr) {
		String strAttr = strKeyAttr;
		String strRet = strKeyAttr;
		List<String> keyAttrArray = new ArrayList<String>();
		String strKeyElem = "";
		String strKeyRemain = "";
		int end = 0;
		while (true) {
			end = strAttr.indexOf("\n");
			if (end != -1 && end != 0) {
				strKeyElem = strAttr.substring(0, end);
				keyAttrArray.add(strKeyElem);
				strKeyRemain = strAttr.substring(end, strAttr.length());
				strAttr = strKeyRemain;
			}
			else if ((end == -1 || end == 0) && strKeyElem.isEmpty() == false) {
				keyAttrArray.add(strAttr.substring(0, strAttr.length()));
				break;
			}
			else {
				keyAttrArray.add(strAttr);
				break;
			}
		}
		for (int i = 0; i < keyAttrArray.size(); i++) {
			strKeyElem = keyAttrArray.get(i);
			if (strKeyElem.indexOf("com.widevine") != -1) {
				// Found Key
				strRet = strKeyElem;
				break;
			}
		}
		return strRet;
	}
};
nexWVDRM.setListener(wvDrmListener);
```

#### void setNexWVDrmOptionalHeaderFields ( HashMap<String, String> optionalHeaderFields)

This method sets optionalParameters when sending requests to the Key Server of NexWVDRM.

Specify the header field and value to be added when sending an http request message to the license server (key server URL) specified when the NexWVDRM.initDRMManager / NexWVDRM.initDRMManagerMulti function is called. The license server can use this header and value to determine whether the user is authenticated. To add an
optional header, you must call it before calling the NexWVDRM.initDRMManager / NexWVDRM.initDRMManagerMulti function.

**Parameters**

| Name                   | Description                                                                                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| optionalHeaderFields |  HashMap is included in the key request message to allow a client application to provide additional message parameters to the server. |

```java
HashMap<String, String> optionalHeaders = new HashMap<>();
String key1 = "test_header1";
String value1 = "test_value1";
String key2 = "test_header2";
String value2 = "test_value2";

optionalHeaders.put(key1, value1);
optionalHeaders.put(key2, value2);

nexWVDRM.setNexWVDrmOptionalHeaderFields(optionalHeaders);
```
