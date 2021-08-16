# HTTP Request Modification

In order to modify an HTTP Request with NexPlayer :

1. Add the following code:

```java
mNexPlayer.setProperty(NexProperty.ENABLE_MODIFY_HTTP_REQUEST, 1);
```
	
After **init** but before calling **open** in order to set the property ENABLE\_MODIFY\_HTTP\_REQUEST to enabled.

2. The following override code must also be included for onModifyHttpRequest:

```java
@Override
public String onModifyHttpRequest(NexPlayer mp, int nRequestLength, Object in\_obj) {
	String strData = "";
	try {
		Log.d(LOG\_TAG, "HTTP\_REQUEST : requestLength :"+nRequestLength+".");
		strData = (String)in\_obj;
		Log.d(LOG\_TAG, "HTTP\_REQUEST DATA :" + strData);
		Log.d(LOG\_TAG, "HTTP\_REQUEST DATA SET END!!! strData.length:"+strData.length()+".");
		return strData;
	}
	catch(Exception e) {
		e.printStackTrace();
	}
	return strData;
}
```
See **onModifyHttpRequest** for more information.
