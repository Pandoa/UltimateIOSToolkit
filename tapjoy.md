# Tapjoy - Mediation
This section contains information on how to use Tapjoy as a mediation partner.

## Enabling Tapjoy Mediation
First, we need to enable Tapjoy Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableTapjoyMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/android/mediation/Tapjoy#step_1_set_up_Tapjoy) to create and configure a Tapjoy account.


## Additional Tapjoy Settings
The following configuration key is available to customize Tapjoy settings:
```ini 
[AdsPro.Mediation.Tapjoy]
Debug=true ; If we want to enable debug mode.
```


## GDPR
You can update the consent status with the C++ method `UTapjoyLibrary::SetHasUserConsent()` or the equivalent Blueprint node `Set Has User Consent`.