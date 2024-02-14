# package.json

```

{
  "name": "soca14",
  "main": "main.js",
  "version": "0.0.1",
  "authors": "sc",
  "description": "scapp",
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "watch": "ng build --watch --configuration development",
    "test": "ng test",
    "serve:ssr:soca14": "node dist/soca14/server/server.mjs",
    "electron": "ng build --base-href ./ && electron .",
	  "dist": "ng build --base-href ./ && electron-builder"
  },
  "private": true,
  "dependencies": {
    "@angular/animations": "^17.1.0",
    "@angular/common": "^17.1.0",
    "@angular/compiler": "^17.1.0",
    "@angular/core": "^17.1.0",
    "@angular/forms": "^17.1.0",
    "@angular/platform-browser": "^17.1.0",
    "@angular/platform-browser-dynamic": "^17.1.0",
    "@angular/platform-server": "^17.1.0",
    "@angular/router": "^17.1.0",
    "@angular/ssr": "^17.1.2",
    "express": "^4.18.2",
    "rxjs": "~7.8.0",
    "tslib": "^2.3.0",
    "zone.js": "~0.14.3"
  },
  "devDependencies": {
    "@angular-devkit/build-angular": "^17.1.2",
    "@angular/cli": "^17.1.2",
    "@angular/compiler-cli": "^17.1.0",
    "@types/express": "^4.17.17",
    "@types/jasmine": "~5.1.0",
    "@types/node": "^18.18.0",
    "electron": "^28.2.2",
    "electron-builder": "^24.9.1",
    "jasmine-core": "~5.1.0",
    "karma": "~6.4.0",
    "karma-chrome-launcher": "~3.2.0",
    "karma-coverage": "~2.2.0",
    "karma-jasmine": "~5.1.0",
    "karma-jasmine-html-reporter": "~2.1.0",
    "typescript": "~5.3.2"
  },
  "build": {
    "appId": "software.cantrips",
    "productName": "SoftwareCantrips",
    "mac": {
      "category": "public.app-category.developer-tools"
    },
    "files": ["**/*", "dist/soca14/browser/**"]
  }
}


```

# main.js
```

const { app, BrowserWindow } = require('electron')
const url = require('url');
const path = require('path');
let mainWindow
function createWindow () {
  mainWindow = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      nodeIntegration: true
    }
  })
  mainWindow.loadURL(
    url.format({
      pathname: path.join(__dirname, `/dist/soca14/browser/index.html`),
      protocol: "file:",
      slashes: true
    })
  );
  // mainWindow.webContents.openDevTools()
  mainWindow.on('closed', function () {
    mainWindow = null
  })
}
app.on('ready', createWindow)
app.on('window-all-closed', function () {
  if (process.platform !== 'darwin') app.quit()
})
app.on('activate', function () {
  if (mainWindow === null) createWindow()
})

```


# Soca14

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 17.1.2.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
