# AppLovin - Mediation
This section contains information on how to use AppLovin as a mediation partner.

## Enabling AppLovin Mediation
First, we need to enable AppLovin Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableAppLovinMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/android/mediation/applovin#step_1_set_up_applovin) to create and 
configure an AppLovin account.


## Additional AppLovin Settings
### Methods
The following methods are available to customize AppLovin settings:

|C++|Blueprints|Description|
|:----|:-----|:-----|
|`UAppLovinLibrary::SetIsAgeRestrictedUser()`| `Set Is Age Restricted User`| Sets if the user is age restricted.|
|`UAppLovinLibrary::InitializeAppLovinSDK()`| `Initialize AppLovin SDK`| Initializes the AppLovin SDK with your SDK key.|
### Config
The following configuration key is available to customize AppLovin settings:
```ini 
[AdsPro.Mediation.AppLovin]
MuteAudio=true ; If we want to mute audio for ads.
```


## GDPR
You can update the consent status with the C++ method `UAppLovinLibrary::SetHasUserConsent()` or the equivalent Blueprint node `Set Has User Consent`.