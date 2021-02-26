# NexPlayer SDK Integration with Agora.io

## Initialize Agora SDK
#### 1. Create RtcEngine
First of all, we have to initialize Agora engine. 

```java
//Initialize event handler
private final IRtcEngineEventHandler mRtcEventHandler = new IRtcEngineEventHandler() {
        @Override
        public void onFirstRemoteVideoDecoded(final int uid, int width, int height, int elapsed) {...}

        @Override
        public void onUserOffline(final int uid, int reason) {...}

        @Override
        public void onUserMuteVideo(final int uid, final boolean toggle) {...}
    };
```
```java
//Initialize RtcEngine
mRtcEngine = RtcEngine.create(getBaseContext(), getString(R.string.agora_app_id), mRtcEventHandler);
```

#### 2. Setup local video
Creates a root view, which will contain the video view.

```java
private void setupLocalVideoFeed() {
        FrameLayout videoContainer = findViewById(R.id.localvideo);
        SurfaceView videoSurface = RtcEngine.CreateRendererView(getBaseContext());
        //Local video surface to overlay NexVideoView
        videoSurface.setZOrderMediaOverlay(true);
        videoContainer.addView(videoSurface);
        mRtcEngine.setupLocalVideo(new VideoCanvas(videoSurface, VideoCanvas.RENDER_MODE_HIDDEN, 0));
        mRtcEngine.setChannelProfile(Constants.CHANNEL_PROFILE_COMMUNICATION);
        mRtcEngine.enableVideo();
        mRtcEngine.setVideoEncoderConfiguration(new		
         		 	VideoEncoderConfiguration(VideoEncoderConfiguration.VD_640x480,
         		 	VideoEncoderConfiguration.FRAME_RATE.FRAME_RATE_FPS_30,
                	VideoEncoderConfiguration.STANDARD_BITRATE,
                	VideoEncoderConfiguration.ORIENTATION_MODE.ORIENTATION_MODE_FIXED_LANDSCAPE));
        mRtcEngine.enableLocalAudio(!mMuted);
    }
```
#### 3. Setup remote videos
Event handler checks whether there are any remote stream. If so, remote video(s) will be loaded.

```java
private final IRtcEngineEventHandler mRtcEventHandler = new IRtcEngineEventHandler() {

        @Override
        public void onFirstRemoteVideoDecoded(final int uid, int width, int height, int elapsed) {
            runOnUiThread(new Runnable() {
                @Override
                public void run() {
                		//Setup remote videos
                    setupRemoteVideoStream(uid);
                }
            });
        }
		
		...
    };
```

#### 4. Join channel
Joins channel with default values. Token and channel name will be the same for this demo (read from remote)

```java
mRtcEngine.joinChannel([channel token], [channel name], null, 0);
```

## Initialize NexPlayer SDK
#### 1. Setup the player

```java
private void setPlayer(){
        mNexPlayer = new NexPlayer();
        
        mNexALFactory = new NexALFactory();
        if(mNexALFactory.init(mContext, android.os.Build.MODEL, null, 0, 1) == false){
            return;
        }
        mNexPlayer.setNexALFactory(mNexALFactory);

	    //Set listeners
        setPlayerListener(mNexPlayer);
        setVideoViewListener(mVideoView);

        mNexPlayer.init(mContext);
        mVideoView.init(mNexPlayer);
        mVideoView.setVisibility(View.VISIBLE);
        mNexPlayer.open(bundle.getString(PARAM_STREAM_URL), null, null, NexPlayer.NEXPLAYER_SOURCE_TYPE_STREAMING, NexPlayer.NEXPLAYER_TRANSPORT_TYPE_TCP);
    }
```

#### 2. Open an stream

```java
private void openStream(String streamUrl){
        mNexPlayer.open(streamUrl, null, null, NexPlayer.NEXPLAYER_SOURCE_TYPE_STREAMING, NexPlayer.NEXPLAYER_TRANSPORT_TYPE_TCP);
    }
```

#### 3. Setup listener

```java
private void setPlayerListener(NexPlayer nexPlayer) {
        nexPlayer.setListener(new NexPlayer.IListener() {

            ...

            @Override
            public void onAsyncCmdComplete(NexPlayer mp, int command, int result, int param1, int param2) {
                if (command == NexPlayer.NEXPLAYER_ASYNC_CMD_OPEN_STREAMING) {
                    mp.start(0);
                } else if (command == NexPlayer.NEXPLAYER_ASYNC_CMD_RESUME) {
                    if (result > 0)  {
                        mNexPlayer.resume();
                    }
                }
            }

            ...
            
        });
    }
```

