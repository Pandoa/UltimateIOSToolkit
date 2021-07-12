# Nend - Mediation
This section contains information on how to use Nend as a mediation partner.

## Enabling Nend Mediation
First, we need to enable Nend Mediation. 
1. Open `<Project>/Config/DefaultEngine.ini`.
2. Add the following configuration:
```ini
[AdsPro.Mediation]
EnableNendMediation=true
```
3. Save and close the file.

!> On iOS, you will have to rebuild the plugin for the change to take effect.

> Make sure to follow [this guide](https://developers.google.com/admob/ios/mediation/nend#step_1_set_up_nend) to create and configure a Nend account.


## Additional Nend Settings
The following configuration key are available to customize Nend settings:
```ini 
[AdsPro.Mediation.Nend]
UserId="user_id" ; Your nend user id.
```

