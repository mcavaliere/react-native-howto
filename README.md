# react-native-howto
A collection of links and references for all things React Native. 

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






### Development Tools

* [expo/awesome-expo: Useful resources for creating apps with Exponent](https://github.com/expo/awesome-expo)

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


### Debugging Notes

* Debugging AsyncStorage in `react-native-debugger`
  * Type `showAsyncStorageContentInDev()` in console
