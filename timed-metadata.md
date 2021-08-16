# Timed Metadata

You can listen to Timed Metadata events with NexPlayer Android SDK. ID3, EMSG DATA, and SCTE35 formats are supported.

## Setting Up The Listener

Timed metadata events are reported within the `onTimedMetaRenderRender` method of the `NexEventReceiver` class. This method is called when new timed metadata is ready. Timed metadata includes additional information about the playing content that may be displayed to the user and this information may change at different times throughout the content. Each time new metadata is available for display, this method is called.

**Parameters**

| Name      | Description                                                                                                    |
|-----------|--------|
| mp        | The NexPlayer object to which this event applies.                                                           |
| TimedMeta | An `NexID3TagInformation` object that contains the timed metadata associated with the content to be displayed. |

A sample implementation might look like below:

```java
mEventReceiver = new NexEventReceiver() {
@Override
public void onTimedMetaRenderRender(NexPlayer mp,  final NexID3TagInformation TimedMeta) {
	try {
		NexID3TagText text = null;
		
		text = TimedMeta.getArtist();
		if( text != null && text.getTextData() != null) {
			String str = new String(text.getTextData(), 0, text.getTextData().length,getTextEncodingType(text.getEncodingType()));
			NexLog.d(LOG_TAG, "Artist: " + str);
		}
	
		text = TimedMeta.getTitle();
		if( text != null && text.getTextData() != null) {
			String str = new String(text.getTextData(), 0,text.getTextData().length, getTextEncodingType(text.getEncodingType()));
			NexLog.d(LOG_TAG, "Title: " + str);
		}
	
		text = TimedMeta.getAlbum();
		if(text != null &&  text.getTextData() != null) {
			String str = new String(text.getTextData(), 0, text.getTextData().length, getTextEncodingType(text.getEncodingType()));
			NexLog.d(LOG_TAG, "Album: " + str);
		}
	
		text = TimedMeta.getLyric();
		if (text != null)  {
			String str = new String(text.getTextData(), 0, text.getTextData().length, getTextEncodingType(text.getEncodingType()));
			NexLog.d(LOG_TAG, "Lyric: " + str);
		}
		
		NexID3TagPicture picture = TimedMeta.getPicture();
		if( picture != null && picture.getPictureData() != null) {
			Bitmap bm = BitmapFactory.decodeByteArray(picture.getPictureData(),0, picture.getPictureData().length);
			NexLog.d(LOG_TAG, "ID3 Image decoded");
		}
	
		text = TimedMeta.getPrivateFrame();
		if (null != text) {
			String strPrivateFrame = new String(text.getTextData(), 0, text.getTextData().length, getTextEncodingType(text.getEncodingType()));
			NexLog.d(LOG_TAG, "TimedMeta PRIVATE FRAME: " + strPrivateFrame);
		}
	
		text = TimedMeta.getText();	
		if( text != null) {
			String strTextFrame = new String(text.getTextData(), 0, text.getTextData().length, getTextEncodingType(text.getEncodingType()));
			NexLog.d(LOG_TAG, "TimedMeta<1>: " + strTextFrame);
		}
	
		ArrayList<NexID3TagText> arrExtraData = TimedMeta.getArrExtraData();
	
		String str1 = "";
		String str2 = "";
	
		if (arrExtraData != null) {
			for (int i = 0; i < arrExtraData.size(); ++i) {
				NexID3TagText ID3ExtraData = arrExtraData.get(i);
				str1 = new String(ID3ExtraData.getTextData(), 0, ID3ExtraData.getTextData().length, getTextEncodingType(ID3ExtraData.getEncodingType()));
				str2 = new String(ID3ExtraData.getExtraDataID(), 0, ID3ExtraData.getExtraDataID().length, getTextEncodingType(ID3ExtraData.getEncodingType()));
	
				if (null != str1 && null != str2) {
					String strText = String.format("getExtraDataID : " + str2 + " getExtraData : " + str1);
					NexLog.d(LOG_TAG, "TimedMeta<2>: " + strText);
				}
			}
		}
	
	} catch (Throwable e) {
		NexLog.d(LOG_TAG, "Exception - onTimedMetaRenderRender() : " + e.getMessage() );
	}
}
}
mNexPlayer.addEventReceiver(mEventReceiver);
```

