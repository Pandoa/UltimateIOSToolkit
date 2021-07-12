# MyTarget - Mediation
This section contains information on how to use MyTarget as a mediation partner.

## Enabling MyTarget Mediation
First, we need to enable MyTarget Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableMyTargetMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/ios/mediation/mytarget#step_1_set_up_the_mytarget_network) to create and 
configure a MyTarget account.


## Additional MyTarget Settings
The following methods are available to customize MyTarget settings:

|C++|Blueprints|Description|
|:----|:-----|:-----|
|`UMyTargetLibrary::SetUserAgeRestricted()`| `Set User Age Restricted`| Sets if the user is an age restricted user.|
|`UMyTargetLibrary::SetCcpaUserConsent()`| `Set CCPA User Consent`| Sets if we have the user's CCPA consent.|
|`UMyTargetLibrary::SetIabUserConsent()`| `Set IAB User Consent`| Sets if we have IAB user consent.|

## GDPR
You can update the consent status with the C++ method `UMyTargetLibrary::SetUserConsent()` or the equivalent Blueprint node `Set User Consent`.