# Closed Captions

The NexPlayer supports a variety of subtitle formats including:

1. Local subtitle files (.srt/.smi/.sub)
2. 3GPP and CFF (TTML) timed text
3. CEA 608 closed captions
4. CEA 708 closed captions
5. Web Video Text Tracks (WebVTT)

?> In content where both CEA 608/708 closed captions and WebVTT text tracks exist, NexPlayer will automatically display the WebVTT text cues but this can be changed by setting the NexProperty. `ENABLE_WEBVTT` to 0 with setProperty.

### Local Subtitles

For subtitles, the path of the subtitle file or the URL to load the subtitle file should be passed to the player in the *smiPath* parameter of NexPlayer.open when content is opened. When streaming content contains subtitles, however, this *smiPath* should be set to *null* to avoid undefined behavior.

?> Only use NexPlayer.open to load local subtitles.

### Support for Other Caption Formats

Different subtitle formats also require different rendering, which is possible with the classes **NexCaptionRenderer**, **NexCaptionRendererForTimedText**, **NexEIA708CaptionView**, and **NexCaptionRendererForWebVTT**

## Rendering Captions with NexCaptionPainter

The NexCaptionPainter renders a variety of subtitle formats including:

1. Local subtitle files (.srt/.smi/.sub)
2. Timed text markup language (TTML)
3. CEA 608 closed captions
4. CEA 708 closed captions
5. Web Video Text Tracks (WebVTT)

#### Using NexCaptionPainter

NexCaptionPainter always needs to know the video output size in the application so that the subtitles can be correctly positioned. If a change in the video size is produced, that information should be notified to NexCaptionPainter. 

When caption data is received on NexPlayer#onTextRenderRender, it should be passed to NexCaptionPainter by calling the `setDataSource` method.

When it is necessary to clear captions from the screen, for example when seeking or stopping content, the **clear** method will remove existing captions on the screen.

`setUserCaptionSettings` will be helpful to make your own caption styles.

When a caption renderer is in use, it always needs to know the video output size in the application so that subtitles can be correctly positioned. This means that when the video changes size, that information should also be passed to the relevant caption renderer. Please see the relevant caption renderers for additional details on which methods to use to implement each kind of subtitles.

Lastly, note that in the case of CEA 608 closed captions, both `setOutputPos` and `setRenderArea` should be called when implementing the captions.

## Properties

### CAPTION_WAITOPEN (540)

Avoids waiting for the first Caption segment to download when starting to play content.

This property can be used when playing Caption content. By default, NexPlayer waits until the first Caption segment is downloaded before the content begins to play so that no caption text will be missed.

However, if this property is disabled (set to 0), the player will start playing content as soon as possible (instead of waiting until the first Caption segment is fully downloaded). This may be preferred if content should start playing as quickly as possible (although the initial Caption may be missed).

This property should be called once, immediately after calling init but before calling open.

- **Default:** 1

- **Values:**

- **0:** Content starts playing before the first Caption segment is downloaded.
- **1:** Content starts playing after the first Caption segment is downloaded.

### ENABLE_CEA708 (517)

Enables rendering and display of CEA 708 closed captions in content when available.

While CEA 608 closed captions are always enabled, it is necessary to set this property to 1 in order for NexPlayer to support CEA 708 closed captions.

In the case where content contains both CEA 608 and CEA 708 closed captions and this property enables CEA 708 closed captions, the application will have to handle choosing which captions to render and display to the user.

- **Values:**

- **0:** CEA 708 closed captions disabled.
- **1:** CEA 708 closed captions enabled.

- **Default:** 0 

### ENABLE_ID3\_TTML (522)

Sets whether or not to display TTML text tracks in ID3 tags automatically when they are included in the content.

In this case, when both CEA closed captions and TTML text tracks in ID3 tags are included in the content, this property can be used to set whether to display the TTML text tracks in ID3 tags or the closed captions automatically.

By default, this property is set to 0 to disable TTML text tracks in ID3 tags automatically if they exist in content (as was the behavior of NexPlayer previously). If for some reason it would be preferable that TTML captions in the ID3 tag be displayed instead of the CEA closed captions text tracks, this property should be set to 1 using setProperty:

```java
mNexPlayer.setProperty(NexProperty.ENABLE_ID3_TTML, 1);
```

This property should only be called once, after calling init but before calling open.

!> Do not use with `PARTIAL_PREFETCH` property. 

- **Values:**

