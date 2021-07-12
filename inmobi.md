# InMobi - Mediation
This section contains information on how to use InMobi as a mediation partner.

## Enabling InMobi Mediation
First, we need to enable InMobi Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableInMobiMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/ios/mediation/inmobi#step_1_set_up_inmobi) to create and configure an InMobi account.


## Additional InMobi Settings
The following methods are available to customize InMobi settings:

|C++|Blueprints|Description|
|:----|:-----|:-----|
|`UInMobiLibrary::SetLogLevel()`| `Set Log Level`| Sets the log level for InMobi.|
|`UInMobiLibrary::SetUserInformation()`| `Set User Information`| Sets the current user information.|


## GDPR
You can update the consent status with the C++ method `UInMobiLibrary::UpdateUserConsent()` or the equivalent Blueprint node `Update User Consent`.

