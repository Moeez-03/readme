# Updates

We've made significant improvements to our project, focusing on enhancing the ecosystem and resolving major issues:

Ecosystem Updates:

Integrated WebSockets and created peer connections for a more robust Google ecosystem.

Developed functions for Google ecosystem cancellation, Google noise controller, and Google text noise controller.

Android Manifest Update:

Updated AndroidManifest.xml with new user permissions and features.
Incorporated Java techniques to resolve major errors, enhancing overall performance.
Error Resolution:

Focused on resolving ecosystem-related errors to ensure a seamless user experience.


## Websockets

Peer Connection
```bash
    public void createPeerConnectionWS() {
        // Configure audio constraints
        MediaConstraints audioConstraints = new MediaConstraints();
        audioConstraints.mandatory.add(new MediaConstraints.KeyValuePair("googEchoCancellation", "true"));
        audioConstraints.mandatory.add(new MediaConstraints.KeyValuePair("googNoiseSuppression", "true"));
        audioConstraints.mandatory.add(new MediaConstraints.KeyValuePair("googAutoGainControl", "true"));
        audioConstraints.mandatory.add(new MediaConstraints.KeyValuePair("googTypingNoiseDetection", "true"));

        // Pass constraints to the WebSocket interface
        myWebSocketCallbackInterface.createPeerConnectionFromInterface(audioConstraints);
    }

```

## AndroidManifest.xml

```python
<uses-permission android:name="android.permission.MANAGE_DEVICE_POLICY_LOCK_TASK" />

<receiver
    android:name=".MyDeviceAdminReceiver"
    android:permission="android.permission.BIND_DEVICE_ADMIN">
    <meta-data
        android:name="android.app.device_admin"
        android:resource="@xml/device_admin_receiver" />
    <intent-filter>
        <action android:name="android.app.action.DEVICE_ADMIN_ENABLED" />
    </intent-filter>
</receiver>

```

## SaplashScreen

```
DevicePolicyManager dpm = (DevicePolicyManager) getSystemService(Context.DEVICE_POLICY_SERVICE);
ComponentName adminComponent = new ComponentName(this, MyDeviceAdminReceiver.class);

if (dpm.isDeviceOwnerApp(getPackageName())) {
    dpm.setLockTaskPackages(adminComponent, new String[]{getPackageName()});
} else {
    Log.e("SplashScreenActivity", "App is not a device owner.");
}
```
```
```