## Creating the project

### Setup views

##### activity_main.xml

```xml
<androidx.constraintlayout.widget.ConstraintLayout
			...
		>

    <com.nexstreaming.nexplayerengine.NexVideoRenderer
       			... 
			>

        [Insert here all control views (for pause the player, control volume...)]
        *ATTENTION: android:translationZ should be higher on control views

    </com.nexstreaming.nexplayerengine.NexVideoRenderer>

    <androidx.constraintlayout.widget.ConstraintLayout
        		[This will be the camera container]
			>

        <FrameLayout
            		[Create a frame layout for each camera]
             />

    </androidx.constraintlayout.widget.ConstraintLayout>


</androidx.constraintlayout.widget.ConstraintLayout>
```  

> **KEEP IN MIND**
> 
> On LaunchActivity, you should request permissions for ***CAMERA*** and ***RECORD_AUDIO***. If these permissions are not granted, you cannot join the room, because they are needed to run agora.  
> Once the permissions are granted, MainActivity can be started. Above steps must be followed in order to integrate both Agora and NexPlayer sides.


### Implement control views

- **Join / Leave the channel**  

	> 	**1.** Declare local boolean variable `isOnChannel`  
	> 	**2.** Set `isOnChannel = true` every time `joinChannel()` is called and `false` when leave button is pressed  
	>	**3.** Create method **initVideo(boolean isOnChannel)** 
	  
	> 	
	```java
	private void initVideo(boolean isOnChannel){
        if (isOnChannel) {
            mRtcEngine.leaveChannel();
            //**CLEAN ALL VIEWS**
            this.isOnChannel = false;
        } else {
            if ([Permissions are granted]) {
                initAgoraEngine();
            }
            setupLocalVideoFeed();
            mRtcEngine.joinChannel(agoraToken, channel, null, 0);
            this.isOnChannel = true;
        }
    }
    ```
    
- **Mute / Unmute local video**  

	> 	**1.** Declare local boolean variable `mMuted = false`  
	> 	**2.** Set `mMuted = !mMuted` every time mute button is pressed  
	>	**3.** Call method **enableLocalAudio** 
	  
	> 	
	```java
	mRtcEngine.enableLocalAudio(!mMuted);
    ```
   > **Additional:** Change button image whenever local audio is muted or not
   > 	
	```java
	int res = mMuted ? R.drawable.mute : R.drawable.unmute;
  	mMuteButton.setImageResource(res);
    ```
    
- **Control player volume**  

	> 	**1.** Create a SeekBar `private static SeekBar volumeView;`  
	> 	**2.** Set `volumeView.setProgress((int) (mGain * 100));`  
	>	**3.** Implement a listener for SeekBar 
	  
	>   	
	```java
	volumeView.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
        @Override
        public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
            float volume = (float) (seekBar.getProgress() * 0.01);
            setVolume(volume);
        }
        ...
    });
	```
	
- **Pause / Resume player**  

	> 	**1.** Create an ImageButton `private static ImageButton mPauseButton;`  
	> 	**2.** Set pause image for mPauseButton  
	>	**3.** Set onClickListener for mPauseButton 
	  
	>   	
	```java
	mPauseButton.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            if(isPaused()){
                resume();
                mPauseButton.setImageResource(R.drawable.pause);
                hideControls();
            }else{
                mPauseButton.setImageResource(R.drawable.play);
                pause();
            }
        }
    });
	```
	
- **NexPlayer control methods summary**  

	> **void start()**
	>   	
	```java
	public void start() {
        mNexPlayer.start(0);
    }
	```
	> **boolean isPaused()**
	>   	
	```java
	public boolean isPaused() {
        return mNexPlayer.getState() == NexPlayer.NEXPLAYER_STATE_PAUSE;
    }
	```
	> **void pause()**
	>   	
	```java
	public void pause() {
        mNexPlayer.pause();
    }
	```
	> **void resume()**
	>   	
	```java
	public void resume() {
        mNexPlayer.resume();
    }
	```
	> **void setVolume(float fGain)**
	>   	
	```java
	public void setVolume(float fGain){
        mNexPlayer.setVolume(fGain);
    }
	```