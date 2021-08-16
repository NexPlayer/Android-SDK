# Player Statistics

Once you have a player up and running is interesting to get the statistics about the url/local video you are playing, this can help to locate problems related to the content you are using and give you several hints about performance.

Through this guide you will learn all the tweaks for getting all your player data.

### Initialization

To monitor the playback statistics, **after** NexPlayer is created and initialized but **before** content is opened, the app must:  

1. Create an instance of the NexStatisticsMonitor class.
2. Set a listener to receive the events reporting statistics information with `IStatisticsListener`.
3. If desired, the time interval at which statistics are monitored can be changed with calls to setDuration.

First of all you need to import the classes that will provide you with the information related to the content playing. Here you can also see the 4 types of information that `NexStatisticsMonitor` will provide you for the playing content.  

```java
import com.nexstreaming.nexplayerengine.NexStatisticsMonitor;
import static com.nexstreaming.nexplayerengine.NexStatisticsMonitor.HttpStatisticsMetric;
import static com.nexstreaming.nexplayerengine.NexStatisticsMonitor.STATISTICS_GENERAL;
import static com.nexstreaming.nexplayerengine.NexStatisticsMonitor.STATISTICS_HTTP;
import static com.nexstreaming.nexplayerengine.NexStatisticsMonitor.STATISTICS_INITIAL;
import static com.nexstreaming.nexplayerengine.NexStatisticsMonitor.STATISTICS_SYSTEM;
```

With this you can start receiving the information related to the content, when the related objects are created.

### NexStatisticsMonitor

The NexStatisticsMonitor class defines a statistics monitoring module to be used during playback of HLS, DASH, or SS content with NexPlayer.

It should be used with `IStatisticsListener` interface. Here is some example code for how to implement and use the class.

1. Create a new NexStatisticsMonitor in the app

```java
NexStatisticMonitor mMonitor = new NexStatisticMonitor(mNexPlayer);
```

2. Set a listener for statistics-related events

```java
mMonitor.setListener( listener );
```

3. Set the time interval at which general playback statistics should be requested (ie every 5 seconds)

```java
mMonitor.setDuration(NexStatisticsMonitor.GeneralStatistic, 5);
```

4. Set the time interval at which system statistics during playback should be requested.

```java
mMonitor.setDuration(NexStatisticsMonitor.SystemStatistic, seconds);
```

### IStatisticsListener

The IStatisticsListener interface will be implemented by the developer and will receive all the information of the playing content.  

Main method to override is **onUpdate**:  

```java
IStatisticsListener mStatisticsListener = new NexStatisticsMonitor.IStatisticsListener() {
	@Override
	public void onUpdated(int statisticsType, HashMap<IStatistics, Object> map) {
		if( statisticType == STATISTICS_GENERAL) {
			printGeneralStatistic( map );
		}
		else if( statisticType == STATISTICS_INITIAL) {
			printInitialStatistic( map );
		}
		else if( statisticType == STATISTICS_HTTP) {
			printHttpStatistic( map );
		}
		else if ...
	}
};
mMonitor.setListener(mStatisticsListener);
```

Method for printing the GeneralStatistics
```java
private void printGeneralStatistic( HashMap<NexStatisticsMonitor.IStatistics, Object> map ) {
	String str = "\n";
	Iterator it = map.entrySet().iterator();

	while (it.hasNext()) {
		Map.Entry entry = (Map.Entry) it.next();

		NexStatisticsMonitor.GeneralStatisticsMetric key = (NexStatisticsMonitor.GeneralStatisticsMetric)entry.getKey();
		Object value = entry.getValue();

		str += ( key.toString() + " : " + getString(value) + "\n\n" );
	}
	System.out.println(str);
}
```

Instead of printing it into the debug console, it is recommended to create a view inside the app for showing the statistics while the content is running or a logs module for checking it later.

## API Reference

### NexStatisticsMonitor Class

This class defines a statistics monitoring module to be used during playback of HLS, DASH, or SS content with NexPlayer.

Implementing this class in an application makes it easier to monitor different kinds of statistics at regular intervals during playback of HLS, DASH, or SS content in order to for example have more details about player performance.

To monitor HLS, DASH, or SS playback statistics, after NexPlayer is created and initialized but before content is opened, an application must:

1. First, create an instance of this NexStatisticsMonitor class,
2. Next, set a listener to receive the events reporting statistics information with IStatisticsListener,
3. lastly, if desired, the time interval at which statistics are monitored can be changed with calls to setDuration.

Depending on what information about playback is needed, different statistics can be retrieved from NexPlayer, including general playback statistics (GeneralStatisticsMetric), statistics when initializing content (InitialStatisticsMetric), HTTP statistics(HttpStatisticsMetric), and system statistics during playback (SystemStatisticsMetric).

The available statistics are briefly summarized in the table below:

<table>
    <thead>
        <tr>
            <th>Statistics Category</th>
            <th colspan=2>Metric</th>
            <th>Data Type</th>
            <th>Unit</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=16>STATISTICS_GENERAL</td>
            <td colspan=2 rowspan=1 style="text-align: center; vertical-align: middle;">PLAY_TIME_SEC</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">seconds</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;"colspan=2 rowspan=1>BYTES_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">Bytes</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>CUR_NETWORK_BW_BPS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">bps</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>CUR_TRACK_BW_BPS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">bps</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_REQUESTS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_DOWN_RATE</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_FAIL_TO_PARSE</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_SEG_IN_BUFFER</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_REQUEST_ERRORS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_REQUEST_TIMEOUT</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_TRACK_SWITCH_UP</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_TRACK_SWITCH_DOWN</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_VIDEO_FRAME_RENDERED</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
         <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_VIDEO_FRAME_DECODED</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
         <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_HTTP_REQUESTS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" rowspan=9>STATISTICS_INITIAL</td>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_TRACK</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_PREBUFFERED_SEGMENTS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>NUM_REDIRECTS</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>MASTER_PLAYLIST</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>MASTER_PLAYLIST_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>INITIAL_PLAYLIST</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>INITIAL_PLAYLIST_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>START_SEGMENT_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>CONTENT_DURATION</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">msec</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" rowspan=15>STATISTICS_HTTP</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=6>DOWN_START</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>FILE_TYPE</td>
            <td style="text-align: center; vertical-align: middle;">FileType</td>
            <td style="text-align: center; vertical-align: middle;">FileType</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>SEG_NO</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">num</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>SEG_DURATION</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">msec</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>TRACK_BW</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">bps</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>MEDIA_COMPOSITION</td>
            <td style="text-align: center; vertical-align: middle;">int</td>
            <td style="text-align: center; vertical-align: middle;">MediaType</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>CONNECT</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>CONNECTED</td>
            <td colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>HEADER_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=3>DATA_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>BYTE_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">Bytes</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>CONTENT_LENGTH</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">Bytes</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=2>DOWN_END</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>BYTE_RECEIVED</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">Bytes</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>ERROR</td>
            <td style="text-align: center; vertical-align: middle;" colspan=1 rowspan=1>RESOURCE_URL</td>
            <td style="text-align: center; vertical-align: middle;">String</td>
            <td style="text-align: center; vertical-align: middle;">text</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" rowspan=2>STATISTICS_SYSTEM</td>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>CPU_USAGE</td>
            <td style="text-align: center; vertical-align: middle;">double</td>
            <td style="text-align: center; vertical-align: middle;">percentage (0 - 1)</td>
        </tr>
        <tr>
            <td style="text-align: center; vertical-align: middle;" colspan=2 rowspan=1>FREE_MEMORY_KB</td>
            <td style="text-align: center; vertical-align: middle;">long</td>
            <td style="text-align: center; vertical-align: middle;">kilobytes</td>
        </tr>
    </tbody>
</table>

Example Code for how to implement and use `NexStatisticsMonitor`:

```java
// Create a new NexStatisticsMonitor in the application
NexStatisticMonitor mMonitor = new NexStatisticMonitor(mNexPlayer);

IStatisticsListener listener =
{
	void onUpdated(int statisticsType, HashMap<IStatistic, Object> map) {
		if( statisticsType == STATISTICS_GENERAL ) {
			while ( IStatistics key in map ) {
				GeneralStatisticsMetric key = (GeneralStatisticsMetric)map.getKey();
				Object value = map.getValue();
			}
		}
		else if( statisticsType == STATISTICS_INITIAL ) {
			while ( IStatistics key in map ) {
				InitialStatisticsMetric key = (InitialStatisticsMetric)map.getKey();
				Object value = map.getValue();
			}
		}
		else if( statisticsType == STATISTICS_HTTP ) {
			while ( IStatistics key in map ) {
				HttpStatisticsMetric key;
				HashMap<HttpStatisticsParamKey, Object> subMap;
				key = (HttpStatisticsMetric)map.getKey();
				subMap = (HashMap<HttpStatisticsParamKey,Object>)map.getValue();
				
				while(HttpStatisticsParamKey key in subMap) {
					HttpStatisticsParamKey paramkey = (HttpStatisticsParamKey)subMap.getKey();
					Object value = entry.getValue();
				}
			}
		}
		else if ..
	}
}

// Set a listener for statistics-related events
mMonitor.setListener( listener );

// Set the time interval at which general playback statistics should be requested (ie every 5 seconds)
mMonitor.setDuration(NexStatisticsMonitor.GeneralStatistic, seconds);
// Set the time interval at which system statistics during playback should be requested.
mMonitor.setDuration(NexStatisticsMonitor.SystemStatistic, seconds);
```

**Classes**

- `enum FileType` An enumeration of the possible types of files being handled by NexPlayer during HLS, DASH, or SS playback.

- `enum GeneralStatisticsMetric` This is an enumeration of the possible general statistics that can be requested during playback of HLS, DASH, or SS content in NexPlayer.

- `enum HttpStatisticsMetric` This enumeration defines the possible HTTP statistics that can be requested during HLS, DASH, or SS playback by NexPlayer.
 
- `enum HttpStatisticsParamKey` This enumeration defines the parameter key, for parameters related to HTTP statistics monitored during HLS, DASH, or SS playback.

- `enum InitialStatisticsMetric` This is an enumeration of the possible initial statistics that can be requested when initializing playback of HLS, DASH, or SS content in NexPlayer.

- `interface IStatistics` This interface defines a set of statistics to be received fromNexPlayer aboutHLS, DASH, or SS playback.

- `interface IStatisticsListener` This interface defines the listener that will be used to receive statistics related to playback.

- `enum MediaType` An enumeration defining the possible types of HLS, DASH, or SS media can be played by NexPlayer.

- `enum StatisticsError` An enumeration of the statistics-related errors possible when using theNexStatisticsMonitor.

- `enum SystemStatisticsMetric`  This is an enumeration of the possible system statistics that can be requested during playback of HLS, DASH, or SS content in NexPlayer.

#### NexStatisticsMonitor( NexPlayer np )

Defines theNexStatisticsMonitormodule that an application can use to retrieve statistics about playback of HLS, DASH, or SS content in NexPlayer.

**Parameters**

| Name            | Description              |
|-----------------|------|
| np | TheNexPlayerinstance that the statistics monitor will receive events from. |

#### StatisticsErrorsetDuration ( int statisticsType, double seconds )

This method sets the interval of time at which playback statistics will be reported and sent (for HLS, DASH, or SS content only).

After a statistics listener has been set, this method can be called to change the interval at which general playback and system statistics are monitored at any time before starting playback.

The default interval of time for monitoring general and system statistics during HLS, DASH, or SS playback is 5000 ms or 5 seconds.

> **Note** The interval between statistics events can only be set for GeneralStatisticsMetric and SystemStatisticsMetric requests so an error will be returned if any other statisticsType is indicated because initial statistics and HTTP statistics are event-driven statistics.

**Parameters**

| Name            | Description              |
|-----------------|------|
| statisticsType | statisticsType The type of statistics to be retrieved at the interval set here. This should be STATISTICS\_GENERAL for general playback statistics or STATISTICS\_SYSTEM for monitoring system statistics during playback. |
| seconds            | The interval at which statistics will be monitored, in seconds, as a double.              |

**Returns**

if successful or the relevant NexStatistics error code (for example, RETURN\_ERROR\_DURATION\_INVALID)

**See Also**

- GeneralStatistics
- SystemStatistics
- StatisticsErrror

#### void setListener ( IStatisticsListener listener )

This method sets a listener to receive statistics events about HLS, DASH, or SS playback in NexPlayer.

A statistics listener should be set after NexPlayer has been created and initialized, but before content playback begins.

**Parameters**

| Name            | Description              |
|-----------------|------|
| listener | The listener that will receive playback statistics events.|