- 0 : TTML text tracks in ID3 tags ignored; CEA closed captions enabled
- 1 : TTML text tracks in ID3 tags enabled; CEA closed captions ignored

- **Default:** 0

### ENABLE_WEBVTT (518)

Sets whether or not to display WebVTT text tracks automatically when they are included in the content.

In the case when both CEA 708 closed captions and WebVTT text tracks are included in the content, this property can be used to set whether to display the WebVTT text tracks or the closed captions automatically.

By default, this property is set to 1 to enable WebVTT text tracks automatically if they exist in content (as was the behavior of NexPlayer previously). If for some reason it would be preferable that CEA 708 closed captions be displayed instead of the WebVTT text tracks, this property should be set to 0 with by with setProperty:

```java
mNexPlayer.setProperty(NexProperty.ENABLE\_WEBVTT, 0);
```

This property should only be called once, immediately after calling init but before calling open.

- **Values:**

- 0 : WebVTT text tracks ignored; CEA 708 closed captions enabled
- 1 : WebVTT text tracks enabled; CEA 708 closed captions ignored

- **Default:** 1 (WebVTT text tracks enabled)
 
### IGNORE_CARRIAGERETURN\_WHEN\_RECEIVE\_ROLLUP (511)

Ignores the Roll Up (RU) column reset command in CEA 608 closed captions.

Because CEA 608 closed captions support the Roll Up (RU) mode, the player starts displaying captions "rolling up" the screen after receiving the Roll Up(RU) command.

The RU command can however have two meanings according to the specifications. One indicates the start of Roll Up mode. The other indicates that the line should be erased and the prompt(cursor) moved to the left-hand edge of the display (to prepare for a new caption).

In the event that some content contains many extra RU commands in the stream, captions may not be displayed properly because they will not be displayed fully and will be continuously erased from the screen.

If this property is enabled, NexPlayer will ignore the extra RU column reset commands and thus will not erase the affected line or move the cursor.

- **Type:** unsigned int

- **Default:** 0

- **Values:**

- 0 : Disabled. CEA 608 closed captions will be displayed according to the specifications.

- 1 : Enabled. Roll Up column reset commands in CEA 608 closed captions will be skipped.


### IGNORE_CEA608\_TEXTMODE\_COMMAND (514)

Allows NexPlayer to ignore the text-mode command in CEA608 closed captions.

This property may be useful in cases where CEA 608 closed captions have been implemented in ways other than strictly following the standard specifications which include extra text mode commands. It allows NexPlayer to properly display those alternatively implemented captions in video content.

In content that includes standard CEA 608 closed captions that follow the specifications, enabling this property may result in captions that do not appear as expected, so use of this property is discouraged in those cases as NexPlayer will properly display CEA 608 closed captions according to the specifications.
 
- **Type:** unsigned integer

- **Default:** 0

- **Values:**

- **0:** Disabled. NexPlayer will display CEA 608 closed captions according to the specifications.
- **1:** Enabled. NexPlayer will ignore the text mode command when displaying CEA 608 closed captions.

### MAX_CAPTION\_LENGTH (901)

Set it to extend max caption length.

This property should be called after init but before calling open.

- **Type:** int

- **Default:** 8192

### SET_STOP\_TEXT\_DOWNLOAD (910)

If set to 1, when setting the text media stream (`setMediaStream` API) with `MEDIA_STREAM_DISABLE_ID`, the subtitles won't be downloaded. To show the subtitles without any delay, you should restart the playback without this property. 

If set to 0, the subtitles won't be shown when using `MEDIA_STREAM_DISABLE_ID` but they will be downloaded in the background.

- **Type:** int

- **Default:** 0

> Since version 6.72.0.862

## API Reference

### NexPlayer.changeSubtitleFD

```java
int changeSubtitleFD (FileDescriptor fd, long offset, long length)
```

Open the caption resource file which is attached in "res/raw" or "assets" folder.

Length and Offset can be acquired from the UI. This API should be called after start() is completed.

**Parameters**

| Name | Description | 
|---|---|
| fd | file descriptor|
| offset | Offset |
| length | length | 

**Returns**
 
The status of the operation: this is zero in the case of success, or a non-zero NexPlayer error code in the
case of failure.
 
