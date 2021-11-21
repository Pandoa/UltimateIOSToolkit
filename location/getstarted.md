# Location - Get Started
This section contains the steps to enable location data access for your application.

## Configuring Contacts

!> This step is not required if your request location through the iOS 15 location button.

Before accessing the location data, you have to enable it in the project's settings.  
1. Open `Edit` > `Project Settings` > `Plugins` > `Ultimate iOS Toolkit` > `Contacts`.
2. Tick the checkbox `Use Location when in Use` or `Use Location Always` according to your need.
3. Add the `Location <type> Usage Description` string. This text is shown to the user while requesting location data access.


<div class="centered">
<img src="_images/EnableLocation.png"/>
</div>

?> Skipping this step will result in iOS terminating the application when attempting to access the device's location data. 

## C++
You can include all the methods and classes for the Core Location API with the following include:

```cpp
#include "UltimateIOSToolkit/Location.h"
```