**See Also**

- setDuration(int statisticsType, double seconds)

#### final int STATISTICS\_GENERAL = 0

A possible argument value for the parameterstatisticsTypein the onUpdated() and setDuration()
 methods for the type of statistics being requested and received, for general playback statistics.

#### final int STATISTICS\_HTTP = 2

A possible argument value for the parameter statisticsType in the onUpdated() method for the type of
statistics being requested and received, for HTTP statistics.

#### final int STATISTICS\_INITIAL = 1

A possible argument value for the parameter statisticsType in the onUpdated() method for the type of
statistics being requested and received, for initial statistics (statistics about when playback is initialized).

#### final int STATISTICS\_SYSTEM = 3

A possible argument value for the parameter statisticsType in the onUpdated() and setDuration()
 methods for the type of statistics being requested and received, for system statistics.

### NexStatisticsMonitor.StatisticsError Enum

An enumeration of the statistics-related errors is possible when using `theNexStatisticsMonitor`.

#### ERROR_DURATION\_INVALID

The duration set is invalid or cannot be applied to the statistics being requested.

#### ERROR_NONE

Playback statistics were successfully retrieved without error.

#### ERROR_TYPE\_INVALID

The type of statistics being requested is invalid.


### NexStatisticsMonitor.SystemStatisticsMetric Enum

This is an enumeration of the possible system statistics that can be requested during playback of HLS, DASH, or SS content in NexPlayer.

These statistics are only related to the system performance during playback. For other statistics specifically about the HLS, DASH, or SS content playback or HTTP statistics, monitor *GeneralStatisticsMetric* or *HttpStatisticsMetricinstead*.

**See Also**

- GeneralStatisticsMetric
- HttpStatisticsMetric
- setDuration

#### SystemStatisticsMetric (int code)

Sets the system statistics metric.

#### int getCode ()

Gets the system statistics code, as an integer.

**Returns**

The system statistics code requested, as an integer.

Implements `NexStatisticsMonitor.IStatistics`.

#### CPU_USAGE = ( 0x00010000 )

The current CPU usage, as a percentage, is represented as a value between 0 and 1, where zero is 0 percent and 1 is 100 percent.

#### FREE_MEMORY\_KB = ( 0x00020000 )

The current amount of memory free, in kilobytes, as a *long*.


### NexStatisticsMonitor.FileType Enum

An enumeration of the possible types of files being handled by NexPlayer during HLS, DASH, or SS playback.

These are possible values for the HTTP statistics parameter key, *FILE\_TYPE*.

#### FileType (intcode)

Sets the ***FileType***.

#### int getCode()

Gets the ***FileType*** code as an integer.

**Returns**

The requested ***FileType*** code as an integer.
 
#### static FileType toFileType (int code)

This method gets the ***FileType*** from the integer code of the ***FileType***.

**Returns**

The ***FileType*** corresponding to the given integer code. This will be one of:
 
- `UNKNOWN` for an unknown filetype,
- `MANIFEST` for a manifest file,
- `SEGMENT` for a segment file,
- `INITIAL_SEGMENT` for an initial segment file, or
- `KEY` for a key file.

### NexStatisticsMonitor.GeneralStatisticsMetric Enum

This is an enumeration of the possible general statistics that can be requested during playback of HLS, DASH, or SS content in NexPlayer.

The statistics defined here are for general playback of HLS, DASH, or SS content. If statistics about the initialization of content are required, please review ***InitialStatisticsMetric*** instead.

**See Also**
 
- InitialStatisticsMetric
- IStatistics
- setDuration

#### GeneralStatisticsMetric (int code)

Sets the general statistic metric.

#### int getCode ()

Gets the general statistic code, as an integer.

**Returns**
 
The general statistics code requested.
 
Implements **NexStatisticsMonitor.IStatistics**.

#### BYTES\_RECEIVED = ( 0x00000200 )

The bytes received, as a long.

This is the same as NexRTStreamInformation.mNumOfBytesRecv.

#### CUR\_NETWORK\_BW\_BPS = ( 0x00000300 )

The current bandwidth of the network, in bps, as an integer.

This is the same as NexRTStreamInformation.mCurNetworkBw.

#### CUR\_TRACK\_BW\_BPS = ( 0x00000400 )

