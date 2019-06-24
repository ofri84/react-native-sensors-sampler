# react-native-sensors-sampler

## Getting started

`$ npm install react-native-sensors-sampler --save`

### Mostly automatic installation

`$ react-native link react-native-sensors-sampler`

### Manual installation


#### iOS

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `react-native-sensors-sampler` and add `SensorsSampler.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libSensorsSampler.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)<

#### Android

1. Open up `android/app/src/main/java/[...]/MainApplication.java`
  - Add `import com.dayzz.SensorsSamplerPackage;` to the imports at the top of the file
  - Add `new SensorsSamplerPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-sensors-sampler'
  	project(':react-native-sensors-sampler').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-sensors-sampler/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      implementation project(':react-native-sensors-sampler')
  	```
4. Android dangerous permissions
  - if you want to use noise sampler you must ask for this permission before subscribing

      ```
        <uses-permission android:name="android.permission.RECORD_AUDIO" />
      ```


## Usage
```javascript
import { allowedSubscriptions, subscribeTo, unsubscribe, settings } from 'react-native-sensors-sampler';

// set settings - every key is optional
settings({
    interval: 100, // 100 millis
    period: 10000, // 10000 millis
    useBackCamera: true // only iOS, default false
})

// subscribe to event
subscribeTo(
    allowedSubscriptions.NOISE, // event
    ({ value, updateType }) => { ... }, // update callback
    (error) => { ... }, // error callback - subscription faild
);

// unsubscribe from event
// no need to call this method when subscription period is over
unsubscribe(allowedSubscriptions.NOISE);
```
