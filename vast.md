# VAST integration with NexPlayer SDK for Android

VAST is a Video Ad Serving Template for structuring ad tags that serve ads to video players. Using an XML schema, VAST transfers important metadata about an ad from the ad server to a video player. Initially launched in 2008, VAST has played an important role in the growth of the digital video marketplace. (http://www.iab.com/guidelines/digital-video-ad-serving-template-vast-4-0/)

The Interactive Media Ads (IMA) SDKs enable publishers to display ads into video, audio, and game content. This SDK provides a set of APIs to make video ad requests to any VAST-compliant ad server, interpret the ad responses, report metrics to the ad servers, support players in handling ad playback, and incorporate key buying signals such as Active View viewability, IDFA/ADID, content targeting, and more. (https://developers.google.com/interactive-media-ads/)

NexPlayer SDK provides a module that enables customers to playback content with VAST ads. Although developers can integrate the IMA-SDK with the NexPlayer SDK, we strongly recommend using the pre-integrated SDK. Handling IMA-SDK features to playback the VAST template will be easier and more efficient with the 
NexPlayer SDK exclusive features.

## VAST Integration Components

- Interactive Media Ads (IMA) Components

 	- **IMA-SDK Lifecycle**
	This diagram shows the full lifecycle of the IMA-SDK. Constructor and method calls are highlighted in
	blue, events in red, and error conditions are shown with red arrows and red text. Use this as a reference
	as you work through your IMA implementation. https://developers.google.com/interactive-media-ads/docs/sdks/android/lifecycle
	![](assets/IMA_SDK_Lifecycle.png)

	- **Interactions among Video Player, the IMA-SDK, and an Ad serve** The following diagram illustrates and annotates the interactions among your video player, the IMA-SDK v3, and an ad server. It helps you visualize how things will work when you finish implementing your integration with the SDK. https://developers.google.com/interactive-media-ads/docs/sdks/android/basic-interactions

		![](assets/Basic_IMA_SDK_Interactions.png)


- NexPlayer with VAST Components
![](assets/NexVASTPlayer_Components.png)
	- NexAdsPlayer is a wrapping class of VideoAdPlayer, VideoProgressUpdate, and UIContainer.
 	- VideoAdPlayer is an ad player of IMA-SDK.
 	- The UIContainer is set with VideoView.
 	- VideoProgressUpdate can be implemented with the duration of ad player.

### Basic VAST Sample Guide

This guide will show how to integrate the NexIMAWrapper into a VAST sample video player application. It is required to set the VideoView when creating NexIMAWrapper with some conditions.

- Conditions
 	- Include Google Play service in your application (https://developers.google.com/android/guides/setup) and add the following piece of code to your application-level ‘build.gradle’ file.

	```gradle
	dependencies {
		vastCompile ’com.google.ads.interactivemedia.v3:interactivemedia:3.9.4’
		vastCompile ’com.google.android.gms:play-services-ads:15.0.1’
	}
	```

 	- Add the following ‘<meta-data>’ code block to your ‘<AndroidManifest.xml>’ inside the ‘application’ tag.

	![](assets/Meta_Data.png)


- Basic steps

	- After checking the above conditions, you should create NexIMAWrapper class to handle VAST ad requests from IMA-SDK and respond to IMA-SDK events. NexIMAWrapper implements several interfaces from the IMA-SDK to track VAST ad events:
	
		- AdErrorEvent.AdErrorListener: 
		- AdsLoader.AdsLoadedListener:
		- AdEvent.AdEventListener:

	```java
	public class NexIMAWrapper implements AdErrorEvent.AdErrorListener, 
		AdsLoader.AdsLoadedListener, AdEvent.AdEventListener {
		...
		}
	```

 	- The NexIMAWrapper instance should be created after NexPlayer.init() is called. This instance will keep the ads logic for handling the IMA SDK integration code and events. 

	```java
	@Override
	protected void onCreate(Bundle icicle) {

		mNexPlayer = new NexPlayer();
		mNexALFactory = new NexALFactory();
		...
		mNexALFactory.init(...);
		mNexPlayer.setNexALFactory(...);
		mNexPlayer.init(this, mPrefData.mLogLevel);
		...
		mNexVASTController = new NexIMAWrapper(context, ViewGroup, false);
		...
	}
	```

	- To create NexIMAWrapper, context and ViewGroup are needed.
	```java
	public NexIMAWrapper(Context context, ViewGroup view);
	```
	- In NexIMAWrapper constructor, NexAdsPlayer instance is created internally, and implements listener interfaces so the IMA-SDK can be notified when your video content finishes or not with an error.
	- If NexIMAWrapper gets a notification of content completion, or an error from NexAdsPlayer, NexIMAWrapper calls AdsLoader.contentComplete(), internally, to notify IMA-SDK.
	- After created NexIMAWrapper, you should set the listeners and actions of VAST.
	```java
	// This interface can be implemented in an application in order to receive ads ready events from NexIMAWrapper
	mNexVASTController.setAdsReadyListener( new NexIMAWrapper.AdsReadyListener() {
            // This method indicates when ADs are successfully loaded.
			@Override
            public void onAdsLoaded() {
                ...
            }

			// This method indicates that an error has happened.
            @Override
            public void onAdsLoadError(AdError error) {
                ...
            }
    });

	// This interface can be implemented in an application in order to receive ADs media events from NexVastController;
	mNexVASTController.setAdsContentEventListener(new NexIMAWrapper.AdsMediaEventListener() {
		// This method indicates that the content playback has been successful until the end of the content.
		@Override
		public void onAllCompletion(NexPlayer mp) {
			...
		}

		//
		@Override
		public void onContentPauseRequested() {
			...
		}

		//
		@Override
		public void onContentResumeRequested() {
			...
		}

		// This method indicates when ad is loaded.
		@Override
		public void onAdLoaded(boolean isLinear, int adPosition, int adCountInGroup, double adDuration, int adGroupidx) {
			...
		}

		// This method indicates when ad playback is completed.
		@Override
		public void onAdCompleted() {
			...
		}

		// // This method indicates when ad playback has started after been loaded.
		@Override
		public void onAdStarted(boolean isSkippable, double skipTimeOffset){
			...
		}

	});

	// This interface can be implemented in an application in order to receive error events from NexIMAWrapper.
	mNexVASTController.setNexPlayerErrorListener(new NexIMAWrapper.OnErrorListener() {
		// An error has occurred during playback.
		@Override
		public void onError(NexPlayer mp, NexPlayer.NexErrorCode errorCode) {
			...
		}
	});

	// This interface can be implemented in an application in order to receive ad point events from NexIMAWrapper.
	mNexVASTController.setAdPointsListener(new NexIMAWrapper.AdPointsListener() {
		// This method indicates when a point of ADs is successfully loaded.
		@Override
		public void onAdPointsLoaded(int[] adPoints) {
			...
		}

		// This method indicates when AD url and start time are successfully loaded.
		@Override
		public void onAdUrlLoaded(int startTime, String adUrl){
			...
		}
	});
	```
	- It is strongly recommended to set the NexIMAWrapper.play() into onAdsLoaded().
	```java
	...
	mNexVASTController.setAdsReadyListener( new NexIMAWrapper.AdsReadyListener() {
		@Override
		public void onAdsLoaded() {
			...
			mNexVASTController.play(0);
			...
		}
	...
	});
	```
