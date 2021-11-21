# Biometry - Get Started
This section contains the steps to enable biometry for your application.

## Configuring Biometry

Before using biometry, you have to enable it in the project's settings.  
1. Open `Edit` > `Project Settings` > `Plugins` > `Ultimate iOS Toolkit` > `Biometry`.
2. Tick the checkbox `Use Biometry`.
3. Add the `Biometry Usage Description` string. This text is shown to the user while requesting Biometry access.


<div class="centered">
<img src="_images/EnableBiometry.png"/>
</div>

?> Skipping this step will result in iOS terminating the application when attempting to access the biometry API. 

## C++
You can include all the methods and classes for Biometry with the following include:

```cpp
#include "UltimateIOSToolkit/Biometry.h"
```