You can receive SCTE35 events with the `onDashScte35Event` callback from `NexEventReceiver`

```java
@Override
public void  onDashScte35Event(NexPlayer mp , NexEmsgData[] data) {
	final NexEmsgData[] datas;
	datas = data;

	NexLog.d(LOG_TAG,"[Scte35] onDashScte35Event is called. length: " + datas.length);
	for(int i=0;i<datas.length;i++) {
		StringBuilder sb = new StringBuilder();
		if (datas[i].mMessageData != null) {
			for (final byte b : datas[i].mMessageData) {
				sb.append(String.format("%02X", b & 0xff));
			}
		}
	
		
		NexLog.d(LOG_TAG, "[Scte35] (" + i + "/" + datas.length + ") id: " + datas[i].mId + ", eventTime: [" + datas[i].mStartTime + "-" + datas[i].mEndTime + "], " + "schemeIdUri: (" + datas[i].mSchemeIdUri + "), value: (" + datas[i].mValue + "), presentation_time: " + datas[i].mPresentationTime + ", duration: " + datas[i].mEventDuration + ", timescale: " + datas[i].mTimescale + ", messageData: " + datas[i].mMessageDataSize + "(" + sb.toString() + ")");
	}
}

}
```

## Properties

### TIMED_ID3\_META\_KEY (521)

Allows custom ID3 tags added to timed metadata in the content to be recognized and handled by NexPlayer.

When customized ID3 tags with additional information have been added to the timed metadata in the content, this property can be used to help NexPlayer recognize and pass those ID3 tags and the extra information they contain to an application.

Additional customized timed metadata will be saved as an ArrayList of NexID3TagText objects and can be retrieved by calling NexID3TagInformation.getArrExtraData.

This property must be set before NexPlayer.open is called.

- **Type:** String

- **Values:** a list of the customized ID3 tag names separated by semicolons (;)

- **Default:** nothing

**See Also**

- NexID3TagText.getExtraDataID
- NexID3TagInformation.getArrExtraData
- NexID3TagInformation.setArrExtraData

### ENABLE_ID3\_TTML (522)

Sets whether or not to display TTML text tracks in ID3 tags automatically when they are included in the content.

In this case, when both CEA closed captions and TTML text tracks in ID3 tags are included in the content, this property can be used to set whether to display the TTML text tracks in ID3 tags or the closed captions automatically.

By default, this property is set to 0 to disable TTML text tracks in ID3 tags automatically if they exist in the content (as was the behavior of NexPlayer previously). If for some reason it would be preferable that TTML captions in ID3 tag be displayed instead of the CEA closed captions text tracks, this property should be set to 1 using setProperty:

```java
mNexPlayer.setProperty(NexProperty.ENABLE_ID3_TTML, 1);
```

This property should only be called once, after calling init but before calling open.

!> Do not use with `PARTIAL_PREFETCH` property. 

- **Values:**

- 0 : TTML text tracks in ID3 tags ignored; CEA closed captions enabled
- 1 : TTML text tracks in ID3 tags enabled; CEA closed captions ignored

- **Default:** 0

### SEND_ALL\_DASH\_MPD\_EVENTS (605)

Set it to decide which events passed through `onDashScte35Event` listener.

This property should be called after init but before calling open.

- **Type:** int

- **Default:** 0

- **Values:**

- **0:** Only scte35 events will be passed through onDashScte35Event listener.
- **1:** All the events in the MPD will be passed through onDashScte35Event listener.


## API Reference


### NexEmsgData Class

This class contains information about an event message of the emsg box.

#### long mEndTime

The `mEndTime` provides the actual end time of event in the Media Presentation time.

It is expressed in Unix Epoch Time in milliseconds.

#### int mEventDuration

