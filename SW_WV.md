# Software Widevine integration with NexPlayerSDK for Android

## What is Software Widevine?

Software Widevine is a DRM technique that allows playing encrypted content on devices that don't support Media DRM. Software DRM module manages 
to decrypt the DRM-protected content received from the content server. This decryption will be done by using the common encryption standard algorithm (cenc).
In order to be able to decrypt the received segments, a license key is needed, which will be obtained from a license server.

## What is a license server?

Also known as endpoint server, which is responsible for managing and storing the key(s) that will be used for decrypting the content segments. A license server can hold a single key or multiples keys for both audio and video. NexPlayer SDK will obtain the key(s) that the SW DRM module will use in order to play the content.

## What is Widevine security level?

As commented before, DRM-protected content needs to be decrypted to be played.
At this point we need to know what security levels a device can support and how they work:

- L1: The most secure level. All cryptography operations are done in Trusted Execution Environment (TEE).
- L3: There is no TEE and decryption is handled by the OS.

However,  some of the devices don’t have Widevine support at all and not able to make the decryption. At this point, SW Widevine takes the action. Since those devices are not able to process the crypto operations within the OS, SW Widevine libraries will allow the device to be able to access those encrypted contents

## How to use SW Widevine with NexPlayer

NexPlayer provides the integration for SW Widevine through a dynamic library called libnexwvdrm.so, which needs to be placed in the libs folder. This software module will work with the information received through NexWVDRM.java.

Besides the library above, NexPlayer also provides NexWVDRM.java and NexWVDRMSession.java which will perform accordingly to the protected data and receiving/sending events from/to the libnexwvdrm.so.

In order to initialize the NexPlayer-SW Widevine module, the following steps needs to be made:

- Create a NexWVDRM object that will be used later:

    ```java   
    NexWVDRM mNexWVDRM = new NexWVDRM();
    ```
    
- Initialize SW Widevine module: 

  ```java
  nexWVDRM.initDRMManager(EnginePath, CertificatePath, KeyServerURL, offlineMode);
  mNexPlayer.setProperties(215, 2); // Specifies the drm mode to be used. In our case will be 2, which means SW Widevine.
  ```
  
  <table>
  <tr>
    <th>Name</th>
    <th colspan=3>Description</th>
  </tr>
  <tr>
    <td>EnginePath</td>
    <td>Will refer to the engine library ("libnexplayerengine.so") to verify that SW DRM is supported by the SDK.</td>
  </tr>
  <tr>
    <td>CertificatePath</td>
    <td>This is the path to store the key and authentication information received from the License server when Store/Retrieve play is performed.
    In the Offline state, it can not connect to the License Server and stores the received authentication information to a file.
    This information should be used only Widevine DRM module of the certified player inside because it is encrypted.</td>
  </tr>
  <tr>
    <td>KeyServerURL</td>
    <td>The license server url where the key/s needed for decrypting the content are stored.</td>
  </tr>
  <tr>
    <td rowspan=5>offlineMode</td>
  </tr>
  <tr><td>0: Online mode. NexPlayer will open a temporary DRM session, which does not store any session handles. Network connection is required.</td></tr>
  <tr><td>1: Storing mode. NexPlayer will open a permanent DRM session, and store it after opening it. Network connection is required.</td></tr>
  <tr><td>2: Retrieving mode. NexPlayer will find a stored DRM session, and then restore it.</td></tr>
  <tr><td>3: Storing + Retrieving mode. NexPlayer will find a stored DRM session. If it exists, then NexPlayer will restore it; if not, the engine will create a     new session and then store it. Network connection is required.</td></tr>
  </table>

  This API should be used before the NexPlayer.open() function call.
  
- NexWVDRM allows to get the license data from the request. (Optional. If not needed, set to null):
  
  ```java
   INexDRMLicenseListener licenseRequestListener = new INexDRMLicenseListener() {
 		@Override
 		public byte[] onLicenseRequest(byte[] requestData) {
 			final String LicenseServer = mCurrentExtraData;
 			Object response = null;
 			try {
 				response = NexHTTPUtil.executePost(LicenseServer, requestData, null);
 			} catch (IOException e) {
 			
 			}
 			return (byte[]) response;
 		}
  };
  nexWVDRM.setLicenseRequestListener(licenseRequestListener);
  ```
  This API should be used before the NexWVDRM.initDRMManager function call.
  
 - NexWVDRM allows sending headers within the license server request, in case they are needed to get the license key(s). (Optional):
 
    ```java
    HashMap<String, String>  optionalHeaders = new HashMap<>();

    String key1 = "test_header1";
    String value1 = "test_value1";
    String key2 = "test_header2";
    String value2 = "test_value2";

    optionalHeaders.put(key1, value1);
    optionalHeaders.put(key2, value2);

    nexWVDRM.setNexWVDrmOptionalHeaderFields(optionalHeaders);
    ```
   This API should be used before the NexWVDRM.initDRMManager function call.
   
-  NexWVDRM allows modifying they key when needed. If multiple keys are gotten from the license server, this call will be needed.
  
    ```java
    NexWVDRM.IWVDrmListener mWidevineDRMListener = mNexWVDRM.createWVDRMListener();
    mNexWVDRM.setListener(mWidevineDRMListener);
    ```
   This API should be used only if the initDRMManager function call has been successful.
   

## Things to consider

- License server needs to allow L3 security level. 
- NexPlayer SW Widevine libraries should be integrated.
