# Banner View
This section contains information about Banner Views (also called Ad Views), if you are looking for examples, head to [the Blueprint examples](/blueprintbannerview) or [the C++ examples](/cppbannerview).

## What are they?
Banner views occupy a spot within an app's layout, either at the top or bottom of the device screen. They stay on screen while users are interacting with the app, and can refresh automatically after a certain period of time. 

<div style="text-align:center">
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="80px" height="auto" viewBox="0 0 140 291.35" style="overflow:visible;enable-background:new 0 0 140 291.35;" xml:space="preserve">
<style type="text/css">
	.st0{fill:#AED8E6;}
	.st1{fill:#378AAD;}
	.st2{fill:#131313;}
	.st3{fill:#28829B;}
</style>
<defs>
</defs>
<g>
	<path class="st0" d="M124.85,291.35H15.15C6.78,291.35,0,284.57,0,276.2V15.15C0,6.78,6.78,0,15.15,0h109.69
		C133.22,0,140,6.78,140,15.15V276.2C140,284.57,133.22,291.35,124.85,291.35z"/>
	<polyline class="st1" points="60.16,132.01 60.16,155.98 84.46,144 	"/>
	<path class="st2" d="M122.62,286.35H17.38c-6.84,0-12.38-5.54-12.38-12.38V17.38C5,10.54,10.54,5,17.38,5h105.24
		C129.46,5,135,10.54,135,17.38v256.59C135,280.81,129.46,286.35,122.62,286.35z"/>
	<path class="st0" d="M101.56,12.72H38.44c-2.47,0-4.47-2-4.47-4.47V3.15h72.07v5.09C106.03,10.71,104.03,12.72,101.56,12.72z"/>
	<path class="st3" d="M123.17,171.82H16.8c-2.55,0-4.61-2.06-4.61-4.61v-34.69c0-2.55,2.06-4.61,4.61-4.61h106.37
		c2.55,0,4.61,2.06,4.61,4.61v34.69C127.78,169.76,125.72,171.82,123.17,171.82z"/>
	<path class="st0" d="M107.22,282.69H32.78c-0.86,0-1.56-0.7-1.56-1.56l0,0c0-0.86,0.7-1.56,1.56-1.56h74.44
		c0.86,0,1.56,0.7,1.56,1.56l0,0C108.78,281.99,108.08,282.69,107.22,282.69z"/>
	<circle class="st2" cx="32.61" cy="149.87" r="14.58"/>
	<path class="st2" d="M115.58,164.45H57.34c-1.31,0-2.37-1.06-2.37-2.37v0c0-1.31,1.06-2.37,2.37-2.37h58.24
		c1.31,0,2.37,1.06,2.37,2.37v0C117.95,163.39,116.89,164.45,115.58,164.45z"/>
	<path class="st2" d="M115.58,152.23H57.34c-1.31,0-2.37-1.06-2.37-2.37l0,0c0-1.31,1.06-2.37,2.37-2.37h58.24
		c1.31,0,2.37,1.06,2.37,2.37l0,0C117.95,151.18,116.89,152.23,115.58,152.23z"/>
	<path class="st2" d="M115.58,140.02H57.34c-1.31,0-2.37-1.06-2.37-2.37l0,0c0-1.31,1.06-2.37,2.37-2.37h58.24
		c1.31,0,2.37,1.06,2.37,2.37l0,0C117.95,138.96,116.89,140.02,115.58,140.02z"/>
</g>
</svg>
<div>A Banner View</div>
</div>

## API Reference
### Methods
#### Initialize 
##### Description
Initializes the AdView. This method must be called before any other methods on the object.
> For C++ only, this method is called automatically when you create an Ad View in Blueprints.  
##### Parameters
- **Width** `int32`: The width of the Ad View.
- **Height** `int32`: The height of the AdView.
- **AdUnit** `FStringView`: The AdUnit used to display the ad.
- **Callback** `FAdMobCallback`: Callback called when the AdView has been initialized.

#### LoadAd
##### Description
Loads an ad. This method must be called before trying to display an ad. It takes time to complete.
##### Parameters

- **Keywords** `const TArray<FString>&`: The keywords for the ad.
- **Callback** `FAdMobCallback`: Callback called when the ad has been loaded.

#### Show
##### Description
Shows the ad. An ad has the be loaded first by using LoadAd.
##### Parameters
- **Callback** `FAdMobCallback`: Callback called when the ad is shown.

#### Hide
##### Description
Hides the AdView.
##### Parameters
- **Callback** `FAdMobCallback`: Callback called when the AdView has been hidden.

#### Pause
##### Description
Pauses the AdView.
##### Parameters

- **Callback** `FAdMobCallback`: Callback called when the AdView has been paused.

#### Resume
##### Description
Resumes the AdView previously paused.
##### Parameters
- **Callback** `FAdMobCallback`: Callback called when the AdView has been resumed.

#### MoveTo
##### Description
Moves the AdView to the desired location.
##### Parameters
- **X** `int32`: The X coordinate where we want the AdView.
- **Y**:`int32` The Y coordinate where we want the AdView.
- **Callback** `FAdMobCallback`: Callback called when the AdView has been moved.

#### MoveTo
##### Description
Moves the AdView to the desired location.
##### Parameters
- **Position**: The position where we want to move the AdView to.
- **Callback** `FAdMobCallback`: Callback called when the AdView has been moved.

#### Destroy
##### Description
Destroys the AdView.
##### Parameters
- **Callback** `FAdMobCallback`: Callback called when the AdView has been destroyed.

### Events
#### OnAdOpened
Called when the user taped the ad and the overlay that covers the screen appeared.

#### OnAdClicked
Called when the user clicked on the ad.

#### OnAdClosed
Called when the user is about to return to the app after tapping on an ad.




