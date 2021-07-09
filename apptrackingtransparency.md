# iOS App Tracking Transparency
This section contains information on how to setup App Tracking Transparency for iOS.

## App Tracking Transparency Message
First, we need to define a message to be displayed to the user.
1. Open the file `<Project>/Config/DefaultEngine.ini`.
2. Add the following data:
```ini
[AdsPro]
EnableUserTrackingConsent=true
UserTrackingUsageDescription="Your message to request App Tracking Transparency."
```
3. Save and close the file.

> You can also enable it by going in the Editor to `Project Settings` > `Plugins` > `AdsPro`.

## Requesting Tracking
It's now time to request Tracking. For that, call the C++ method `UAppTrackingLibrary::RequestIdentifierForAdvertisers()` or the equivalent Blueprint node `Request Identifier for Advertisers`.
This method takes time to complete as it waits for the user choice. Once the user made the choice, one of the following values is returned:

- **Authorized**: The user authorizes access to app-related data for tracking the user or the device.
- **Denied**: The user denies authorization to access app-related data for tracking the user or the device.
- **NotDetermined**:  The app can't determine the user's authorization status for access to app-related data for tracking the user or the device.
- **Restricted**: Authorization to access app-related data for tracking the user or the device has a restricted status.

> You can get the status at any moment by calling the C++ method `UAppTrackingLibrary::GetTrackingAuthorizationStatus()` or the equivalent Blueprint node `Get Tracking Authorization Status`.
	

