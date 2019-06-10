# Simple Viewer App

Copyright © 2019 Bentley Systems, Incorporated. All rights reserved.

An iModel.js sample application that demonstrates opening an iModel and viewing its data. The data is presented using the following components:

* _Viewport_: Renders geometric data onto an HTMLCanvasElement.
* _Tree_: Displays a hierarchical view of iModel contents.
* _Property Grid_: Displays properties of selected element(s).
* _Table_: Displays element properties in a tabular format.

This app serves as a guide on how you can embed one or more of these components into your own application.
See http://imodeljs.org for comprehensive documentation on the iModel.js API and the various constructs used in this sample.

## Development Setup

1.	If you do not have a ProjectWise Project, register a sample one. Otherwise, you can skip this step.
	- If in *Production*, go to https://imodeljs.github.io/iModelJs-docs-output/getting-started/registration-dashboard/.
	- If in *QA*, go to http://builds.bentley.com/prgbuilds/AzureBuilds/iModelJsDocs/public/getting-started/registration-dashboard/.
	Go to [Registered Products], and select [+ New Project].
	Under [iModel Source], use the sample [Bentley Example] with the [Retail Building Sample] selection.
	
	For more information, see the section on [authorization](https://imodeljs.github.io/iModelJs-docs-output/learning/common/accesstoken/.

2.	Open Command Prompt and navigate into the directory of the viewer application.

3.	In Command Prompt, type *code .* to open the directory in Visual Studio Code.

4.	Edit [src/common/config.json] with your project name and iModel name.

5.	Find the following line of code in [src/common/configuration.json]:
	*	imjs_buddi_resolve_url_using_region: "102",
	- If in *Production*, comment this out.
	- If in *QA*, leave it uncommented.

6.	Type [Ctrl + `] to open the terminal in Visual Studio Code.

7.	Type the following command in the terminal to install the dependencies:
	*	npm install

8.	Type the following command in the terminal to build the application:
	*	npm run build
	
9.	Type the following command in the terminal to run the application:
	*	npm run start:servers
	
	There are two servers, a web server that delivers the static web resources (the frontend Javascript, localizable strings, fonts, cursors, etc.),
	and the backend RPC server that opens the iModel on behalf of the application.
	This starts them both running locally.

10.	Open a web browser (e.g. Chrome, Edge), and navigate to the following:
	*	localhost:3000

[//]: # (Commented out until Electron version fixed. Note: The Electron version is meant to run on desktops, but will currently not work within a virtual machine.)

![Screenshot of the application](./docs/header.png)

## Testing

Run both e2e and unit tests with `npm test`

### End-to-end tests

You can run just end-to-end tests with `npm run test:e2e`. But it takes a while
to build and start the tests, so if want to actively change something within them,
first launch the app with `npm run test:e2e:start-app` and when it's done `npm run test:e2e:test-app`

If you want to see what tests do behind the scenes, you can launch them in non
headless mode. Edit the file in *./test/end-to-end/setupTests.ts* and add

```js
{ headless: false }
```

to puppeteer launch options. Like this

```ts
before(async () => {
  browser = await Puppeteer.launch({ headless: false });
});
```

### Unit tests

Run with `npm run test:unit`

## Purpose

The purpose of this application is to demonstrate the following:

* [Dependencies](./package.json) required for iModel.js-based frontend applications.
* [Scripts](./package.json) recommended to build and run iModel.js-based applications.
* How to set up a simple backend for
  [web](./src/backend/web/BackendServer.ts) and
  [electron](./src/backend/electron/main.ts).
* How to set up a simple [frontend for web and electron](./src/frontend/api/SimpleViewerApp.ts).
* How to [implement OIDC sign-in](./docs/oidc.md) to get access to iModels on iModelHub.
* How to [consume](./src/frontend/components/App.tsx) iModel.js React components.
* How to implement unified selection between a
  [viewport](./src/frontend/components/Viewport.tsx),
  [tree](./src/frontend/components/Tree.tsx),
  [property grid](./src/frontend/components/Properties.tsx) and a
  [table](./src/frontend/components/Table.tsx).
* How to include
  [tools](./src/frontend/components/Toolbar.tsx) in a
  [viewport](./src/frontend/components/Viewport.tsx).

## Contributing

[Contributing to iModel.js](https://github.com/imodeljs/imodeljs/blob/master/CONTRIBUTING.md)
