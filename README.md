# RSPlacePicker
Pick a location and get latitude, longitude and map imageUrl

<img src="Images/img_1.png" alt="Map expanded" width="500" /> <img src="Images/img_2.png" alt="Place selected" width="500"/> <img src="Images/img_3.png" alt="Results expanded" width="500"/>

# Download
Add Jitpack in your root build.gradle at the end of repositories:
```
allprojects {
  repositories {
	...
	maven { url 'https://jitpack.io' }
    }
}

```
Step 2. Add the dependency
```
dependencies {
      implementation 'com.github.Sanjay-Prajapati:RSPlacePicker:v1.0.1'
 }

```

## Setup
1. Add Google Play Services to your project - [How to](https://developers.google.com/android/guides/setup).
2. Sign up for API keys - [How to](https://developers.google.com/places/android-sdk/signup)
   - Make sure your api key is not restricted.
3. Add the Android API key to your AndroidManifest file as in the [sample project](https://github.com/RAHUL-SADHU/RSPlacePicker/blob/master/app/src/main/AndroidManifest.xml).

### Add code your activity
```
 val placePicker = RSPlacePicker()
                   .setAndroidApiKey("YOUR GOOGLE API KEY")
		   .build(this)
 startActivityForResult(placePicker, REQUEST_PLACE_PICKER)

 override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
        super.onActivityResult(requestCode, resultCode, data)
        if ((requestCode == REQUEST_PLACE_PICKER) && (resultCode == Activity.RESULT_OK)) {
            val location: LocationModel? = data?.let { RSPlacePicker.getLocation(it) }
            Toast.makeText(this, "latitude: ${location?.latitude} longitude: ${location?.longitude}
	    imageUrl:${location?.mapImage}", Toast.LENGTH_LONG).show()
        }
  }

```
