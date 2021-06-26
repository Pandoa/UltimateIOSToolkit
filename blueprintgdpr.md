# GDPR - Blueprints Examples
This section contains examples on how to use GDPR with the plugin.
## Checking if User Consent is required
At app startup, you must check if the consent is required. To do so, call the `Is Consent Required` node of the Consent Library.
```cpp
// Include the Consent Library.
#include "Consent/ConsentLibrary.h"

// Our method starting the GDPR sequence.
void UMyClass::StartGDPRSequence()
{
	// Gets if the consent is required.
	// This method takes time to complete so we bind the OnConsentRequirementResult method as a callback
	// when we know if the consent is required.
	UConsentLibrary::IsConsentRequired(FConsentRequiredCallback::CreateUObject(this, &ThisClass::OnConsentRequirementResult));
}

// This method executes when we know if the consent is required.
void UMyClass::OnConsentRequirementResult(const bool bIsConsentRequired)
{
	if (bIsConsentRequired)
	{
		// We need user consent!
		// We must now prompt a consent window, either with UMP or our own.
	}
	else
	{
		// No need for user consent.
		// You can start loading and displaying ads.
	}
}
```

## Using the UMP to request consent
Now that we know if the consent is required, we must ask the user about it.   
We can show the UMP consent form with the `RequestConsent()` method of the Consent Library.  
You can also nicely launch your own consent form here so it blends better with your application style.
```cpp
// Our method showing the UMP window.
void UMyClass::ShowConsentWindow()
{
	// Requests the consent with the UMP platform.
	// As it takes time until the user make a choice, we setup a callback that is going to be called 
	// when the user made a choice.
	UConsentLibrary::RequestConsent
	(
		false /* bTagForUnderAgeOfConsent */,
		false /* bUseDebugSettings */,
		EConsentDebugGeography::Disabled /* DebugGeography */,
		FConsentRequestCallback::CreateUObject(this, &ThisClass::OnConsentRequestResult)
	);
}

// This method is executed when the user made a choice.
void UMyClass::OnConsentRequestResult(const EConsentError Error, const EConsentStatus Status)
{
	// We successfully showed the consent window.
	if (Error == EConsentError::None)
	{
		// Get what the user actually chose.
		const EConsentType ConsentType = UConsentLibrary::GetConsentType();
		
		switch (ConsentType)
		{
			case EConsentType::Unknown:
			{
				// The consent is still unknown.
			} 
			break;
			
			case EConsentType::Personalized:
			{
				// We can show personalized ads.
			} 
			break;
			
			case EConsentType::NonPersonalized:
			{
				// We can't show personalized ads.	
			} 
			break;
		}
	}
	
	// An error occured check "Error" value to get the exact error.
	else
	{
		// Failed to get consent.
	}
}
```

## Disabling Personalized Ads
If the user didn't give you consent, you now have to disable presonalized ads.
```cpp
// Include the AdMob library.
// To disable a Mediation Partner, you have to include its library as well.
#include "AdMob/AdMobLibrary.h"

// Our method to disable personalized ads.
void UMyClass::DisablePersonalizedAds()
{
	// Disable personalized Ads Requests.
	UAdMobLibrary::SetPersonalizedAdsEnabled(false);
	
	// You have to do the same thing for each Mediation Partner you are using. More on this on each Mediation Partner's page.
}
```

## Everything Together
Here is all the code assembled. A simple call to `StartGDPRSequence` will then start the whole GDPR sequence.

```cpp
#include "Consent/ConsentLibrary.h"
#include "AdMob/AdMobLibrary.h"

// Our method starting the GDPR sequence.
void UMyClass::StartGDPRSequence()
{
	// Gets if the consent is required.
	// This method takes time to complete so we bind the OnConsentRequirementResult method as a callback
	// when we know if the consent is required.
	UConsentLibrary::IsConsentRequired(FConsentRequiredCallback::CreateUObject(this, &ThisClass::OnConsentRequirementResult));
}

// This method executes when we know if the consent is required.
void UMyClass::OnConsentRequirementResult(const bool bIsConsentRequired)
{
	if (bIsConsentRequired)
	{
		// We need user consent!
		// We must now prompt a consent window, either with UMP or our own.
		ShowConsentWindow();
	}
	else
	{
		// No need for user consent.
		// You can start loading and displaying ads.
		OnGDPRSequenceOver();
	}
}

// Our method showing the UMP window.
void UMyClass::ShowConsentWindow()
{
	// Requests the consent with the UMP platform.
	// As it takes time until the user make a choice, we setup a callback that is going to be called 
	// when the user made a choice.
	UConsentLibrary::RequestConsent
	(
		false /* bTagForUnderAgeOfConsent */,
		false /* bUseDebugSettings */,
		EConsentDebugGeography::Disabled /* DebugGeography */,
		FConsentRequestCallback::CreateUObject(this, &ThisClass::OnConsentRequestResult)
	);
}

// This method is executed when the user made a choice.
void UMyClass::OnConsentRequestResult(const EConsentError Error, const EConsentStatus Status)
{
	// We successfully showed the consent window.
	if (Error == EConsentError::None)
	{
		// Get what the user actually chose.
		const EConsentType ConsentType = UConsentLibrary::GetConsentType();
		
		switch (ConsentType)
		{
			case EConsentType::Unknown:
			{
				// The consent is still unknown. An error probably occured.
				// You shouldn't assume consent has been given.
			} 
			break;
			
			case EConsentType::Personalized:
			{
				// We can show personalized ads.
				OnGDPRSequenceOver();
			} 
			break;
			
			case EConsentType::NonPersonalized:
			{
				// We can't show personalized ads.	
				DisablePersonalizedAds();
				
				// Personalized ads disabled, we can continue.
				OnGDPRSequenceOver();				
			} 
			break;
		}
	}
	
	// An error occured check "Error" value to get the exact error.
	else
	{
		// Failed to get consent.
		// An error occured, what should be done is up to you.
		// You shouldn't assume consent has been given.
	}
}

// Our method to disable personalized ads.
void UMyClass::DisablePersonalizedAds()
{
	// Disable personalized Ads Requests.
	UAdMobLibrary::SetPersonalizedAdsEnabled(false);
	
	// You have to do the same thing for each Mediation Partner you are using. More on this on each Mediation Partner's page.
}

// Called when the GDPR sequence is over. Care has been taken in case of consent refused.
void UMyClass::OnGDPRSequenceOver()
{
	// Either way, we can start loading and showing ads!
}

```







