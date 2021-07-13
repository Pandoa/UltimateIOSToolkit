# Banner View - C++ Examples
This section contains examples on how to use Banner Views with C++.
## Creating a Banner View
To use a Banner view, we first have to create one. You can create a Banner View as any UObjects with the `NewObject` templated method:
```cpp
#include "AdMob/BannerView.h"

void UMyClass::CreateBannerView()
{
	UAdMobBannerView* const MyBannerView = NewObject<UAdMobBannerView>();
}
```

## Initializing a Banner View
After creation, Banner Views have to be initialized to be usable. To initialize a Banner View, you have to call the `Initialize` method. 
This method takes time to complete.
```cpp
// Method that initializes our Banner View.
void UMyClass::InitializeBannerView()
{
	MyBannerView->Initialize
	(
		350 /* Width */,
		200 /* Height */,
		TEXT("ca-app-pub-3940256099942544/6300978111") /* The AdUnit used for the Banner View */,
		
		/* The callback when the Banner is initialized */
		FAdMobCallback::CreateUObject(this, &ThisClass::OnBannerViewInitialized) 
	);
}

// Method called when the initialization is over.
void UMyClass::OnBannerViewInitialized(const EAdMobError Error)
{
	if (Error == EAdMobError::None)
	{
		// Our Banner is correctly initialized.
	}
	
	else 
	{
		// An error occured. Check the exact value of Error to know what went wrong.
	}
}
```	

## Loading an Ad
Now that the Banner is initialized, it's time to load an ad that will be then shown to the user.  
To load an ad, call the `LoadAd` method.
```cpp
// The method that loads an ad for our Banner View.
void UMyClass::LoadAdForBannerView()
{
	MyBannerView->LoadAd
	(
		{ TEXT("Unreal"), TEXT("Game"), TEXT("Fun") } /* Request's keywords */,
		
		/* Callback called when the ad is loaded */
		FAdMobCallback::CreateUObject(this, &ThisClass::OnBannerViewAdLoaded)
	);
}

// Method called when the ad is loaded.
void UMyClass::OnBannerViewAdLoaded(const EAdMobError Error)
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

!> If you plan to show a Banner View during a precise time as for level transition, you should load the ad *before* so the ad
is ready when you want to show it.

## Showing the Banner
To show the Banner View, simply call the `Show` method.
```cpp
void UMyClass::ShowBannerView()
{
	MyBannerView->Show();
}
```

## Everything Together
Here is a complete example showing how to use the three examples above together. 

##### Header File `MyClass.h`
```cpp
// Your copyright notice.

#include "CoreMinimal.h"
#include "MyClass.generated.h"

// Forward declaration of the Banner View class.
class UAdMobBannerView;

/**
 * A class to show how to use a Banner View.
 * Call ShowBanner() to start the whole process of showing a Banner.
 * Note: Uncomment the API notation if you want to use it from another C++ module.
 **/
UCLASS()
class /* MYGAME_API */ UMyClass : public UObject
{
	GENERATED_BODY()
public:
	// Method that creates, initializes, loads an ad and finally shows a Banner view.
	void ShowBanner();
	
private:
	// Called when the Banner is initialized.
	void OnBannerViewInitialized(const EAdMobError Error);
	
	// Called when the ad for the Banner is loaded.
	void OnBannerViewAdLoaded(const EAdMobError Error);
	
private:
	// Our Banner View.
	// It's mandatory to mark it as UPROPERTY() as it would get garbage collected otherwise.
	UPROPERTY()
	UAdMobBannerView* MyBannerView;
};
```

##### Source File `MyClass.cpp`
```cpp
// Your copyright notice

#include "MyClass.h"

// Include the Banner View's definition.
#include "AdMob/BannerView.h"

// Our public method to start showing a Banner View.
void UMyClass::ShowBanner()
{
	// Creates the Banner View.
	MyBannerView = NewObject<UAdMobBannerView>();
	
	// Initializes the Banner View.
	MyBannerView->Initialize
	(
		350 /* Width */,
		200 /* Height */,
		TEXT("ca-app-pub-3940256099942544/6300978111") /* The AdUnit used for the Banner View */,
		
		/* The callback when the Banner is initialized */
		FAdMobCallback::CreateUObject(this, &ThisClass::OnBannerViewInitialized) 
	);
}

// Method called when the Banner is initialized.
void UMyClass::OnBannerViewInitialized(const EAdMobError Error)
{
	// Checks that no error occured.
	if (Error == EAdMobError::None)
	{
		// Loads the ad we want to show.
		MyBannerView->LoadAd
		(
			/* Request's keywords */
			{ TEXT("Unreal"), TEXT("Game"), TEXT("Fun") },
			/* Callback called when the ad is loaded */
			FAdMobCallback::CreateUObject(this, &ThisClass::OnBannerViewAdLoaded)
		);
	}
	
	else
	{
		// You should handle failed initialization here.
	}
}

// Method called when the ad is loaded.
void UMyClass::OnBannerViewAdLoaded(const EAdMobError Error)
{
	// Checks that no error occured.
    if (Error == EAdMobError::None)
    {
		// Optionally move the Banner View.
		MyBannerView->MoveTo(EAdMobAdPosition::TOP);
		
		// Or move it to a custom XY location.
		MyBannerView->MoveTo(30, 50);
		
		// Other methods can be called at a later time:
		// MyBannerView->Pause();
		// MyBannerView->Resume();
		// MyBannerView->Hide();
		// MyBannerView->Destroy();
		
		// Show the Banner View.
        MyBannerView->Show();
    }
    
    else
    {
        // An error occured. Check the exact value of Error to know what went wrong.
    }
}
```









































