# Motion - Get Started
This section contains the steps to enable motion for your application.

## Configuring Motion

Before using biometry, you have to enable it in the project's settings.  
1. Open `Edit` > `Project Settings` > `Plugins` > `Ultimate iOS Toolkit` > `Motion`.
2. Tick the checkbox `Use Motion`.
3. Add the `Motion Usage Description` string. This text is shown to the user while requesting Motion access.


<div class="centered">
<img src="_images/EnableMotion.png"/>
</div>

?> Skipping this step will result in iOS terminating the application when attempting to access the motion API. 

## C++
You can include all the methods and classes for the Motion API with the following include:

```cpp
#include "UltimateIOSToolkit/Motion.h"
```