The current track bandwidth, in bps, as an integer.

This is the same as NexRTStreamInformation.mCurTrackBw.

#### NUM\_HTTP\_REQUESTS = ( 0x00001000 )

This current number of HTTP requests that have been made, as an integer.

This is the same as the running count of onHttpRequest (NexPlayer mp, String msg) calls.

#### NUM\_REQUEST\_ERRORS = ( 0x00000A00 )

The current number of segments that the player failed to receive, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegFailToReceive.

#### NUM\_REQUEST\_TIMEOUT = ( 0x00000B00 )

The current number of segment reads that resulted in a timeout, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegTimeout.

#### NUM\_SEG\_DOWN\_RATE = ( 0x00000700 )

The number of segments that have an actual read bitrate below the bitrate specified in the profile, where the read bitrate is the speed at which the segments are read from the network.

This is the same as NexRTStreamInformation.mNumOfSegDownRate.

#### NUM\_SEG\_FAIL\_TO\_PARSE = ( 0x00000800 )

The number of segment reads that were failed to be read and parsed, for example, due to HTTP errors, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegFailToParse.

#### NUM\_SEG\_IN\_BUFFER = ( 0x00000900 )

The current number of segments in the buffer, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegInBuffer.

#### NUM\_SEG\_RECEIVED = ( 0x00000600 )

The current number of segments received, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegReceived.

#### NUM\_SEG\_REQUESTS = ( 0x00000500 )

The current number of segment requests, as an integer.

This is the same as NexRTStreamInformation.mNumOfSegRequest.

#### NUM\_TRACK\_SWITCH\_DOWN = ( 0x00000D00 )

The number of times the content profile has been changed to a profile with a lower bitrate, as an integer.

This is the same as NexRTStreamInformation.mNumOfTrackSwitchDown.

#### NUM\_TRACK\_SWITCH\_UP = ( 0x00000C00 )

The number of times the content profile has been changed to a profile with a higher bitrate, as an integer.

This is the same as NexRTStreamInformation.mNumOfTrackSwitchUp.

#### NUM\_VIDEO\_FRAME\_DECODED = ( 0x00000F00 )

The current number of frames that have been decoded, as an integer.

This is the same as getContentInfoInt (NexPlayer.CONTENT\_INFO\_INDEX\_VIDEO\_CODEC\_DECODIN-
G\_TOTAL\_COUNT).

#### NUM\_VIDEO\_FRAME\_RENDERED = ( 0x00000E00 )

The current number of frames that have been successfully rendered, as an integer.

This is the same as getContentInfoInt (NexPlayer.CONTENT\_INFO\_INDEX\_VIDEO\_RENDER\_TOTAL\_COUNT).

#### PLAY\_TIME\_SEC = ( 0x00000100 )

The current play time in seconds, as along.

This is the same as the count of NEXPLAYER\_EVENT\_TIME.


### NexStatisticsMonitor.HttpStatisticsMetric Enum

This enumeration defines the possible HTTP statistics that can be requested during HLS, DASH, or SS playback by NexPlayer.

For general playback statistics or system statistics during playback, please monitor `GeneralStatisticsMetric` or `SystemStatisticsMetric` instead.

**Public Attributes**

- **DOWN\_START** = ( 0x00000000 )
- **CONNECT** = ( 0x00000001 )
- **CONNECTED** = ( 0x00000003 )
- **HEADER\_RECEIVED** = ( 0x00000004 )
- **DATA\_RECEIVED** = ( 0x00000005 )
- **DOWN\_END** = ( 0x00000006 )
- **ERROR** = ( 0x00000007 )

**See Also**
 
- GeneralStatisticsMetric
- SystemStatisticsMetric
- HttpStatisticsParamKey

#### HttpStatisticsMetric( int code )

Sets the HTTP statistics metric.

#### int getCode ( )

Gets an HTTP statistic metric as an integer.

**Returns**

The requested HTTP statistic metric, as an integer.
 
Implements `NexStatisticsMonitor.IStatistics`.

### NexStatisticsMonitor.HttpStatisticsParamKey Enum

This enumeration defines the parameter key, for parameters related to HTTP statistics monitored during HLS, DASH, or SS playback.

**Public Attributes**

- **RESOURCE\_URL** = ( 0x00000000 )
    The resource URL, as a *String*.
