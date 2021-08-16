# Controlling the Buffer

NexPlayer loads content data into buffers in a device’s memory to prepare for playback (the so-called Prefetch buffer in NexPlayer). Buffer settings can be adjusted in multiple ways with the properties listed below:

- **To Control Buffer Size** :
 - `PREFETCH_BUFFER_SIZE`: This property sets the size of the prefetch buffer to prepare for playback. The default value is 50MB but depending on the content size, this value can be adjusted accordingly. If the buffer status satisfies either limit set by MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION, the filling of the prefetch buffer will be stopped even though there may be spare space still available in the prefetch buffer.

- **To Control Buffering Duration** : NexPlayer uses two separate properties to determine buffering time, `INITIAL_BUFFERING_DURATION` and `RE_BUFFERING_DURATION`.

 - `INITIAL_BUFFERING_DURATION`: This property defines the initial time to buffer before beginning streaming playback (HLS, RTSP, etc). The default value is 5 seconds and when the buffer status meets this value set by INITIAL\_BUFFERING\_DURATION, the player will pause the filling of the buffer. This value is generally lower so that playback can begin as quickly as possible.
 
 - `RE_BUFFERING_DURATION`: This property defines how much content should be buffered when additional buffering during streaming playback (HLS, RTSP, etc) is necessary. The default value is 5 seconds and when the buffer status meets this value set by RE\_BUFFERING\_DURATION, the buffering will be paused. This re-buffering duration is also used when seeking in content (if the target seek destination time falls outside of the previously buffered content data).

**How Buffering Operates in General**

NexPlayer will start filling the prefetch buffer automatically when the amount of data loaded in memory becomes less than the value set by a property defining the buffering minimum. Similarly, the buffer will stop loading data segments when the memory is filled more than the value set by a property defining a maximum buffered amount. The actual properties defining this behavior operate differently depending on the protocol type of the content, but these operations will run automatically in the background and can be adjusted with the following properties:

- **For Non-HTTP Protocols** :

 - `MIN_BUFFER_RATE`: If the prefetch buffer is less full than the value set by this property, the buffer will resume filling until the buffer status meets one of the conditions set by either *MAX\_BUFFER\_RATE* or *MAX\_BUFFER\_DURATION*. The default value is 30%.
 - `MAX_BUFFER_RATE`: If the prefetch buffer is more than this value percent full, buffering will be paused until the buffer status meets the condition set by the property MIN\_BUFFER\_RATE. The default value is 90%.
 - `MIN_BUFFER_DURATION`: If the duration of content available in the filling buffer is less than this value, buffering will resume filling the buffer until its status meets one of the conditions set by either MAX\_BUFFER\_RATE or MAX\_BUFFER\_DURATION. The default value is 30 seconds.
 - `MAX_BUFFER_DURATION`: If the duration of content available in the filling prefetch buffer is greater
       than this value, buffering will be paused until the buffer status meets the condition of MIN\_BUFFER\_DURATION again. The default value is 300 seconds.

- **For HTTP Protocols** : For HTTP protocols, only properties defining buffering maximums, MAX\_BUFFER\_DURATION and MAX\_BUFFER\_RATE, are available. The properties work in the same way as for non-HTTP protocols. After being paused automatically, buffering will automatically resume after 10% of the buffer is exhausted. Note that when MAX\_BUFFER\_DURATION and MAX\_BUFFER\_RATE are both set, NexPlayer will apply the first maximum value that is met. For example, if the percentage set by MAX\_BUFFER\_RATE is passed first, the prefetch buffering will automatically pause even if the buffer is less full than the duration value set for MAX\_BUFFER\_DURATION.
