# cordova-jb-plugin-panframe
Integrates panframe SDK with cordova: http://www.panframe.com/

This plugin defines a global `panframePlugin` object, which has panframe plugin function.
Although the object is in the global scope, it is not available until after the `deviceready` event.

    document.addEventListener("deviceready", onDeviceReady, false);
    function onDeviceReady() {
    	panframePlugin.init(videoUrl, viewMode);
    }

## Installation

    cordova plugin add https://github.com/bijanmmarkes/cordova-jb-plugin-panframe.git

### Supported Platforms

- Android
- iOS

### Parameters
	videoUrl: Your videUrl - supports RTMP, and HTTP Live Streaming (HLS) e.g. - [Ultra light flight] - http://mobile.360heros.com/producers/4630608605686575/9813601418398322/video/video_31b451b7ca49710719b19d22e19d9e60.mp4
	viewMode:
		iOS:
			0 for spherical,
	        1 for flat,
	        2 for cylindrical,
	        3 for side-by-side VR (non-stereoscopic),
	        4 for top-down VR formatted content (stereoscopic).
	    Android:
	    	0 for spherical,
			1 for flat display,
			2 for stereo side-by-side


### Quick Example

    panframePlugin.init("http://mobile.360heros.com/producers/4630608605686575/9813601418398322/video/video_31b451b7ca49710719b19d22e19d9e60.mp4", 2);


### Android Notes

- If you are using any other plugin or library which internally uses Android Play Services, then gradle build will failed with Multiple Dex File error. To Fix that you can do either of the following 
	* Remove the `play-services` dependencies from `build.gradle` file and rebuild. (_This needed to be done every time you remove & add plugin again._)
	* Download clone this plugin repository locally, remove the following line from `plugin.xml` -
		`<dependency id="cordova-plugin-android-support-v4" />` 
      & now add plugin locally by `cordova plugin add PATH_TO_REPO`