- **FILE\_TYPE** = ( 0x00000001 )
	 The file type being received, as a `FileType`.
- **SEG\_NO** = ( 0x00000002 )
    The current segment number, as an integer.
- **SEG\_DURATION** = ( 0x00000003 )
    The duration of the current segment, as an integer.
- **TRACK\_BW** = ( 0x00000004 )
    The bandwidth of the current track, as an integer.
- **MEDIA\_COMPOSITION** = ( 0x00000005 )
    The media composition of the current content, as an integer.
- **BYTE\_RECEIVED** = ( 0x00000006 )
    The current number of bytes received, as a *long*.
- **CONTENT\_LENGTH** = ( 0x00000007 )
    The current length of the HLS, DASH, or SS content received so far, as a *long*.
- **ERROR\_CODE** = ( 0x00000008 )
    The error code.

#### HttpStatisticsParamKey (int code)

Sets the HTTP statistics parameter key.

#### final int getCode ()

Gets the HTTP statistics parameter key as an integer code.

**Returns**
 
The HTTP statistics parameter key requested, as an integer.
 
#### BYTE\_RECEIVED = ( 0x00000006 )

The current number of bytes received, as a *long*.

A parameter for the HTTP statistics, `DATA_RECEIVED` and `DOWN_END`.

#### CONTENT\_LENGTH = ( 0x00000007 )

The current length of the HLS, DASH, or SS content received so far, as a *long*.

A parameter for the HTTP statistic, DATA\_RECEIVED.

#### ERROR\_CODE = ( 0x00000008 )

The error code.

A parameter for the HTTP statistic, *ERROR*.

#### FILE\_TYPE = ( 0x00000001 )

The file type being received, as a *`FileType`*.

A parameter for the HTTP statistic, *DOWN\_START*.

#### MEDIA\_COMPOSITION = ( 0x00000005 )

The media composition of the current content, as an integer.

A parameter for the HTTP statistic, *DOWN\_START*.

#### RESOURCE\_URL = ( 0x00000000 )

The resource URL, as a *String*.

A possible parameter for the HTTP statistics, *DOWN\_START*, *CONNECT*, *CONNECTED*, *HEADER\_RECEIVED*, *DATA\_RECEIVED*, *DOWN\_END*, and *ERROR*.

#### SEG\_DURATION = ( 0x00000003 )

The duration of the current segment, as an integer.

A parameter for the HTTP statistic, *DOWN\_START*.

#### SEG\_NO = ( 0x00000002 )

The current segment number, as an integer.

A parameter for the HTTP statistic, *DOWN\_START*.

#### TRACK\_BW = ( 0x00000004 )

The bandwidth of the current track, as an integer.

A parameter for the HTTP statistic, *DOWN\_START*.


### NexStatisticsMonitor.InitialStatisticsMetric Enum

This is an enumeration of the possible initial statistics that can be requested when initializing playback of HLS, DASH, or SS content in NexPlayer.

Since this statistics metric is only for monitoring the statistics related to the initialization of content, for more general playback statistics, monitor *GeneralStatisticsMetric* instead.

**See Also**
 
`GeneralStatisticsMetric`
 

#### int getCode ()

Gets the initial statistic code, as an integer.

**Returns**

The initial statistics code, as an integer.
 
> Implements `NexStatisticsMonitor.IStatistics`.

#### CONTENT\_DURATION = ( 0x00000090 )

The total duration of the current content, as an integer.

This is the same as `NexContentInformation.mMediaDuration`.

#### INITIAL\_PLAYLIST = ( 0x00000060 )

The full content of the initial manifest playlist, as a *String*.

This is the same as *NexRTStreamInformation.mInitialMpd*.

#### INITIAL\_PLAYLIST\_URL = ( 0x00000070 )

The actual URL (after all redirects) of the initial request for the manifest playlist, as a *String*.

This is the same as *NexRTStreamInformation.mInitialMpdUrl*.

#### MASTER\_PLAYLIST = ( 0x00000040 )

The full content of the master manifest playlist, as a *String*.

This is the same as *NexRTStreamInformation.mMasterMpd*.

#### MASTER\_PLAYLIST\_URL = ( 0x00000050 )

The URL of the master manifest playlist, as a *String*.

This is the same as *NexRTStreamInformation.mMasterMpdUrl*.

