# Get Started

This section contains steps required to use the plugin. You can still use the plugin if you don't follow them but will only have test ads and default configuration.

## Creating an AdMob account
> [Official documentation page](https://support.google.com/admob/answer/7356219) for account creation.  

To create an AdMob account:
1. Go to https://apps.admob.com.
2. Click Sign up with your Google Account to sign up with an existing Google Account or click Create a new Google Account if you want to create a new account. Follow the on-screen prompts.
3. Complete the account information to create your new AdSense and Google Ads accounts:  
4. Check the checkbox to confirm that you've read and agree to the program policies, AdSense Terms & Conditions, and Google Ads Terms & Conditions.
5. Click Create AdMob account.

## Set up an app in AdMob
> [Official documentation page](https://support.google.com/admob/answer/9989980) for account creation.  

1. Sign in to your AdMob account at https://apps.admob.com.
2. Click Apps in the left sidebar.
3. Click Add app.
4. Select the platform of your app (Android or iOS). 
5. Select Yes, if it is listed on a supported app store.
6. Click Continue.

## Getting the Application ID

To make the plugin use your newly created application, we need to get the generated Application ID.

1. Go to https://apps.admob.com/.
2. Click Apps in the left sidebar.
3. Click the newly created application.
4. Click App Settings in the left sidebar.
5. In the middle of the screen, copy the Application ID by clicking on <img src="https://github.com/Pandoa/AdsPro/blob/main/_images/GetApplicationId.png?raw=true" height="25px" style="position:relative;top:8px"/>.
7. Open (or create it if it doesn't exist) the file `<YourProject>/Config/DefaultEngine.ini` in your favorite text editor.
8. Add the Application ID previously copied for the desired platform with the following structure:
```ini
[AdsPro]
AndroidAdMobAppID=ca-app-pub-XXXXXXXXXXXXXXXXXXX~XXXXXXX ; For Android
iOSAdMobAppID=ca-app-pub-XXXXXXXXXXXXXXXXXXX~XXXXXXX     ; For iOS
```
9. Save and close the file `DefaultEngine.ini`.

!> All settings can be edited in the Editor by going to `Project Settings` > `Plugins` > `AdsPro`.  

!> After doing this step, make sure to *always* use test ads during development or your account might be flagged and suspended if you don't.

> If this step is skipped, a test Application ID is automatically used. It will only show test ads.

## Enabling Test Ads

?> If you use your own Application ID, skipping this part might result in your AdMob account being flagged and suspended.

Test ads must be used during development. To do so, there exists three methods.

### Demo ad units
The quickest way to enable testing is to use Google-provided demo ad units. 
These ad units are not associated with your AdMob account, so there's no risk of your account generating invalid traffic when using these ad units.

<div style="margin-left:50%;left:-25%;position:relative">

|Ad Format|Sample ad unit ID|
|:----|:----|
|App Open|`ca-app-pub-3940256099942544/3419835294`|
|Banner View|`ca-app-pub-3940256099942544/6300978111`|
|Interstitial Ad|`ca-app-pub-3940256099942544/1033173712`|
|Rewarded Video|`ca-app-pub-3940256099942544/5224354917`|
</div>

### Add your test device in the AdMob UI
For a simple, non-programmatic way to add a test device and test new or existing app builds, use the AdMob UI.
1. Sign in to your AdMob account at https://apps.admob.com.
2. Click Settings in the sidebar.
3. Click the Test devices tab.
4. Click Add test device.  
5. Select the platform of your device.
6. Enter a device name. Consider using a name that will help you quickly identify your devices in your AdMob account.
7. Enter your Advertising ID/IDFA. How to find your advertising ID/IDFA [here](https://support.google.com/admob/answer/9691433). 
8. Select a gesture to use to activate ad inspector.
9. Click Done. 

### Add your test device programmatically
If you want to test ads in your app as you're developing, follow the steps below to programmatically register your test device.

1. Load your ads-integrated app and make an ad request.
2. Check the log output for a message that looks like the one below, which shows you your device ID.  
On Android:
```logcat
I/Ads: Use RequestConfiguration.Builder.setTestDeviceIds(Arrays.asList("33BE2250B43518CCDA7DE426D04EE231"))
to get test ads on this device.
```
On iOS:
```logs
<Google> To get test ads on this device, set:
GADMobileAds.sharedInstance.requestConfiguration.testDeviceIdentifiers =
@[ @"2077ef9a63d2b398840261c8221a0c9b" ];
```
3. Before loading any ads, call the C++ method `UAdMobLibrary::AddTestDeviceID(TEXT("33BE2250B43518CCDA7DE426D04EE231")))` or the equivalent Blueprint
node `Add Test Device ID`.
4. You can optionally check if it works correctly with the C++ method `UAdMobLibrary::IsTestDevice()` or the equivalent Blueprint node 
`Is Test Device`.
5. Re-run your app. If the ad is a Google ad, you'll see a Test Ad label centered at the top of the ad (banner, interstitial, or rewarded video):  

<div style="text-align:center">
<img src="https://developers.google.com/admob/images/android-testad-0.png" style="max-width:500px"/>
</div>

> Ads with this Test Ad label are safe to click. Requests, impressions, and clicks on test ads will not show up in your account's reports.
