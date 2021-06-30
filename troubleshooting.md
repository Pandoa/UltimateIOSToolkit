# Troubleshooting
This section contains information on how to troubleshoot errors you might face when using the plugin.

## Getting Device Logs
Getting the device logs is the first step in understanding the problems. It contains usefull information on what's going on under the hood.
### Android
The following steps will help you get an Android device's logs.
1. Connect your device to your computer.
2. Open a terminal.
3. Run the following command:
```bash
adb logcat
```
> To clear the logs before reproducing the issue, you can run `adb logcat -c`.

### iOS
You can get the device's logs with the following steps:
1. Connect your iOS device to the Mac through USB.
2. Launch Xcode. Go to Windows > Devices and Simulators.
3. Click on Open Console.

## Getting Unreal Engine Logs
The following steps will help you to get the Unreal Engine logs of your device.
1. Connect your device to your computer.
2. In the Editor, launch your game on your external device.
3. In the top Editor toolbar, go to `Window` > `Developer Tools` > `Device Output Logs`.
4. Reproduce the issue.