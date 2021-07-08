# Flurry - Mediation
This section contains information on how to use Flurry as a mediation partner.

## Enabling Flurry Mediation
First, we need to enable Flurry Mediation. 
1. Open `<Project>/Config/Engine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableFlurryMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/android/mediation/Flurry#step_1_set_up_Flurry) to create and configure an Flurry account.


## Additional Flurry Settings
The followin configuration key are available to customize Flurry settings:
```ini 
[AdsPro.Mediation.Flurry]
ServerParamLogEnabled=true 
```

