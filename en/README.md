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

### React-native Installation Guide [#referência](https://facebook.github.io/react-native/docs/getting-started.html):
* Abra um prompt de comando em modo administrador, não importando o diretório.
* Open the command prompt with elevated rights.
* Type `npm install react-native-cli -g` and press `ENTER` to install the react-native globally **(Maybe this will take several minutes to finish, just wait)**.
	
### Creating your first project:
* Abra um prompt de comando já com o caminho onde irá ficar a pasta de seu projeto selecionado. Ex: Seu projeto é `C:\Temp\meuprojeto` abra o prompt em `C:\Temp`.
* Open the command prompt with elevated rights.
* Type `react-native init nameofyourproject` and press `ENTER` **(The react-native files will be downloaded and will take several minutes to finish, just wait)**.
	
### Rodando o projeto no emulador (AVD):
* Caso queira rodar em um AVD, basta seguir [este](https://developer.android.com/studio/run/managing-avds.html) tutorial para a criação e execução do AVD de acordo com o device.
* Depois de instalado, verifique se o device aparece na lista do ADB (Android Debug Bridge) digitando o seguinte comando: "adb devices"
	- Caso o device não apareça na lista, reinicie a maquina.
* Depois de conseguir visualizar o device no ADB, basta executar o comando `react-native run-android` na pasta de seu projeto.
* Se tudo correr bem, o APK será instalado na AVD e já será executado.

### Rodando em seu dispositivo físico:
* Plugue seu device no computador pelo USB.
* Abra o prompt de comando e digite `adb devices` para verificar se seu dispositivo está na lista.
	- Caso seu dispositivo não esteja na lista, tente reiniciar ou reinstalar os drivers.
* Caso seu dispositivo esteja na lista, digite o comando `adb reverse tcp:8081 tcp:8081`. Este comando serve para indicar ao device a porta correta de I/O que ele irá se comunicar com o ADB.
	- Este comando deve ser executado sempre que o dispositivo for plugado na maquina.
* Por fim, execute o comando `react-native run-android` na pasta do seu projeto.
* Se tudo correr bem, o APK será instalado em seu device e já será executado.
	
### Habilitando Hot Reload:
* O Hot Reload serve para que seu dispositivo ou AVD seja atualizado em tempo real com as modificações feitas sempre que o documento é salvo.
* Para habilitá-lo no device, balence o aparelho para aparecer o menu e clique em `Enable Hot Reload`.
* Para habilitá-lo no AVD, aperte Ctrl+M para abrir o menu e clique em `Enable Hot Reload`.
	
### Debugando sua aplicação:
* Abra o menu no device ou AVD e clique em `Debug JS Remotely`, se tudo correr bem, uma aba do Chrome será aberta e você poderá abrir a developer tools e debuggar como se debuga um javascript normal.
* Caso queira ver logs disparados pelo JAVA, basta abrir o prompt de comando e digitar `adb logcat`, isso ira mostrar todo o log JAVA e também os logs que irão aparecer em tempo real.

### Desplugando o device:
* Se você tentar remover o dispositivo com segurança, será alertado de que não é possível pois está sendo utilizado por outro processo. Isso ocorre por que ele está em constante comunicação com o ADB. Para conseguir remover, basta digitar o comando `adb kill-server`.
		
### Gerando versão final do APK (Signed APK):
* Para gerar um apk em versão "release" deve-se realizar algumas configurações.
* Primeiro você deve gerar uma keystore para seu aplicativo. Esta keystore deve ser guardada para sempre, pois é através dela que a Play Store guarda os dados de download, hating e etc.
* Para gerar a keystore você pode seguir [este](http://facebook.github.io/react-native/releases/0.39/docs/signed-apk-android.html) tutorial, porém eu achei mais fácil fazer pelo Android Studio.
* Para gerar através do Android Studio, basta abrir o menu `Build > Generate Signed APK`.
* Em seguida clique em `Create new` para criar uma nova keystore.
* Escolha a pasta de destino da chave o seguinte caminho `..caminhoDoProjeto/android/app/` e salve nesta pasta.
* Agora em seu projeto, abra o arquivo `gradle.properties` e insira as seguintes variáveis:

```
MYAPP_RELEASE_STORE_FILE=nomedoarquivo.keystore
MYAPP_RELEASE_KEY_ALIAS=nomedoalias
MYAPP_RELEASE_STORE_PASSWORD=****
MYAPP_RELEASE_KEY_PASSWORD=****
```
	
* Abra agora o arquivo `app/build.gradle` e adicione as seguintes configurações:

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

* Para gerar o APK você pode gerar por linha de comando ou pelo android studio. Eu recomendo por linha de comando pois o Android Studio demora para abrir.
* Para gerar por linha de comando, primeiro execute o seguinte comando na pasta do seu projeto: `cd android && gradlew assembleRelease`.
	- Caso compile com sucesso, o APK será gerado na pasta `...caminhoDoProjeto/android/app/build/outputs/apk/` com o nome de `apk-release.apk`.
* Para gerar pelo Android Studio, basta clicar em `Build > Generate Generate Signed APK` em seguida clicar em `Next`, escolher a pasta `...caminhoDoProjeto/android/app/build/outputs/apk/` e clicar em `Finish`.
	- Caso compile com sucesso, o APK será gerado na pasta "...caminhoDoProjeto/android/app/build/outputs/apk/" com o nome de "apk-release.apk".
	- Caso queira testar a versão release em seu device ou AVD, basta executar o comando `react-native run-android --variant=release`.
 
# Problemas encontrados durando o desenvolvimento

* As vezes ao executar o comando `react-native run-android`, ocorre um problema na compilação dizendo que alguma pasta ou arquivo não pode ser criado. Neste caso basta executar novamente o comando que irá funcionar normalmente. Não descobri por que acontece isso, parece que algum processo fica preso no ADB.
* No início tive problemas em executar no meu device, mas realmente era problema de driver. Entrei no site da motorola e baixei o Motorola Device Manager e isso resolveu.
* As vezes quando instala algum pacote pelo NPM, você deve digitar o comando `react-native link nome-do-pacote`, este comando configura o pacote no seu projeto e está descrito na documentação de todos os pacotes. Porém, já aconteceu do comando estar desatualizado no pacote que baixei, e ele não executar todo o processo de configuração. Sendo assim, recomendo verificar sempre a parte de instalação manual que os pacotes geralmente possuem.
* Tive problemas com um GIF animado que utilizava como loading. Ele simplesmente não animava. Depois de pesquisar achei [esta](http://facebook.github.io/react-native/releases/0.39/docs/image.html#gif-and-webp-support-on-android) documentação e tudo funcionou normalmente.
* Alguns problemas ocorrem também por não executar o prompt de comando como administrador, sendo assim, é bom sempre executar como administrador.
* Quando está com a opção `Debug JS Remotely` marcada, a função de `Hot Reload` não funciona muito bem, sendo assim, deve-se manualmente dar reload no aplicativo quando necessários abrindo o menu e clicando em Reload, ou então no caso de estar rodando em uma AVD, basta apertar duas vezes seguidas a tecla `R` do teclado com o foco na AVD.
* No início do desenvolvimento, percebi que a compilação estava extremamente lenta, levando cerca de 15 a 20 minutos. Depois de pesquisar muito e não achar a solução, consegui constatar que o meu problema era o proxy. Provavelmente na compilação o react-native deve fazer algumas verificações online ou algo assim. Sendo assim, resolvi o problema abrindo o arquivo `gradle.properties` e adicionando as seguintes variáveis:

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

* O problema de lentidão na compilação pode ser também por que você está com a opção `Debug JS Remotely` habilitada ao compilar.

### Contribuir
Sinta-se a vontade para abrir pull requests com algum problema e solução que encontrou durante o desenvolvimento.
