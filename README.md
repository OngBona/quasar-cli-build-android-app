# Quasar App (second-app)

A Quasar Framework app

## Install the dependencies
```bash
npm install
```

### Start the app in development mode (hot-code reloading, error reporting, etc.)
```bash
quasar dev
```

### Lint the files
```bash
npm run lint
```

### Build the app for production
```bash
quasar build
```

### Customize the configuration
See [Configuring quasar.conf.js](https://quasar.dev/quasar-cli/quasar-conf-js).

## Build android application

```bash
quasar build -m cordova -T android --stacktrace
```
`cd src-cordova`

[doc](https://cordova.apache.org/docs/en/9.x/reference/cordova-cli/index.html#page-toc-source)
```bash
cordova build android --verbose
```
## Run Application on emulator
```bash
 quasar dev -m android
 ```