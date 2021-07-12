# Verizon Media - Mediation
This section contains information on how to use Verizon Media as a mediation partner.

## Enabling Verizon Media Mediation
First, we need to enable VerizonMedia Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableVerizonMediaMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/android/mediation/VerizonMedia#step_1_set_up_VerizonMedia) to create and configure an VerizonMedia account.

## GDPR
You can update the consent status with the C++ method `UVerizonMediaLibrary::SetPrivacyData()` or the equivalent Blueprint node `Set Privacy Data`.