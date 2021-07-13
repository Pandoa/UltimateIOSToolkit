# Rewarded Video - C++ Examples
This section contains examples on how to use Rewarded Videos with C++.
## Creating a Rewarded Video
To use a Rewarded Video, we first have to create one. You can create a Rewarded Video as any UObjects with the `NewObject` templated method:

```cpp
#include "AdMob/RewardedVideo.h"

void UMyClass::CreateRewardedVideo()
{
	UAdMobRewardedVideo* const MyRewardedVideo = NewObject<UAdMobRewardedVideo>();
}
```

## Loading an Ad
Before showing the Rewarded Video, we have to load an ad for it first.
To load an ad, call the `LoadAd` method.

```cpp
void UMyClass::LoadAdForRewardedVideo()
{
	MyRewardedVideo->LoadAd
	(
		/* Ad unit for the ad. */
		TEXT("ca-app-pub-3940256099942544/3419835294"),
		
		/* Request's keywords. */
		{ TEXT("Unreal"), TEXT("Game"), TEXT("Fun") },
		
		/* Callback called when the ad is loaded. */
		FAdMobCallback::CreateUObject(this, &ThisClass::OnRewardedVideoLoaded)
	);
}

// Method called when the ad is loaded.
void UMyClass::OnRewardedVideoLoaded(const EAdMobError Error)
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

!> If you plan to show a Rewarded Video during a precise time as for level transition or on a loading screen, you should load the ad *before* so the ad
is ready when you want to show it.

## Showing the Rewarded Video
To show the Rewarded Video, simply call the `Show` method.
```cpp
void UMyClass::ShowRewardedVideo()
{
	MyInterstitial->Show();
}
```

## Waiting for Reward
The most important part of showing the rewarded video is to give a reward if the user watched the ad.  
To do so, we can bind the `OnReward` event after we create the Rewarded Video.
```cpp
void UMyClass::CreateRewardedVideo()
{
	// Creates the Rewarded Video as shown previously.
	UAdMobRewardedVideo* const MyRewardedVideo = NewObject<UAdMobRewardedVideo>();
	
	// Binds our function to the reward event.
	MyRewardedVideo->OnReward.AddDynamic(this, &ThisClass::OnReward);
	
	// Load an ad and show the video...
}

void UMyClass::OnReward(const FString& Type, int32 Amount)
{
	// If this code executes, the user deserves a reward.
}
```

