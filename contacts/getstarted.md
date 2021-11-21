# Contacts - Get Started
This section contains the steps to enable contacts access for your application.

## Configuring Contacts

Before accessing the contacts, you have to enable it in the project's settings.  
1. Open `Edit` > `Project Settings` > `Plugins` > `Ultimate iOS Toolkit` > `Contacts`.
2. Tick the checkbox `Use Contacts`.
3. Add the `Contacts Usage Description` string. This text is shown to the user while requesting contacts access.


<div class="centered">
<img src="_images/EnableContacts.png"/>
</div>

?> Skipping this step will result in iOS terminating the application when attempting to access the device's contacts. 

## C++
You can include all the methods and classes for the Contacts API with the following include:

```cpp
#include "UltimateIOSToolkit/Contacts.h"
```
