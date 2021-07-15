# Chartboost - Mediation
This section contains information on how to use Chartboost as a mediation partner.

## Enabling Chartboost Mediation
First, we need to enable Chartboost Mediation. 
1. Open `<Project>/Config/Engine.ini`.
2. Adds the following configuration:
```ini
[AdsPro.Mediation]
EnableChartboostMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/android/mediation/Chartboost#step_1_set_up_Chartboost) to create 
and configure a Chartboost account.


## Additional Chartboost Settings
### Methods
The following methods are available to customize Chartboost settings:

|C++|Blueprints|Description|
|:----|:-----|:-----|
|`UChartboostLibrary::StartWithAppId()`| `Start with App ID`| Starts the Chartboost SDK with an App ID and an App Signature.|

## GDPR
You can update the consent status with the C++ method `UChartboostLibrary::SetDataUseConsent()` or the equivalent Blueprint node `Set Data Use Consent`.