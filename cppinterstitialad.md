# Interstitial Ad - C++ Examples
This section contains examples on how to use Interstitial Ads with C++.
## Creating an Interstitial Ad
To use an Interstitial Ad, we first have to create one. You can create an Interstitial Ad as any UObjects with the `NewObject` templated method:

```cpp
#include "AdMob/InterstitialAd.h"

void UMyClass::CreateInterstitialAd()
{
	UAdMobInterstitialAd* const MyInterstitialAd = NewObject<UAdMobInterstitialAd>();
}
```

## Loading an Ad
Before showing the Interstitial Ad, we have to load an ad for it first.
To load an ad, call the `LoadAd` method.

```cpp
void UMyClass::LoadAdForInterstitialAd()
{
	MyInterstitialAd->LoadAd
	(
		/* Ad unit for the ad. */
		TEXT("ca-app-pub-3940256099942544/3419835294"),
		
		/* Request's keywords. */
		{ TEXT("Unreal"), TEXT("Game"), TEXT("Fun") },
		
		/* Callback called when the ad is loaded. */
		FAdMobCallback::CreateUObject(this, &ThisClass::OnInterstitialAdLoaded)
	);
}

// Method called when the ad is loaded.
void UMyClass::OnInterstitialAdLoaded(const EAdMobError Error)
{
	if (Error == EAdMobError::None)
	{
		// The ad is correctly loaded.
	}
	
	else
	{
		// An error occured. Check the exact value of Error to know what went wrong.
	}
}
```

!> If you plan to show an Interstitial Ad during a precise time as for level transition or on a loading screen, you should load the ad *before* so the ad
is ready when you want to show it.

## Showing the Interstitial Ad
To show the Interstitial Ad, simply call the `Show` method.
```cpp
void UMyClass::ShowInterstitialAd()
{
	MyInterstitial->Show();
}
```