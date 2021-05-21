# Conviva Integration with NexPlayer™ SDK for Android

## Legal Notices

**Disclaimer for Intellectual Property**

This product is designed for general purpose, and accordingly the customer is responsible for all or any of
intellectual property licenses required for actual application. NexStreaming Corp. does not provide any indem-
nification for any intellectual properties owned by third party.

**Copyright**

Copyright for all documents, drawings and programs related with this specification are owned by NexStreaming
Corp. All or any part of the specification shall not be reproduced nor distributed without prior written approval
by NexStreaming Corp. Content and configuration of all or any part of the specification shall not be modified
nor distributed without prior written approval by NexStreaming Corp.

© Copyright 2010-2019 NexStreaming Corp. All rights reserved.

## Using the Conviva Client Module

From version 6.10 of the NexPlayer™ SDK, a new module has been added to make it easier to integrate Conviva
into applications with NexPlayer™.
For more information on how to use the NexPlayer™ SDK with Conviva, please see: NexConvivaClient.


## Class Documentation

### NexConvivaClient Class Reference

**Classes**

- `enum CONVIVA_PROPERTY`

	This enumeration includes the properties that must be set to integrate the Conviva client 	module into NexPlayer™.

**Static Public Attributes**

- `static final int ERR_FATAL = StreamerError.SEVERITY_FATAL`
- `static final int WARNING = StreamerError.SEVERITY_WARNING`

**Protected Member Functions**

- `void onError (NexErrorCode errorcode)`
- `void openSession (Context context, NexPlayer player, String path)`
- `void startSession ()`
- `void closeSession ()`
- `void releaseSession ()`
- `void pauseSession ()`
- `void resumeSession ()`
- `void stopSession ()`

**Detailed Description**

This enumeration includes the properties that must be set to integrate the Conviva client module into NexPlayer™.

The values of the different properties can be set by calling the setProperty method of the relevant client class.

**Parameters**

| Parameter             | Description                                             |
|--------------------------------|-------------------------------------------------------------------------------------------|
| STR\_CUSTOMER_KEY               | The customer key or operator ID needed to set up a client module session, as a *String*.                                             |
| STR\_VIEWER_ID             | The individual viewer’s ID, as a *String*. |
| STR\_CDN_NAME | The name of the Content Delivery Network, as a *String*. Please see the official client documentation for possible values.                                |
| STR\_PLAYER_NAME                    | The name of the Player application that is based on the NexPlayerTM SDK, as a *String*.                                                           |
| STR\_ASSET_NAME      | The name of the video asset, as a *String*.                                                 |
| BOOL\_IS_LIVE          | The content’s type as a *boolean*. *TRUE* if the content is LIVE.                                                   |


#### Example Code

```java
public void onCreate(Bundle icicle) {
		...
		createAndSetNexPlayer(); // Create and set NexPlayer SDK.
		
		// Create Conviva Client module.
		NexConvivaClient mConvivaClient = new NexConvivaClient();
		
		// Set Conviva Client Properties.
		mConvivaClient.setProperty(CONVIVA_PROPERTY.STR_CDN_NAME, ConvivaContentInfo.CDN_NAME_OTHER);
		
		mConvivaClient.setProperty(CONVIVA_PROPERTY.STR_CUSTOMER_KEY, "XXXXXXXXXXXXX");
		
		mConvivaClient.setProperty(CONVIVA_PROPERTY.STR_PLAYER_NAME, "NexPlayerSample");
		
		mConvivaClient.setProperty(CONVIVA_PROPERTY.STR_VIEWER_ID, "Test Viewer");
		mConvivaClient.setProperty(CONVIVA_PROPERTY.STR_ASSET_NAME, "VideoTitle");
		
		// Add ConvivaClient to NexPlayer
		mNexPlayer.addNexClient(mConvivaClient);
		
		// Start Play
		startPlay();
		...
}

```	
**See Also**

- NexPlayer.addNexClient in the NexPlayer™ SDK
- NexPlayer.removeNexClient in the NexPlayer™ SDK
- NexPlayer.getClientStatus in the NexPlayer™ SDK

#### NexConvivaClient()

This initializes the NexConvivaClient module.


#### boolean adEnd()

This method is called to notify the Conviva client module of the end of an advertisement.

**Returns**

*TRUE* if successful, *FALSE* in the event of failure. If no Conviva client module is available, *FALSE* will be returned.

