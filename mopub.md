# MoPub - Mediation
This section contains information on how to use MoPub as a mediation partner.

## Enabling MoPub Mediation
First, we need to enable MoPub Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableMoPubMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/ios/mediation/mopub#step_1_set_up_mopub) to create and configure a MoPub account.

## GDPR
You can update the consent status with the C++ method `UMoPubLibrary::SetHasUserConsent()` or the equivalent Blueprint node `Set Has User Consent`.


