# NexPlayer Synchronization Feature

## How to enable synchronization feature?

NexPlayer synchronization can be enabled by setting the following property:

```
mNexPlayer.setProperty(NexPlayer.NexProperty.ENABLE_SPD_SYNC_TO_GLOBAL_TIME, 1);
```

For DASH, _suggestedPresentationDelay_ attribute is taken account for synchronising the playback. You should set the following property to set presentation delay on HLS as it is not supported by default in this protocol. 

```
mNexPlayer.setProperty(NexPlayer.NexProperty.SET_APPLS_PROGRAM_DATE_TIME_PRESENTATION_DELAY, 6000);
```


## Advanced configuration
You can control the synchronization behaviour further by adjusting the below properties


##### ENABLE\_SPD\_SYNC\_TO\_DEVICE\_TIME

Enables synchronization to device UTC for more accurate behaviour. 

```
mNexPlayer.setProperty(NexPlayer.NexProperty.ENABLE_SPD_SYNC_TO_DEVICE_TIME, 1);
```

Default: 0

Values:

- 0: Disabled device UTC
- 1: Enabled device UTC


##### SET\_SPD\_SYNC\_DIFF\_TIME

If the current playback is not more synchronized than this value, the player will speed up playback and make sync. 

```
mNexPlayer.setProperty(NexPlayer.NexProperty.SET_SPD_SYNC_DIFF_TIME, 100);
```


Unit: msec (1/1000 sec)

Default: 300 (300 msec)



##### SET\_SPD\_TOO\_MUCH\_DIFF\_TIME

If playback is out of sync than this value, the player will jump to synchronize the video rather than make it by speeding

```
mNexPlayer.setProperty(NexPlayer.NexProperty.SET_SPD_TOO_MUCH_DIFF_TIME, 5000);
```

Unit: msec (1/1000 sec) 

Default: 5000 (5 seconds)


## Things to consider

- You should make sure **suggestedPresentationDelay** is present in DASH manifest otherwise synchronisation won't work
- For HLS, you should set _SET\_APPLS\_PROGRAM\_DATE\_TIME\_PRESENTATION\_DELAY_ property as mentioned above
- You should make sure there is enough distance from the live edge to provide a smooth playback which should be adjusted with suggestedPresentationDelay and _SET\_APPLS\_PROGRAM\_DATE\_TIME\_PRESENTATION\_DELAY_ properties. If there is not enough space to buffer from the live edge, playback might be effected.

