# Vungle - Mediation
This section contains information on how to use Vungle as a mediation partner.

## Enabling Vungle Mediation
First, we need to enable Vungle Mediation. 
1. Open `<Project>/Config/Engine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableVungleMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/android/mediation/vungle#step_1_set_up_vungle) to create and configure a Vungle account.

## Additional Vungle Settings
The following configuration can be passed to Vungle:  

|Config Name| Default Value|
|:----|:----|
|Placements| |
|UserId| `test_user`|
|StartMuted| `false`|

These settings can be set as followed in `<Project>/Config/Engine.ini`:
```ini
[AdsPro.Mediation.Vungle]
Placements="Placement1,Placement2"
UserId="my_user_id"
StartMuted=false
```

## GDPR
You can update the consent status with the C++ method `UVungleLibrary::UpdateConsentStatus()` or the equivalent Blueprint node `Update Consent Status`.