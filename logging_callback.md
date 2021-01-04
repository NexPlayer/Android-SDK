# NexPlayer Logging Callback

### Enabling the feature

NexPlayer logs can be received to application side by enabling the following property:

```
String yourSocketName = "socket";
String socket = new File(getApplicationContext().getFilesDir(), yourSocketName).getAbsolutePath();
mNexPlayer.setProperty(NexProperty.SET_UDS_NAME_FOR_LOGGING, socket);
mNexPlayer.setProperty(NexProperty.ENABLE_LOGGING_TO_APP_SIDE,1);
```

### Receiving the logs

`NexLogd.java` is a simple example about how to receive a log message. You can find this class and usage inside the sample application for your reference.

The code below is a part of `NexLogd.java` and after receiving the log, it is coverted to String and just printed via Log.d function as an example:

```java
public void run() {
	String yourSocketName = "socket";
    String socket = new File(mContext.getFilesDir(), yourSocketName).getAbsolutePath();
    InputStream serverInStream = null;
    LocalSocket recvSocket = new LocalSocket(LocalSocket.SOCKET_DGRAM);
    mLocSockAddr = new LocalSocketAddress(socket, LocalSocketAddress.Namespace.FILESYSTEM);

    try {
        recvSocket.bind(mLocSockAddr);
        serverInStream = recvSocket.getInputStream();

    } catch (IOException e) {
        e.printStackTrace();
    }

    mLooping = true;
    mData = new byte[1024];
    while(mLooping) {
        try {
            int readn = serverInStream.read(mData, 0, 1023);
            String logmsg = new String(mData, 0, readn-1);
            Log.d(TAG, logmsg);
        } catch (IOException e) {
            e.printStackTrace();
            mLooping = false;
            Log.d(TAG," an error happened while reading from UDS");
            break;
        }
    }

    Log.d(TAG,"finished a loop of receiving a log message");
}
```