?> When building the APK, most of resources will be compressed. This makes it difficult to extract FileDescriptor. To avoid compressing, you MUST change your file’s extension. These extensions are allowed: ".jpg", ".jpeg", ".png", ".gif", ".wav", ".mp2", ".mp3", ".ogg", ".aac", ".mpg", ".mpeg", ".mid", ".midi", ".smf", ".jet", ".rtttl", ".imy", ".xmf", ".mp4", ".m4a", ".m4v", ".3gp", ".3gpp", ".3g2", ".3gpp2", ".amr", ".awb", ".wma", ".wmv"
 
### NexPlayer.changeSubtitlePath

```java
int changeSubtitlePath (String path)
```

This method allows the subtitle file for particular content to be changed during playback.

A new subtitle file can be loaded from the device’s storage or from a given URL as passed in the parameter path. For example, the user can change the subtitles to a different language while playing the particular content.

**Parameters**

| Name | Description | 
|---|---|
| path | The path to the new subtitle file to use or the URL to load the new subtitle file from. |

**Returns**

Zero if successful or a non-zero error code.


### NexPlayer.setCaptionLanguage

```java
native int setCaptionLanguage (int indexOfCaptionLanguage)
```

This method selects a caption (subtitle) track that will be used.

Subtitles for the selected track will be passed to onTextRenderRender for display.

This is used for file-based captions only. For streaming media with included captions,setMediaStream()
should be used instead, and local captions should be turned off since running both types of captions at the same time has undefined results.

**Parameters**

| Name                   | Description                                                                                                                                                                                         
|----|----------------------------------|
| indexOfCaptionLanguage | An index into the mCaptionLanguages array specifying which language to use. If there are n entries in the caption array, then you may pass 0 ...n-1 to specify the language, n to turn off captions. |

**Returns**
 
Zero if successful, non-zero if there was an error.
 
### NexPlayer.setCEA608CaptionChannel

```java
native int setCEA608CaptionChannel ( int nChannel)
```

Sets the input channel for CEA 608 closed captions.

This method will be one of four available channels. Setting the input channel to zero will also disable or turn off CEA 608 closed captions if they are present.

When viewing content including CEA 608 closed captions, it is important to choose whether to have the application support them in BASIC or FULL mode with the property SET\_CEA608\_TYPE. In order to meet CEA 608 closed caption specifications completely, the closed captions should be displayed in the FULL mode. If BASIC mode is selected, the closed captions will be treated similar to other subtitles and may not always be accurately displayed (or may be difficult for a user to read) depending on the display attributes used in the closed captions.

When supporting CEA 608 closed captions in BASIC mode, setting the input channel to any number between 1 and
4 merely enables and displays the captions.

Since CEA 608 closed captions may include different information on the available input channels, the desired input channel may be selected in FULL mode by choosing the relevant channel number (1, 2, 3, or 4).

**Parameters**

| Name | Description | 
|---|---|
|nChannel| This will be an integer from 0 to 4. If it is zero, the closed captions will be disabled. When using CEA 608 captions in BASIC mode, 1 to 4 simply enable the captions. When using CEA 608 captions in FULL mode, 1 to 4 chooses the input channel to be displayed as closed captions.|

**Returns**
 
Zero if successful or a non-zero error code.

### NexEventReceiver.onTextRenderInit
 
```java
void onTextRenderInit( NexPlayer mp, int numTracks )
```
 
Called when initially beginning playback of media content with associated subtitles.
 
**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.|
| numTracks | The number of subtitle tracks available for this media. Note that this may be 0 if there are no subtitles, or this function may not be called at all.|

### NexEventReceiver.onTextRenderRender

```java
void onTextRenderRender( NexPlayer mp, int trackIndex, NexClosedCaption textInfo )
```
 
This function is called when new subtitle data is ready for display. This is called whenever playback reaches a point in time where subtitles on any track need to be displayed or cleared. The text to display is provided in a NexClosedCaption object as a byte array; it is the responsibility of the application to convert this to text with the appropriate encoding. Where possible, the encoding information will be provided in the NexClosedCaption.mEncodingType, but many subtitle file formats do not explicitly specify an encoding, so it may be necessary for the application to guess the encoding or allow the user to select it. 

**Parameters**

| Name  | Description  | 
|---|---|
| mp | The NexPlayer object to which this event applies.|
| trackIndex | This is always zero and should always be ignored.|
| textInfo | The text to be displayed (cast this to a NexClosedCaption object).|

### NexClosedCaption Class

This class handles the subtitles and closed captions data of content.

