# react-native-howto
A collection of links and references for all things React Native. 

### Styling
* Responsive Text:
  * [react-native-size-matters](https://github.com/nirsky/react-native-size-matters)
* Style Architecture: 
  * [Scaling React Native apps for Tablets](https://medium.com/react-native-training/scaling-react-native-apps-for-tablets-211de8399cf1)
  * [React Native — Design Systems and Styling Strategy](https://medium.com/@mikecavaliere/react-native-design-systems-and-styling-strategy-189e4f8f1684) 
  
  

### Snippets

* Disable yellow box warnings in simulator/emulator
  * `console.disableYellowBox = true;`

### Gotchas and Fixes
* ```DeltaPatcher.js:58 Uncaught (in promise) Error: DeltaPatcher should receive a fresh Delta when being initialized```
  * [Monkey patch: 2 RN files](https://github.com/facebook/react-native/issues/18209#issuecomment-371935230)
* `AsyncStorage` promises not resolving, or callbacks not firing.
  * [Monkey patch](https://github.com/facebook/react-native/pull/18522/files) and [some background](https://github.com/facebook/react-native/issues/13704).
* [Elements in KeyboardAvoidingView still covered by keyboard](https://github.com/facebook/react-native/issues/13497)
  * Usually happens with bottom-most element. 
  * Fix: use the `keyboardVerticalOffset` attribute. 
  * `<KeyboardAvoidingView behavior='position' keyboardVerticalOffset={80}>`
* KeyboardAvoidingView strangeness on Android
  * in `AndroidManifest.xml`, set `android:windowSoftInputMode="adjustPan"` to the appropriate scene
    * See: [How to make your React Native app respond gracefully when the keyboard pops up](https://stackoverflow.com/questions/39344140/react-native-how-to-control-what-keyboard-pushes-up#answer-43208431)
  * add this to `app.json`
```
"androidStatusBar": {
    "backgroundColor": "#000000"
}
```

### Android Release Gotchas
* `Could not find or load main class java.se.ee` (when using `./gradlew assembleRelease`)
  * Remove this line from your `.bash_profile`: 
`export JAVA_OPTS='-XX:+IgnoreUnrecognizedVMOptions --add-modules java.se.ee'`
  * [GitHub thread](https://github.com/flutter/flutter/issues/16093#issuecomment-390489264)

* `Could not get unknown property 'release' for SigningConfig container.`
  * Just put the `signingConfigs` block on top of `buildTypes` block in your `build.gradle`.
  * [GitHub thread](https://github.com/researchgate/gradle-release/issues/187)
* `Task 'installRelease' not found in root project`
  * Check for `signingConfig` in `buildTypes` > `release` (in `app/build.gradle`)
    * [GitHub issue](https://github.com/facebook/react-native/issues/16854#issuecomment-348376236)
* `adb` can't find connected device (Mac OSX)
  * Solution: 
    1. Find device VendorID in System Preferences. 
    1. `echo [VENDOR_ID] >> ~/.android/adb_usb.ini`
    1. `adb kill-server ; adb devices`
  * [SO Answer](https://stackoverflow.com/questions/7135999/adb-not-finding-my-device-phone-macos-x#answer-7136003)
* `INSTALL_FAILED_UPDATE_INCOMPATIBLE`
  * Solution: 
    * On device, uninstall the app and try again. 
* Debugging release build crashes
  * `adb logcat AndroidRuntime:E *:S` will tail the logs of a connected device.


### Development Tools

* [expo/awesome-expo: Useful resources for creating apps with Exponent](https://github.com/expo/awesome-expo)
* [react-native-debugger](https://github.com/jhen0409/react-native-debugger)
  * [react-native-debugger-open](https://github.com/jhen0409/react-native-debugger/tree/master/npm-package) to have it open automatically
* [remote-redux-devtools](https://github.com/zalmoxisus/remote-redux-devtools)


### Redux

* [rematch/rematch: A Redux Framework](rematch/rematch: A Redux Framework)
* [Versent/redux-crud: A set of standard actions and reducers for Redux CRUD Applications](https://github.com/Versent/redux-crud)
* [React Native with Redux-Form](https://medium.com/wolox-driving-innovation/https-medium-com-wolox-driving-innovation-easy-forms-in-react-native-with-redux-form-1cdc16a9a889)


### Navigation

* [wix/react-native-navigation: A complete native navigation solution for React Native](https://github.com/wix/react-native-navigation/)
* [react-navigation/react-navigation: Routing and navigation for your React Native apps](https://github.com/react-navigation/react-navigation)
* [Preventing double taps in react-navigation](https://github.com/react-navigation/react-navigation/issues/271#issuecomment-278901237)

### UI Libraries

* [NativeBase | Essential cross-platform UI components for React Native](https://nativebase.io/)
* [react-native-material-ui: Highly customizable material design components for React Native](https://github.com/xotahal/react-native-material-ui)

### UI Components

* [react-native-snap-carousel](https://github.com/archriss/react-native-snap-carousel)
* [alexbrillant/react-native-deck-swiper: tinder like react-native deck swiper](https://github.com/alexbrillant/react-native-deck-swiper)


### Uncommon Stuff

* Sending background (without UI) emails 
  * Original repo: [react-native-mailcore](https://github.com/agenthunt/react-native-mailcore)
  * Also [my fork of this library](https://github.com/mcavaliere/react-native-mailcore) (includes "From:" and "To:" headers for deliverability)


### Debugging Notes

* Debugging AsyncStorage in `react-native-debugger`
  * Type `showAsyncStorageContentInDev()` in console
