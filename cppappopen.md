# App Open - C++ Examples
This section contains examples on how to use App Open ads with C++.
## Creating an App Open Ad
To use an App Open ad, we first have to create one. You can create an App Open ad as any UObjects with the `NewObject` templated method:
```cpp
#include "AdMob/AppOpen.h"

void UMyClass::CreateAppOpen()
{
	UAdMobAppOpen* const MyAppOpen = NewObject<UAdMobAppOpen>();
}
```
## Loading an Ad
Before showing the App Open ad, we have to load an ad for it first.
To load an ad, call the `LoadAd` method.
```cpp
void UMyClass::LoadAdForAppOpen()
{
	MyAppOpen->LoadAd
	(
		/* Ad unit for the ad. */
		TEXT("ca-app-pub-3940256099942544/3419835294"),
		
		/* Request's keywords. */
		{ TEXT("Unreal"), TEXT("Game"), TEXT("Fun") },
		
		/* The orientation we want to display the App Open. */
		EAppOpenOrientation::Portrait,
		
		/* Callback called when the ad is loaded. */
		FAdMobCallback::CreateUObject(this, &ThisClass::OnAppOpenAdLoaded)
	);
}

// Method called when the ad is loaded.
void UMyClass::OnAppOpenAdLoaded(const EAdMobError Error)
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

!> If you plan to show an App Open ad during a precise time as for level transition or on a loading screen, you should load the ad *before* so the ad
is ready when you want to show it.

## Showing the App Open Ad
To show the App Open ad, simply call the `Show` method.
```cpp
void UMyClass::ShowAppOpen()
{
	MyAppOpen->Show();
}
```

## Discarding Old Ads
App Open ads are usually loaded in advance to a potential occasion to show the ad to the user. Due to this fact, some App Open ads might
wait a long time before being shown. To avoid showing ads loaded too long ago that AdMob wouldn't reward us for, we can check how much
time elapsed since we loaded the ad.  
To do it, you can use the `GetAdLoadTime()` method.

```cpp
void UMyClass::ShowAdIfNotExpired()
{
	// Get when the ad was loaded.
	const FDateTime LoadTime = MyAppOpen->GetAdLoadTime();

	// Checks that less than 4 hours have passed.
	if (LoadTime + FTimespan::FromHours(4.) > FDateTime::Now())
	{
		// We should reload an ad.
		// MyAppOpen->LoadAd(...);
	}
	else
	{
		// The ad is less than 4 hours old. We can show it.
		MyAppOpen->Show();
	}
}
```


## Everything Together
##### Header File `MyClass.h`

```cpp
// Your copyright notice.

#include "CoreMinimal.h"
#include "MyClass.generated.h"

// Forward declaration of the App Open class.
class UAdMobAppOpen;

/**
 * A class to show how to use an App Open ad.
 * Call ShowAppOpen() to start the whole process of showing an App Open ad.
 * Note: Uncomment the API notation if you want to use it from another C++ module.
 **/
UCLASS()
class /* MYGAME_API */ UMyClass : public UObject
{
	GENERATED_BODY()
public:
	// Method that creates and shows an App Open ad.
	void ShowAppOpen();
	
private:
	// Method called when the ad has been loaded.
	void OnAppOpenAdLoaded(const EAdMobError Error);
	
private:
	// Called when the App Open is presented to the user.
	// We mark it as UFUNCTION() to be able to use it with AddDynamic().
	UFUNCTION()
	void OnAppOpenPresented(EAdMobError Error);
	
	// Called when the user dismissed the ad.
	// We mark it as UFUNCTION() to be able to use it with AddDynamic().
	UFUNCTION()
	void OnAppOpenDismissed();
	
	// Called when the ad recorded an impression.
	// We mark it as UFUNCTION() to be able to use it with AddDynamic().
	UFUNCTION()
	void OnAppOpenImpression();
	
private:
	// Our App Open ad.
	// It's mandatory to mark it as UPROPERTY() as it would get garbage collected otherwise.
	UPROPERTY()
	UAdMobAppOpen* MyAppOpen;
};
```

##### Source File `MyClass.cpp`

```cpp
// Your copyright notice.

#include "MyClass.h"

#include "AdMob/AppOpen.h"

void UMyClass::ShowAppOpen()
{
	// We start by creating the App Open object.
	MyAppOpen = NewObject<UAdMobAppOpen>();
	
	// Here, we can optionally bind methods to available events.
	MyAppOpen->OnPresented .AddDynamic(this, &ThisClass::OnAppOpenPresented);
	MyAppOpen->OnDismissed .AddDynamic(this, &ThisClass::OnAppOpenDismissed);
	MyAppOpen->OnImpression.AddDynamic(this, &ThisClass::OnAppOpenImpression);
	
	// Everything is setup, we load the ad.
	MyAppOpen->LoadAd
	(
		/* Ad unit for the ad. */
		TEXT("ca-app-pub-3940256099942544/3419835294"),
		
		/* Request's keywords. */
		{ TEXT("Unreal"), TEXT("Game"), TEXT("Fun") },
		
		/* The orientation we want to display the App Open. */
		EAppOpenOrientation::Portrait,
		
		/* Callback called when the ad is loaded. */
		FAdMobCallback::CreateUObject(this, &ThisClass::OnAppOpenAdLoaded)
	);
}

void UMyClass::OnAppOpenAdLoaded(const EAdMobError Error)
{
	if (Error == EAdMobError::None)
	{
		// An ad is correctly loaded. We can show it now.
		MyAppOpen->Show();
	}
	else
	{
		// Something went wrong.
	}
}

void UMyClass::OnAppOpenImpression()
{
	// An impression has been recorded.
}

void UMyClass::OnAppOpenDismissed()
{
	// The user dismissed the App Open ad.
}

void UMyClass::OnAppOpenPresented(EAdMobError Error)
{
	if (Error == EAdMobError::None)
	{
		// The ad is currently showing.
	}
	else
	{
		// Something went wrong while showing the ad.
	}
}

```























