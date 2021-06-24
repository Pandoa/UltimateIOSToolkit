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

## Request User Consent