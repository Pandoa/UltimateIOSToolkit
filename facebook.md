# Facebook - Mediation
This section contains information on how to use Facebook as a mediation partner.

## Enabling Facebook Mediation
First, we need to enable Facebook Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableFacebookMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/android/mediation/facebook#step_1_set_up_facebook_audience_network) 
to create and configure a Facebook account.


## Additional Facebook Settings
### Methods
The following methods are available to customize Facebook settings:

|C++|Blueprints|Description|
|:----|:-----|:-----|
|`UFacebookLibrary::SetIsAgeRestrictedUser()`| `Set Is Age Restricted User`| Sets if the user is age restricted.|
|`UFacebookLibrary::InitializeFacebookSDK()`| `Initialize Facebook SDK`| Initializes the Facebook SDK with your SDK key.|
### Config
The followin configuration key are available to customize Facebook settings:
```ini 
[AdsPro.Mediation.Facebook]
MuteAudio=true ; If we want to mute audio for ads.
```

## GDPR
Please review Facebook's [guidance](https://www.facebook.com/business/gdpr) for information about GDPR and Facebook advertising.
