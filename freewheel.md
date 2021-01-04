# Freewheel Integration with NexPlayer SDK for Android

## Using the FreeWheel Client Module

From version 6.15 of the NexPlayer™ SDK, a new module has been added to make it easier to integrate FreeWheel into applications with NexPlayer™.

For more information on how to use the NexPlayer™ SDK with FreeWheel, please see: `NexFreeWheelClient` 

This documentation is a work in progress.

## Class Documentation

### NexFreeWheelClient Class Reference

This class allows the FreeWheel client module to be easily integrated into the NexPlayer™ SDK.

In order to integrate the FreeWheel client module, please do the following:

- Create the `NexFreeWheel` client by calling:

 ```java
NexFreeWheelClient mFreeWheelClient = new NexFreeWheelClient();
```

- Add the FreeWheel client module to NexPlayer™ by calling:

 ```java
mNexPlayer.addNexClient(mFreeWheelClient);
```

For additional guidance, please see the example code that follows.

**Example Code**

```java
public void onCreate(Bundle icicle) {
	// Create and set NexPlayer SDK.
	createAndSetNexPlayer(); 

	// Create FreeWheel client module:
	FreeWheelClient mFreeWheelClient = new NexFreeWheelClient();

	// Add the FreeWheel client module to NexPlayer:
	mNexPlayer.addNexClient(mFreeWheelClient);
	// Start Play
	startPlay();
}

@Override
public void onTimedMetaRenderRender(NexPlayer mp, final NexID3TagInformation TimedMeta) {
	mHandler.post(new Runnable() {
		public void run() {
			mFreewheelClient.handleMetaData ( "TIT2", extractedMetaData, currentTime );
		}
	}
}
```

**See Also**

- NexPlayer.addNexClient
- NexPlayer.removeNexClient
- NexPlayer.getClientStatus


#### NexFreeWheelClient(Activity activity,Context context,String contentsURL)

Constructs a new Stream Stitcher Helper instance for the FreeWheel service.

**Parameters**

| Name  | Description  | 
|---|---|
|activity| Current activity, usually the player itself.|
|context| Usually the application context will be used for underlying the cookie manager.|
|contentsURL| The stitched stream URL. Please ask FreeWheel Account Manager for the appropriate format.|


#### void handleMetaData(String key, String value, long msec)

This method lets the NexPlayer™ SDK handle metadata updates for the FreeWheel client module.

It is supposed to pass TIT2 for the Stream Stitcher.

**Parameters**

| Name  | Description  | 
|---|---|
|key |The key of the metadata which comes up when the player extracts an ID3 tag.|
|value| The value of the extracted metadata.|
|msec |The current play time of content when the metadata is updated/populated.|


