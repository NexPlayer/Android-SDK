# NexPlayer Logs

NexPlayer provides different log levels, which makes it easier to understand what is happening in the background, both in the application and native layers.

The range of NexPlayer SDK logs is from 0 up to 4. The higher the number, the more information is extracted from the player. 

Apart from this log level setting, NexPlayer also provides the option, to get logs from some other libraries composing our SDK. These will be:

- Codec library. 
- Renderer library.
- Protocol library.

?> Please note that enabling the logs might effect the device performance hence the playback.

### How to obtain the NexPlayer logs?

In order to get full logs from our SDK, some steps and different APIs must be used:

At first, we need to set the SDK log level, which will be 4:

```java
....
mNexALFactory.init (mContext, android.os.Build.MODEL, NexPlayer.NEX_DEVICE_USE_AUTO, 4, 1);
....
mNexPlayer.init (mContext, 4);
....
```

Once the above step is done, we need to set the log level for the rest of the NexPlayer native libraries that are part of the SDK `(5, 5, 11)`:

```java
....
/*
* @param codecLog     The level of logs to be generated related to codecs, as an integer.
* @param RendererLog  The level of logs to be generated related to rendering, as an integer.
* @param protocol_Log The level of logs to be generated related to protocols, as an integer.
*/
mNexPlayer.setDebugLogs(5, 5, 11); 
....
```

The log level settings for the native libraries need to be done before calling NexPlayer.open()

By default, the basic log level for the SDK will be 0 whilst for the native libraries will be (-1, -1, 0).

As a way of confirming that full logs are enabled, a log should have been printed, by looking for `Powered by NexPlayerSDK` with the SDK version that is being used:

### Step by Step Setup Guide

1. Set up the NexPlayer logging: 

```
int logLevel = 4;
mNexALFactory.init (Context, android.os.Build.MODEL, NexPlayer.NEX_DEVICE_USE_AUTO, logLevel, 1);
....
mNexPlayer.init (Context, logLevel);
....
mNexPlayer.setDebugLogs (5, 5, 11);
```

2. Clear the log buffer from the connected mobile device with the following command: 

`adb logcat -c`

3. Start collecting the device logs and writing them into a file:

`adb logcat > fileName.log`

4. Start any content playback (device logging will start printing NexPlayer logs into the file above).

5. Once the content is finished, close the player.

6. Stop adb logging, pressing `ctrl+c`.

7. filename.log file will include all the necessary NexPlayer logs

If you want to stop the logging before the content is finished, or before exiting it, skip step 5.

### ADB logging commands

To clear the log buffer from the device

`adb logcat -c` 

Write device logs into the console

`adb logcat` 

Write device logs into a file

`adb logcat > out.log`  

You can read more about the ADB logcat from [here](https://developer.android.com/studio/command-line/logcat)

#### Other NexPlayer logging features

NexPlayer provides other options for the logging process, which can be checked in our documentation:

- [Log2File](/Android-SDK/advanced/log2File): This NexPlayer feature allows you to save logs on the device and making it easier to debug the playback process. 

- [Logging Callback](/Android-SDK/advanced/logging-callback): With this feature, you can receive the NexPlayer logs from the application side to collect them directly from the users or for any kind of debug purposes. 

