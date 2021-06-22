# C++ Setup
This section contains required steps to start using the plugin with C++.
## Including the `AdsPro` module
To use the plugin using C++, you need to include the `AdsPro` module.  
To do so, open your `Project.Build.cs` file and add the following line in the constructor:
```csharp
PublicDependencyModuleNames.Add("AdsPro");
```
## Plugin Includes
To use the methods and classes of the plugin, you must include the corresponding includes.  
Here is a non-exhaustive list of available includes:
```cpp
// Ads
#include "AdMob/AdMobLibrary.h"
#include "AdMob/AdMobTypes.h"
#include "AdMob/BannerView.h"
#include "AdMob/RewardedVideo.h"
#include "AdMob/InterstitialAd.h"

// Mediation
#include "Mediation/Vungle/VungleLibrary.h"
#include "Mediation/Vpon/VponLibrary.h"

// iOS 14 App Tracking Transparency
#include "AppTracking/AppTrackingLibrary.h"

// Consent
#include "Consent/ConsentLibrary.h"
```
