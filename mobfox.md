# MobFox - Mediation
This section contains information on how to use MobFox as a mediation partner.

## Enabling MobFox Mediation
First, we need to enable MobFox Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableMobFoxMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/ios/mediation/mobfox#configure_mediation_settings_for_your_ad_unit) to create and configure a MobFox account.