> **Warning** Do not call this method when playing local content. It should only be used for streaming content.

#### boolean adStart()

This method is called to notify the Conviva client module of the beginning of an advertisement.

**Returns**

*TRUE* if successful, *FALSE* in the event of failure. If no Conviva client module is available, *FALSE* will be returned.

> **Warning** Do not call this method when playing local content. It should only be used for streaming content.

#### Object getProperty (CONVIVA_PROPERTY key)

This method gets the value of any property of the Conviva client module.

**Parameters**

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                |
|-----------|----------------------------------------|
| key       | The Conviva module property to get. This will be one of:  *NexClient.CONVIVA\_PROPERTY.PREF\_STR\_CDN_NAME*    
*NexClient.CONVIVA\_PROPERTY.PREF\_STR\_CUSTOMER_KEY*  
*NexClient.CONVIVA\_PROPERTY.PREF\_STR\_PLAYER_NAME* 
*NexClient.CONVIVA\_PROPERTY.PREF\_STR\_USER_ID*  *NexClient.CONVIVA\_PROPERTY.PREF\_STR\_ASSET_NAME*|

**Returns**

The requested Conviva client property.

**See Also**

- NexConvivaClient.setProperty
- NexClient.CONVIVA_PROPERTY
- NexConvivaClient

#### boolean pauseMonitor()

This method pauses monitoring by the current Conviva client module.

**Returns**

*TRUE* if successful, *FALSE* in the event of failure. If no Conviva client module is available, *FALSE* will be
returned.

> **Warning** Do not call this method when playing local content. It should only be used for streaming content.

#### void reportError (String desc, int priority)

This method returns priority values to report errors within the application including Conviva.

This method should be called after NexConvivaClient is initialized.

When an error occurs, the application calls *reportError* with the parameter *priority* set to either *NexConvivaClient.ERR_FATAL* or *NexConvivaClient.WARNING*.

If the *priority* parameter is *NexConvivaClient.ERR_FATAL*, NexConvivaClient will clean up the current session. When the value of *priority* is *NexConvivaClient.WARNING*, NexConvivaClient will only deliver a warning to Conviva and continue with the current session.

**Parameters**

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| desc       | Returns a detailed description of the error as a String.|
| key       | The value to set. This will be one of:<br>  *NexConvivaClient.ERR\_FATAL* <br>    *NexConvivaClient.WARNING*|
</br>


#### boolean resumeMonitor()

This method resumes monitoring by the current Conviva client module.

**Returns**

*TRUE* if successful, *FALSE* in the event of failure. If no Conviva client module is available, *FALSE* will be
returned.

> **Warning** Do not call this method when playing local content. It should only be used for streaming content.

#### void sendSessionEvent (String name, Map<String, Object> eventAttr)

This method sends the session events related to the Conviva client module sessions in NexPlayer™.

**Parameters**

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| name  | The name of the event, as a *String*.
| eventAttr         | The event attributes, as a Map of Strings and Objects.|

#### void setCustomTags (Map<String, String> map)

This method allows customized tags to be used with the Conviva client module.

For more information on how custom tags can be used with Conviva, please refer to the official Conviva documentation at <http://developer.conviva.com/integration/tags>.

**Parameters**

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| map  | The customized tags to be added and their values as a Map of Strings.|

#### void setProperty (CONVIVA_PROPERTY key, String value)

This method sets the value of any property for the Conviva client module in NexPlayer™.

**Parameters**

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| key  | The property to set. For possible properties please see the enumeration, CONVIVA_PROPERTY, in the NexClient class and the details class description of NexConvivaClient.
| value         | The value to set as a *String*.|

**See Also**

- NexClient.CONVIVA_PROPERTY
- NexConvivaClient

#### void setProperty (CLIENT_PROPERTY key, boolean value)

This method sets the value of any property for the Conviva client module in NexPlayer™.

**Parameters**

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| key  | The property to set. For possible properties please see the enumeration, CONVIVA_PROPERTY, in the NexClient class and the details class description of NexConvivaClient.
| value         | The value to set as a *boolean*.|

**See Also**

- NexClient.CONVIVA_PROPERTY
- NexConvivaClient

#### void toggleTrace (boolean enable)

This method enables or disables debugging log generated for the Conviva library.

Debug logs are disabled by default.

**Parameters**

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| enable  | Whether or not to enable the Conviva logs. Pass *TRUE* to enable or *FALSE* to disable them.|
