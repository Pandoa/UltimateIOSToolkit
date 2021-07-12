# AdColony - Mediation
This section contains information on how to use AdColony as a mediation partner.

## Enabling AdColony Mediation
First, we need to enable AdColony Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableAdColonyMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/android/mediation/adcolony#step_1_set_up_adcolony) to create and configure an AdColony account.


## Additional AdColony Settings
The following methods are available to customize AdColony settings:

|C++|Blueprints|Description|
|:----|:-----|:-----|
|`UAdColonyLibrary::SetPopupOptions()`| `Set Popup Options`| Sets the popup options for AdColony.|


## GDPR
You can update the consent status with the C++ method `UAdColonyLibrary::SetGDPRPrivacyOptions()` or the equivalent Blueprint node `Set GDPR Privary Options`.