The `mEventDuration` provides the duration of event in media presentation time.

The value 0xFFFF indicates an unknown duration.

#### int mId

The `mId` is a field identifying this instance of the message.

Messages with equivalent semantics shall have the same value,

- i.e. processing of any one event message box with the same id is sufficient.

#### byte[] mMessageData

The `mMessageData` is body of the message, which fills the remainder of the message box.

This may be empty depending on the above information. The syntax and semantics of this field must be defined by
the owner of the scheme identified in the `mSchemeIdUri` field.

#### long mPresentationTime

ThemPresentationTime.

- If `mVersion` is 0, provides the Media Presentation time delta of the media presentation time of the event and the earliest presentation time in this segment. The timescale is provided in the `mTimescale` field.
- If `mVersion` is 1, provides the Media Presentation time of the event measured on the Movie timeline, in the timescale provided in the `mTimescale` field.

#### String mSchemeIdUri

The `mSchemeIdUri` used identifies the message scheme.

The semantics and syntax of the `mMessageData` are defined by the owner of the scheme identified.

For SCTE-35 event, the `mSchemeIdUri` is equal to "urn:scte:scte35:2013:bin", "urn:scte:scte35:2013:xml" and "urn:scte:scte35:2014:xml+bin".

#### long mStartTime

The `mStartTime` provides the actual start time of event in the Media Presentation time.

It is expressed in Unix Epoch Time in milliseconds.

### NexID3TagInformation Class

This class contains information about the metadata associated with the content, from sources such as ID3 tags.

This includes a series of text fields (the set of fields that actually contain information will vary depending on the format and which fields the content creator has filled in). These fields include information such as the album name, artist, lyrics, and so on.

This also includes the picture associated with the content, for formats such as MP3 and AAC that can have an optional associated still image, included as a `NexID3TagPicture` object.

This image is generally used in place of video for content that does not have video. The exact use of the still image is up to the content producer. In the case of an MP3 or AAC audio file, it is usually the album cover artwork. In the case of HTTP Live Streaming, audio-only tracks often have a still image to be shown in place of the video. This image may change during playback (for example, some audio-only HLS streams provide a new image every ten seconds or so).

When timed metadata is used with HLS content, the `NexID3TagInformation` object associated with the content will be updated each time new metadata is available during playback and should be updated accordingly.

#### ArrayList < NexID3TagText > getArrExtraData ( )

This method gets a list of customized ID3 tags and the extra data they contain included in the content timed metadata.

For the list of customized ID3 tags to be recognized and handled by NexPlayer, they should be set using the NexProperty *TIMED_ID3_META_KEY* after NexPlayer is initialized but before *NexPlayer.open* is called.

**Returns**


The customized ID3 tags and the additional data they contain as an ArrayList of `NexID3TagText` objects.

**See Also**


- `setArrExtraData`
- `TIMED_ID3_META_KEY`

#### NexID3TagText getComment ( )

This method gets the data included in the comment frame of the current content’s ID3 tags.

**Returns**

The comment frame data as a `NexID3TagText` object.

#### NexID3TagText getPrivateFrame ( )

This method gets the information included in private frames of the current content’s ID3 tags.

The private frames in ID3 tags are used to include additional information that is required by a program but can’t be
included in the other ID3 tag frames, and are tagged:

	<Header for ’Private frame’, ID: "PRIV">
	Owner identifier 	<text string> $00
	The private data 	<binary data>

Where the ’Owner identifier’ string includes contact information for the organization which is responsible for the
frame and its provided binary data.

NexPlayer merely passes the private frame information to the client application where it can be handled as desired.

#### NexID3TagText getText ( )

This method gets the data in the text frame included in the ID3 tags of the current content, if available.

**Returns**

The text frame data as a `NexID3TagText` object.

#### int getTimeCode ( )

This method gets the timestamp of timed metadata.

**Returns**

The timestamp of timed metadata in millisecond unit.

#### void setArrExtraData (ArrayList < NexID3TagText > ExtraData)

