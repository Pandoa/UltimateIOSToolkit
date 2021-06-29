# GDPR - Blueprints Examples
This section contains examples on how to use GDPR with the plugin.
## Checking if User Consent is required
At app startup, you must check if the consent is required. To do so, call the `Is Consent Required` node of the Consent Library.

<div style="text-align:center">
<img src="https://github.com/Pandoa/AdsPro/blob/main/_images/IsConsentRequired.png?raw=true"/>
</div>

## Using the UMP to request consent
Now that we know if the consent is required, we must ask the user about it.   
We can show the UMP consent form with the `Request Consent` method of the Consent Library.  
You can also nicely launch your own consent form here so it blends better with your application style.

<div style="text-align:center">
<img src="https://github.com/Pandoa/AdsPro/blob/main/_images/UMPRequestConsent.png?raw=true"/>
</div>

## Disabling Personalized Ads
If the user didn't give you consent, you now have to disable presonalized ads.

<div style="text-align:center">
<img src="https://github.com/Pandoa/AdsPro/blob/main/_images/DisablePersonalizedAds.png?raw=true"/>
</div>


