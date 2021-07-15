# C++ Setup
This section contains required steps to start using the plugin with C++. These steps are not needed if you don't plan to use the plugin with C++.
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
#include "AdMob/AppOpen.h"
#include "AdMob/BannerView.h"
#include "AdMob/RewardedVideo.h"
#include "AdMob/InterstitialAd.h"

// Mediation
#include "Mediation/AdColony/AdColonyLibrary.h"
#include "Mediation/AppLovin/AppLovinLibrary.h"
#include "Mediation/Chartboost/ChartboostLibrary.h"
#include "Mediation/Fyber/FyberLibrary.h"
#include "Mediation/InMobi/InMobiLibrary.h"
#include "Mediation/IronSource/IronSourceLibrary.h"
#include "Mediation/MyTarget/MyTargetLibrary.h"
#include "Mediation/Tapjoy/TapjoyLibrary.h"
#include "Mediation/UnityAds/UnityAdsLibrary.h"
#include "Mediation/VerizonMedia/VerizonMediaLibrary.h"
#include "Mediation/Vpon/VponLibrary.h"
#include "Mediation/Vungle/VungleLibrary.h"

// iOS 14 App Tracking Transparency
#include "AppTracking/AppTrackingLibrary.h"

// Consent
#include "Consent/ConsentLibrary.h"
```