This method sets the list of customized ID3 tags and the extra data they contain included in the content timed metadata.

For the list of customized ID3 tags to be recognized and handled by NexPlayer, they should be set using the
NexProperty *TIMED_ID3_META_KEY* after NexPlayer is initialized but before *NexPlayer.open* is called.

**Parameters**

| Name      | Description                                                                                                  |
|-----------|------|
| ExtraData | The list of customized ID3 tags and the extra data they contain, as an ArrayList of `NexID3TagText` objects. |

**See Also**

- `getArrExtraData`
- `TIMED_ID3_META_KEY`

#### void setComment (NexID3TagText comment)

This method sets the information from the comment frame in the current content’s ID3 tags.

**Parameters**

| Name    | Description                                                |
|---------|--------------------|
| comment | The data in the comment frame as a `NexID3TagText` object. |

#### void setPicture (NexID3TagPicture picture)

This method sets the picture associated with the current content, if available.

This may be used as a still image to display in the event that video for particular content may not be displayed (due to network variability or perhaps an unsupported video codec is in use).

**Parameters**

| Name    | Description                                                            |
|---------|------------|
| picture | A `NexID3TagPicture` object containing the picture data and MIME type. |

#### void setPrivateFrame (NexID3TagText privateFrame)

This method sets the information included in private frames of the current content’s ID3 tags.

**See Also**


- `getPrivateFrame` for more information.

#### void setText (NexID3TagText text)

This method sets the text frame data in this class.

**Parameters**

| Name | Description                                      |
|------|----------|
| text | The text frame data as a `NexID3TagText` object. |

### NexID3TagPicture Class

This class allows NexPlayer to handle picture information included in timed metadata ID3 tags.

NexPlayer passes an instance of this class whenever new picture information for the current content is received from its ID3 tags and is included in an updated `NexID3TagInformation` object.

#### byte[] getPictureData ( )

This method gets the picture data associated with current content from the content’s timed metadata ID3 tags.

**Returns**

A byte array of the picture data.

#### NexID3TagText getMimeType()

This method gets the MIME type of the picture associated with the current content (from the content’s timed metadata ID3 tags).

### NexID3TagText Class

This class determines the encoding of text data included in the content ID3 tags.

**Public Member Functions**

- `int getEncodingType ()`
    
    This method gets the encoding type of text included in the content ID3 tags.
- `String **getEncodingTypeName** ()`
- `byte[ ] getTextData ()`
    
    This method gets the text data included in the content ID3 tags.
- `byte[ ] getExtraDataID ()`
    
    This method gets the customized ID3 tags of the extra data added to content timed metadata so they can be passed to the app.

#### int getEncodingType ( )

This method gets the encoding type of text included in the content ID3 tags.

**Returns**

The encoding type of the text.

#### byte[] getExtraDataID ( )

This method gets the customized ID3 tags of the extra data added to content timed metadata so they can be passed to the app.

?> This method can only be used if the customized ID3 tag names have already been set using the NexProperty *TIMED_ID3_META_KEY*.

**Returns**

The customized ID3 tags as a byte array, or *null* if *TIMED_ID3_META_KEY* has not been set.

**See Also**

- `TIMED_ID3_META_KEY`

#### byte[] getTextData ( )

This method gets the text data included in the content ID3 tags.

**Returns**

The text data as an array.

- `ENCODING_TYPE_ASCII` = 0x20000000
- `ENCODING_TYPE_ISO_8859` = 0x30000000 
- `ENCODING_TYPE_ISO_8859_1` = 0x30000010
- `ENCODING_TYPE_UNICODE` = 0x10000000 
- `ENCODING_TYPE_UNKNOWN` = 0x00000000
- `ENCODING_TYPE_UTF16` = 0x10000020 
- `ENCODING_TYPE_UTF16_BE` = 0x10000030 
- `ENCODING_TYPE_UTF32` = 0x10000040 
- `ENCODING_TYPE_UTF32_BE` = 0x10000050 
- `ENCODING_TYPE_UTF8` = 0x10000010 
