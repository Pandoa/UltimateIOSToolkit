# IronSource - Mediation
This section contains information on how to use IronSource as a mediation partner.

## Enabling IronSource Mediation
First, we need to enable IronSource Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableIronSourceMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/ios/mediation/ironsource#step_1_set_up_ironsource) to create and configure an IronSource account.


## GDPR
You can update the consent status with the C++ method `UIronSourceLibrary::SetConsent()` or the equivalent Blueprint node `Set Consent`.
