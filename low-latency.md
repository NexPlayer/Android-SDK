
## Low Latency

Low latency technology can make the user view the live content as close to real-time as possible.

### How to enable low latency mode

You can enable the low latency mode bu using the below properties.

```java
mNexPlayer.setProperty(NexProperty.LIVE_VIEW_OPTION, NexProperty.LIVE_VIEW_LOW_LATENCY);
mNexPlayer.setProperty(NexProperty.PARTIAL_PREFETCH, 1);
```		       

### How to adjust the latency

You can further configure and optimise the playback by using these options:

- **Buffer Option 1** : Manual Mode The latency value is set by `INITIAL_BUFFERING_DURATION` and `RE_BUFFERING_DURATION` of NexProperty. It should set the reliable value depending on the bitrate of content and network environment.

	
	```java          
	mNexPlayer.setProperty(NexPlayer.NexProperty.LOW_LATENCY_BUFFER_OPTION, NexPlayer.NexProperty.
	LOW_LATENCY_BUFFEROPTION_NONE);
	```

	- **Case 1 :** For **Ultra Low Latency** This mode would be suitable for a managed network maintaining constant bandwidth(ex. Video services based on broadband). The latency might be around
1000ms. 

	```java    
	mNexPlayer.setProperty(NexPlayer.NexProperty.INITIAL_BUFFERING_DURATION, 500);
	mNexPlayer.setProperty(NexPlayer.NexProperty.RE_BUFFERING_DURATION, 500);
	```  
	
	> **Note** Buffering may frequently occur when bandwidth (Throughput) is not sufficient to deliver a
	segment or chunk in time.
	                  
         		
	- **Case 2 :** For Low Latency This mode would be suitable for public networks such as WiFi and LTE. The latency might be around 3000ms. 
	
	```java                
	mNexPlayer.setProperty(NexPlayer.NexProperty.INITIAL_BUFFERING_DURATION, 2000);
	mNexPlayer.setProperty(NexPlayer.NexProperty.RE_BUFFERING_DURATION, 2000);
	```    
         
	> **Note** Buffering will rarely occur, but the latency will be slightly longer than the initial buffering time you set up.
             
       
	- **Case 3 :** Adjust latency for HLS. In case of HLS, the player has disadvantage in low latency perspective than DASH:
		- The player should reload the playlist in order to figure out the URL for the next segment.
		- According to the HLS spec., the player MUST wait at least the duration of the last segment in the Playlist before attempting to reload the Playlist file again.
		- HLS does not have the availabilityStartTime of the segment that is defined in DASH. Therefore, the player does not know when the next segment becomes available. For this reason, we would recommend setting the buffering time to a little bit longer value than the target duration. If target duration is 2 seconds, then we recommend setting the buffering time as below. Otherwise, buffering may occur frequently.
	
	```java
	mNexPlayer.setProperty(NexProperty.INITIAL_BUFFERING_DURATION, 4000);
	mNexPlayer.setProperty(NexProperty.RE_BUFFERING_DURATION, 4000);
	```

- **Buffer Option 2** : Auto Buffer Mode. The latency value is calculated by the player at runtime. During playback, the latency may increase or decrease because it may change depending on the network environment. Example :

	```java
	mNexPlayer.setProperty(NexProperty.LOW_LATENCY_BUFFER_OPTION, NexProperty. LOW_LATENCY_BUFFEROPTION_AUTO_BUFFER);
	```

- **Buffer Option 3** : Constant Buffer Mode. The latency value is calculated by the player at the beginning of playback and maintains the value unchanged during playback. The latency increases more than when using Auto Buffer Mode, but the rebuffering will be reduced and try to maintain constant latency after rebuffering. 

	Example :

	```java
	mNexPlayer.setProperty(NexProperty.LOW_LATENCY_BUFFER_OPTION, NexProperty. LOW_LATENCY_BUFFEROPTION_CONST_BUFFER);
	```
	
### Syncronization option

You can control the behaviour of the playback by setting the `LOW_LATENCY_SYNC_CONTROL_OPTION` property. By default it works in `LOW_LATENCY_CONTROL_SEEK` mode.

Example:

```java
mNexPlayer.setProperty(NexProperty.LOW_LATENCY_SYNC_CONTROL_OPTION, NexProperty. LOW_LATENCY_SYNC_CONTROL_SEEK);
```

- `LOW_LATENCY_SYNC_CONTROL_SEEK` : When the latency rate increases, the latency rate is reduced to the Seek function of the player.

- `LOW_LATENCY_SYNC_CONTROL_SPEEDCONTROL` When the latency rate increases, it adjusts the playback rate at 1.1x playback speed or slowing down to 0.9x to keep the synchronization
	