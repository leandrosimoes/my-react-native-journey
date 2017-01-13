# my-react-native-journey
This is a personal repo that I put my throbleshotings, configurations and experiences with my react-native develope journey.

# My basic react-native script

### Basic device config:
* First of all your device must have Develop Mode activated, and you can do this on `Config > About` and than tap the `Version Number` multiple times.
* Doing this, the Develop Mode will be enabled in your device at `Config > Developer`.
* Open this menu and enable the `USB Depuration` option.
* After that, open the `Config > Security` menu and enable the `Unknow sources` option.

### Programs and IDE's Installation Guide:
* Node.js: [download](https://nodejs.org/en/).
* Android Studio: [download](https://developer.android.com/studio/index.html?gclid=Cj0KEQiAsrnCBRCTs7nqwrm6pcYBEiQAcQSznM4iv3JZqUhEyWeYAY5Bdr9dMNAYrH-dOihoYtv-gXYaAmOu8P8HAQ).
* VS Code: [download](https://code.visualstudio.com/).
* SDKS E ENVIRONMENT VARIABLES:
	- To install the SDK's I suggest to install the Android Studio and use it to verify which you have to install [here](https://facebook.github.io/react-native/docs/getting-started.html).
	- For environment variables I suggest to veriry [this](https://facebook.github.io/react-native/docs/getting-started.html).
* VS Code Config:
	- Open VS Code, press `F1`, type `Install Extensions` and press `ENTER`. Doing this, the extensions installation menu will be open.
	- Search by `VS Code React Standard Style snippets` and install the extension.
	- Search by `ESLint` and install the extension too. (Click [here](http://eslint.org/) if you want to know more about ESLint).
	- At the project folder, open the command prompt and type `npm install eslint -g`.
	- At the project folder, open the command prompt and type `npm install eslint-plugin-react --save-dev `.
	- At the project folder, open the command prompt and type `npm install eslint-plugin-react-native --save-dev `.
	- Back to VS Code, press `F1`, type `Create '.eslintrc.json' File` and press `ENTER`. Doing this, a `.eslintrc.json` file will be created inside the project folder. This file contains some basic ESLint configurations. Copy the configurations above and override this file content and restart your VS Code. Doing this, your VS Code will be ready to show errors and warnings abour react and react-native.

```json
{
    "env": {
        "browser": true,
        "commonjs": true,
        "es6": true,
        "node": true
    },
    "parserOptions": {
        "ecmaFeatures": {
            "jsx": true
        },
        "sourceType": "module",
        "ecmaVersion": 7
    },
    "rules": {
        "no-const-assign": "warn",
        "no-this-before-super": "warn",
        "no-undef": "warn",
        "no-unreachable": "warn",
        "no-unused-vars": "warn",
        "constructor-super": "warn",
        "valid-typeof": "warn",            
        "comma-dangle":"off",
        "react-native/no-unused-styles": "warn",
        "react-native/split-platform-components": "warn",
        "react-native/no-inline-styles": "warn",
        "react-native/no-color-literals": "warn",
        "react/prop-types": "off",
        "no-extra-boolean-cast": "off"
    },
    "plugins": [
        "react",
        "react-native"
    ],
    "extends": ["eslint:recommended", "plugin:react/recommended"],
    "settings": {
        "react": {
        "pragma": "React",
        "version": "0.14.8"
        }
    }
}
```

**OBS: The Android Studio installation is not required, by the way doing this will save you a lot of time, will be usefull to see some JAVA exceptions and warnings and very usefull to create the AVD (Android Virtual Devices). The VS Code installations is not required too, but this was the better choice for me.**

### React-native Installation Guide [#reference](https://facebook.github.io/react-native/docs/getting-started.html):
* Open the command prompt with elevated rights.
* Type `npm install react-native-cli -g` and press `ENTER` to install the react-native globally **(Maybe this will take several minutes to finish, just wait)**.
	
### Creating your first project:
* Open the command prompt with elevated rights.
* Type `react-native init nameofyourproject` and press `ENTER` **(The react-native files will be downloaded and will take several minutes to finish, just wait)**.
	
### Run the app on AVD:
* To create the AVD just follow [this](https://developer.android.com/studio/run/managing-avds.html) tutorial.
* To verify if the ADV is running, open the command prompt and type `adb devices`.
    - If the device is not running, reboot your pc.
* To run the app, open the command prompt on the project folder and type `react-native run-android`.
* If everything goes fine, the app will be installed and open on the AVD.

### Run the app on your device:
* Attach the device on pc.
* To verify if the ADV is running, open the command prompt and type `adb devices`.
* Abra o prompt de comando e digite `adb devices` para verificar se seu dispositivo está na lista.
    - If the device is not running, verify if the drivers are installed and reboot your pc.
* To run the app, open the command prompt on the project folder and type `react-native run-android`.    
* If everything goes fine, the app will be installed and open on the device.
	
### Enable Hot Reloading
* The Hot Reloading is used to update the changes on your device/AVD after save the code in real time.
* To enable on device, shake the device to open the menu and press `Enable Hot Reloading` option.
* To enable on AVD, press Ctrl+M to open the menu and press `Enable Hot Reloading` option.
	
### Debugging your app:
* Open the menu on device/AVD and press the `Debug JS Remotely` option. A new browser tab will be open. Now just open de developer tools to debug.
* If you want to see the JAVA logs, just open the command prompt and type `adb logcat`, this will show all JAVA log in real time.

### Detach your device:
* To detach your device safely, open the command prompt and type `adb kill-server`, than, detach your device.
		
### Build the Signed APK:
* To build the "release" APK you need to config some things.
* First you need to generate the your keystore app. This keystore can't be lost, this key is used by Play Store to store informations like download, hating, ect.
* To generate the keystore by command prompt just follow [this](http://facebook.github.io/react-native/releases/0.39/docs/signed-apk-android.html) tutorial.
* To generate the keystore by Android Studio (easiest way), open the Android Studio, then open the `Build > Generate Signed APK` menu.
* Now click on `Create New` option to criate a new keystore.
* Choose the `..projectFolder/android/app/` as destination folder.
* Now open the `gradle.properties` file and put this variables inside it:

```
MYAPP_RELEASE_STORE_FILE=filename.keystore
MYAPP_RELEASE_KEY_ALIAS=aliasname
MYAPP_RELEASE_STORE_PASSWORD=****
MYAPP_RELEASE_KEY_PASSWORD=****
```
* Now open the `app/build.gradle` and put this settings inside it:

```				
signingConfigs {
	release {
		storeFile file(MYAPP_RELEASE_STORE_FILE)
		storePassword MYAPP_RELEASE_STORE_PASSWORD
		keyAlias MYAPP_RELEASE_KEY_ALIAS
		keyPassword MYAPP_RELEASE_KEY_PASSWORD
	}
}
```

* To generate the app by command prompt, open the command prompt at your project folder and type `cd android && gradlew assembleRelease`.
    - If everything goes fine, the APK will be generated at `...caminhoDoProjeto/android/app/build/outputs/apk/` with the name of `apk-release.apk`.
* To generate the app by Android Studio, just open the `Build > Generate Generate Signed APK` menu and click `Next`, choose the `...caminhoDoProjeto/android/app/build/outputs/apk/` as the destination path and click on `Finish`.
    - If everything goes fine, the APK will be generated at `...caminhoDoProjeto/android/app/build/outputs/apk/` with the name of `apk-release.apk`.
* If you want to test the "release" APK on your device, just open the command prompt at the project folder and type `react-native run-android --variant=release`.
 
# Throbleshotings

* Sometimes when you execute the `react-native run-android` you will see some folder permissions erros, just run the command again.
* I have some driver problems to run on my MOTO G and I have to download the Motorola Device Manager to fix.
* Sometimes you have to install some NPM packages and then type `react-native link nome-do-pacote`. This command set the package necessary configs on the right locations, but sometimes this not work well, so I recommend to follow the packages documentations and config manualy.
* I have some problems to show animated GIF images and after some researches I found [this](http://facebook.github.io/react-native/releases/0.39/docs/image.html#gif-and-webp-support-on-android) solution.
* Some errros just occours becaouse the prompt command is not open with elevated rights.
* If the `Debug JS Remotely` option is enabled, the `Hot Reloading` option do not work so well and your have to reload manualy typing the `R` key two times on AVD or open the menu and click on `Reload` option on device.
* I have some extreme performance problems during the compilation (something about 15 or 20 minutes!) and after a LOT of researches I fix it after put this configurations on `gradle.properties` file:

```
systemProp.http.proxyHost=192.****
systemProp.http.proxyPort=****
systemProp.http.proxyUser=****
systemProp.http.proxyPassword=****

systemProp.https.proxyHost=192.****
systemProp.https.proxyPort=****
systemProp.https.proxyUser=****
systemProp.https.proxyPassword=****
```

* The extreme performance problems maybe can occour because you are compiling with the `Debug JS Remotely` enabled.

### Contribute
Feel free to open pull requests with your problems, solutions, etc.