NexPlayer uses this class to handle SMI, SRT, SUB, and Smooth Streaming subtitles as well as CEA 608 and CEA 708 closed captions included in HLS content, 3GPP and CFF timed-text as well as WebVTT text tracks.

?> Certain methods though may only be called to handle specifically CEA 608 closed captions, CEA 708 closed captions, timed text, or WebVTT text tracks, so care must be taken when implementing support for those captions.

Text information from standard subtitle files (SMI, SRT, SUB, and Smooth Streaming subtitles) is handled by the getTextData method while the text of CEA 608 close captions, 3GPP timed text, and WebVTT captions must each be handled separately by, respectively, getString, getTextDataFor3GPPTT, and getTextDataForWebVTT. In the case of CFF timed text (TTML), text data is handled separately by the getTextDataforTTML method.

For CEA 708 closed captions, please see NexEIA708Struct and NexEIA708CaptionView.

The instance of NexClosedCaption is delivered through the onTextRenderRender method for regular subtitles.

When timed text, CEA 608 closed captions, or WebVTT are implemented, it is necessary to create and display the captions in a separate caption renderer, like NexCaptionRendererForTimedText, NexCaptionRenderer, and. For example, CEA 608 captions can be displayed one character at a time and thus the position of each character must be considered. The vertical position of each character is set by a row number, rowbetween 0 and 15, while the horizontal position of the character is set by a column number, colbetween 0 and 32. NexPlayer.IListener.onTextRenderRender, NexCaptionRenderer, NexEIA708Struct, NexEIA708CaptionView, NexCaptionRendererForTimedText, and NexCaptionRendererForWebVTT for additional details.

### NexCaptionPainter Class

This class defines the caption renderer view and displays the information to the user.

In order to support all of the text attributes and display options of the CEA 608 / CEA 708 / WebVTT / TTML / SMI / SRT / SUB specifications, it is necessary to create a Caption Renderer view with the `NexCaptionPainter` class.

The `NexCaptionPainter` view is overlaid on the application’s video output, and as a result, whenever the video display changes, the `NexCaptionPainter` must also be updated in order for captions to be accurately displayed.

In particular, the `NexCaptionPainter` in an application requires the following information:

- Rendering Area Information: Whenever the video output in an application UI changes its size or the orientation changes, the new size information should also be passed to the `NexCaptionPainter`class by calling the `NexCaptionPainter.setRenderingArea` method.
- New Caption Data: Whenever new caption data is received, it should be passed to the `NexCaptionPainter` by calling the `NexCaptionPainter.setDataSource` method.

When it is necessary to clear captions from the screen, for example when seeking in or stopping content, calling the `NexCaptionPainter.clear` method will remove the captions existing on the screen.

When you want to set attributes to the captions, the `NexCaptionSetting` should be passed to `NexCaptionPainter` by calling the `NexCaptionPainter.setUserCaptionSettings` method.

### NexCaptionRenderer Class

This class defines the CEA 608 Closed Caption renderer view and displays the information to the user.

In order to support all of the text attributes and display options of the CEA 608 specifications, it is necessary to create a separate Caption Renderer view with the `NexCaptionRenderer` class.

The` NexCaptionRenderer` view is overlaid on the application’s video output, and as a result, whenever the video display changes, the `NexCaptionRenderer` must also be updated in order for captions to be accurately displayed.

In particular, the `NexCaptionRenderer` in an application requires the following information:

- Video Size Information: Whenever the video output in an application’s UI changes size or orientation changes, the new size information should also be passed to `NexCaptionRenderer` by calling the `NexCaptionRenderer.setRenderArea` method.
- New CEA 608 closed caption Data: Whenever new CEA 608 closed caption data is received, it should be passed to the `NexCaptionRenderer` by calling the `NexCaptionRenderer.SetData` method.

When it is necessary to clear CEA 608 closed captions from the screen, for example when seeking in or stopping content, calling the `NexCaptionRenderer.makeBlankData` method will erase captions existing on the screen.

This class should only be used when displaying CEA 608 closed captions, not other kinds of subtitles.

To display CFF and 3GPP timed text, please use `NexCaptionRendererForTimedText`.
 
### NexCaptionPreview Class

This class defines the look of a caption preview renderer so that a preview of captions may be displayed to the user.

This class can be used as a preview of user selections, to show how captions will be rendered on screen during playback when different attributes such as caption window, background, text color, and edge effect have been set by the user.

This preview can be used for any format of captions.
 
### NexCaptionRendererForTimedText Class

