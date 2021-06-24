# GDPR
This section contains information on how to make your application GDPR-compliant.

## What is GDPR
The General Data Protection Regulation (GDPR) is a privacy and security law applicated by the European Union.  
It imposes obligations onto organizations anywhere, as long as they target or collect data related to people in the EU.

Among other obligations, the data subject has to give you specific, unambiguous consent to process the data.

AdMob uses users' data to show personalized ads through your application so you must comply to it if you target EEA countries or disable
personalized ads. The same applies for any Mediation Partner used by your application.

!> Please, keep in mind that this documentation is not law related. For any real concern, a contact with a specialized lawyer is probably the best thing to do.

## Delay Mobile Ads SDK Initialization
By default, the Google Mobile Ads SDK initializes app measurement and begins sending user-level event 
data to Google immediately when the app starts. This initialization behavior ensures you can enable AdMob 
user metrics without making additional code changes.

However, if your app requires user consent before these events can be sent, you can delay app measurement 
until you explicitly initialize the Mobile Ads SDK or load an ad.

To delay app measurement, add the following in `<Project>/Config/Engine.ini`:
```ini
[AdsPro]
DelayGoogleMeasurementsData=true
```

!> It is important to not load any ads before obtaining consent as the Google Mobile Ads gets automatically initialized when an ad request is done.

> You can initialize the Mobile Ads SDK at any time by calling `UAdMobLibrary::InitializeMobileAdsSDK()` or the equivalent Blueprint node `Initialize the MobileAds SDK`.

## Check if User Consent is required
After making sure the SDK initialization is delayed, we need to know if the consent is required.  
The plugin offers the method `UConsentLibrary::IsConsentRequired()` and its equivalent Blueprint node `Is Consent Required` to know if the consent is required. These methods 
return `true` if the user is in the EEA or we weren't able to get the information.

## Requesting Consent
It's now time to request consent.
### Using the User Messaging Platform
The UMP can be used to display Google's default consent form.
### Rolling your own

## Consent Refused


## Summary
The following diagram shows a summary to how your application should behave.
<div style="text-align:center">
	<img src="https://github.com/Pandoa/AdsPro/blob/main/_images/AdMobConsent.png?raw=true"/>
</div>