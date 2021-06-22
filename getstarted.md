# Get Started

This section contains steps required to use the plugin. You can still use the plugin if you don't follow them but will only have test ads and default configuration.

## Creating an AdMob account
> [Official documentation page](https://support.google.com/admob/answer/7356219) for account creation.  

To create an AdMob account:
1. Go to https://apps.admob.com.
2. Click Sign up with your Google Account to sign up with an existing Google Account or click Create a new Google Account if you want to create a new account. Follow the on-screen prompts.
3. Complete the account information to create your new AdSense and Google Ads accounts:  
4. Check the checkbox to confirm that you've read and agree to the program policies, AdSense Terms & Conditions, and Google Ads Terms & Conditions.
5. Click Create AdMob account.

## Set up an app in AdMob
> [Official documentation page](https://support.google.com/admob/answer/9989980) for account creation.  

1. Sign in to your AdMob account at https://apps.admob.com.
2. Click Apps in the left sidebar.
3. Click Add app.
4. Select the platform of your app (Android or iOS). 
5. Select Yes, if it is listed on a supported app store.
6. Click Continue.

## Getting the Application ID

To make the plugin use your newly created application, we need to get the generated Application ID.

1. Go to https://apps.admob.com/.
2. Click Apps in the left sidebar.
3. Click the newly created application.
4. Click App Settings in the left sidebar.
5. In the middle of the screen, copy the Application ID by clicking on <img src="https://github.com/Pandoa/AdsPro/blob/main/_images/GetApplicationId.png?raw=true" height="25px" style="position:relative;top:8px"/>.
7. Open (or create it if it doesn't exist) the file `<YourProject>/Config/Engine.ini` in your favorite text editor.
8. Add the Application ID previously copied for the desired platform with the following structure:
```ini
[AdsPro]
AndroidAdMobAppID=ca-app-pub-XXXXXXXXXXXXXXXXXXX~XXXXXXX ; For Android
iOSAdMobAppID=ca-app-pub-XXXXXXXXXXXXXXXXXXX~XXXXXXX     ; For iOS
```
9. Save and close the file `Engine.ini`.

!> After doing this step, make sure to *always* use test ads during development or your account might be flagged and suspended if you don't.

> If this step is skipped, a test Application ID is automatically used. It will only show test ads.