This class defines the renderer view for CFF and 3GPP timed text subtitles in content and displays them.

In order for NexPlayer to display CFF or 3GPP timed text, a separate Caption Renderer view must be created with the `NexCaptionRendererForTimedText` class.

In particular, in order to use `NexCaptionRendererForTimedText`, care must be taken to do the following:

1. **Pass Video Size Information** : Since the `NexCaptionRendererForTimedText` view is overlaid on the video display in an application, information about the video display must be passed to the caption renderer for timed text to be properly displayed. This means that when the video output size in the application UI is set or changes (including when the video surface is first created), `NexCaptionRendererForTimedText` should also be notified. To do so, the following two methods should be called:
    - `setScaleRatio`: When the video is scaled up (for example to fit-screen or full-screen), pass the scale ratio to `NexCaptionRendererForTimedText` with this method.
	- `setVideoSizeInformation`: To fit the text render area within the video, `NexCaptionRendererForTimedText` also needs to know the video size and position information provided by calling this method.
2. **Pass Timed Text Data to the Renderer** : Whenever timed text is updated, the new timed text data must be passed to `NexCaptionRendererForTimedText`. To do this:
	- (a) When calling `onTextRenderRender`, the text type must be checked by calling `NexClosedCaption.getTextType`.
	- (b) If that method returns TEXT\_TYPE\_TTML\_TIMEDTEXT for CFF timed text or TEXT\_TYPE\_3GPP\_TIMEDTEXT for 3GPP timed text, pass a `NexClosedCaption` object with the new timed text data to
`NexCaptionRendererForTimedText` with the `setData(NexClosedCaption data)` method.
	- (c) Finally, call the NexCaptionRendererForTimedText.invalidate method when updating the captions.
3. **Clear Timed Text on the Screen** : Whenever timed text must be cleared from the screen (for example when
    seeking or stopping content), calling clear and invalidate will `clear` any existing text from the device screen.

To display CEA 608 closed captions however, please use `NexCaptionRenderer`.

### NexCaptionRendererForWebVTT Class

This class defines the renderer view for Web Video Text Tracks (WebVTT) text tracks in HLS content and displays them.

In order for NexPlayer to display WebVTT, a separate Caption Renderer view must be created with the `NexCaptionRendererForWebVTT` class.

In particular, in order to use `NexCaptionRendererForWebVTT`, care must be taken to do the following:

1. **Pass Video Size Information** : Since the `NexCaptionRendererForWebVTT` view is overlaid on the video display in an application, information about the video display must be passed to the caption renderer for the WebVTT text to be properly displayed. This means that when the video output size in the application UI is set or changes (including when the video surface is first created), `NexCaptionRendererForWebVTT` should also be notified. To do so, the following two methods should be called:
    - `setScaleRatio`: When the video is scaled up (for example to fit-screen or full-screen), pass the scale ratio to `NexCaptionRendererForWebVTT` with this method.
    - `setVideoSizeInformation`: To fit the text render area within the video, `NexCaptionRendererForWebVTT` also needs to know the video size and position information provided by calling this method.
2. **Pass Caption Data to the Renderer** : Whenever WebVTT text is updated, the new caption data must be passed to `NexCaptionRendererForWebVTT`. To do this:
	- (a) When calling `onTextRenderRender`, the text type must be checked by calling `NexClosedCaption.getTextType`.
	- (b) If that method returns TEXT\_TYPE\_WebVTT for WebVTT text, pass a NexClosedCaption object with the new WebVTT text data to NexCaptionRendererForWebVTT with the `setData(NexClosedCaptiondata)` method.
	- (c) Finally, call the `NexCaptionRendererForWebVTT.invalidate` method when updating the captions.
 
3. **Clear the Text on the Screen** : Whenever WebVTT text must be cleared from the screen (for example when seeking or stopping content), calling clear and invalidate will `clear` any existing text from the device screen.

To display CEA 608 closed captions, CEA 708 closed captions, or timed text (CFF or 3GPP) however, please use the relevant caption renderers, namely one of `NexCaptionRenderer`, `NexEIA708CaptionView`, or `NexCaptionRendererForTimedText`.
  
### NexCaptionWindowRect Class

This class manages the position of captions for NexCaptionSetting.

### NexCaptionSetting Class

This class manages the attributes of the captions for `NexCaptionPainter`.

### NexCaptionWindowRect Class

This class manages the position of captions for NexCaptionSetting.