#### NUM\_PREBUFFERED\_SEGMENTS = ( 0x00000020 )

The total number of segments loaded in the buffer, as an integer.

This is the same as *NexRTStreamInformation.mNumOfSegInBuffer*.

#### NUM\_REDIRECTS = ( 0x00000030 )

The total number of redirects, as an integer.

This is the same as *NexRTStreamInformation.mNumOfRedirect*.

#### NUM\_TRACK = ( 0x00000010 )

The total number of tracks in the current content, as an integer.

#### START\_SEGMENT\_URL = ( 0x00000080 )

The description of the initially selected profile, as a *String*.

This is the same as *NexRTStreamInformation.mStartSegUrl*.


### NexStatisticsMonitor.IStatistics Interface

This interface defines a set of statistics to be received from NexPlayer about HLS, DASH, or SS playback.

Every set of statistics (general, initial, HTTP, and system statistics) implements this interface.

**See Also**

- GeneralStatistics
- InitialStatistics
- HTTPStatistics
- SystemStatistics
 

#### int getCode ( )

This method gets a statistics code.

Implemented in `NexStatisticsMonitor.SystemStatisticsMetric`, `NexStatisticsMonitor.HttpStatisticsMetric`, `NexStatisticsMonitor.InitialStatisticsMetric`, and `NexStatisticsMonitor.GeneralStatisticsMetric`.


### NexStatisticsMonitor.IStatisticsListener Interface

This interface defines the listener that will be used to receive statistics related to playback.

Any listener created to receive statistics from NexPlayer must implement this interface.

Once an instance of *NexStatisticsMonitor* is created, a statistics listener implementing this interface can be set with *setListener(IStatisticsListener listener)*.


#### void onUpdated (int statisticsType, HashMap < IStatistics, Object > map)

This method is called whenever statistics are updated and sent by NexPlayer.

The time interval at which general and system statistics are updated in *NexStatisticsMonitor* can be
changed by calling the *setDuration()* method.

<table>
<tr>
  <th>Name</th>
  <th>Description</th>
 </tr>
<tr>
  <th rowspan="5">statistics Type</th>
</tr>
  <tr><td><b>STATISTICS_GENERAL</b>= 0, for general playback statistics</td></tr>
  <tr><td><b>STATISTICS_INITIAL</b>= 1, for initial statistics when playback starts</td></tr>
  <tr><td><b>STATISTICS_HTTP</b>= 2, for HTTP statistics during playback</td></tr>
  <tr><td><b>STATISTICS_SYSTEM</b>= 3, for system statistics during HLS, DASH, or SS playback</td></tr>
</table>

| Name | Description                                   |
|------|---------------------------|
| map  | The updated statistics object as a *HashMap*. |

### NexStatisticsMonitor.MediaType Enum

An enumeration defining the possible types of HLS, DASH, or SS media can be played by NexPlayer.

These media types include:

- `NONE= 0` : No media file found.
- `AUDIO = 1` : Audio content.
- `BASEVIDEO = 2` : Base video content.
- `TEXT = 4` : Text content or subtitles.
- `ENHANCEDVIDEO = 8` : Enhanced video content.

**See Also**

 
- GeneralStatistics
- isMediaExist( MediaType mediaType, int mediaComposition )
 

#### int getCode ( )

Gets the integer code for the `MediaType`.

**Returns**

The integer code for the specified `MediaType`.
 
 
#### static boolean isMediaExist (MediaType mediaType,int mediaComposition)

This method indicates whether or not the requested media exists in the current content.

This method can be used to check if the current content contains the specific media (*AUDIO,BASEVIDEO,TEXT,ENHANCEDVIDEO*) based on the *mediaComposition* value received.

**Parameters**

 
| Name              | Description|
|-------------------|-----------------|
| mediaType         | The type of media to check. This will be one of: <br/>•*AUDIO* (0x00000001): for audio media. <br/>•*BASEVIDEO* (0x00000002): for base video. <br/>•*TEXT* (0x00000004): for text or subtitles. <br/>•*ENHANCEDVIDEO* (0x00000008): for enhanced video. |
| mediaComposition | The composition of the specified media, as an integer.|

**Returns**
 
*TRUE* if the media indicated exists, or *FALSE* if it does not exist in the current content.
