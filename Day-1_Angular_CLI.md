# Angular CLI

> * [Setup & Basic Troubleshooting](https://github.com/cosmicdev2016/angular-sessions/blob/master/Day-1_Angular_CLI.md#angular-cli-setup--basic-troubleshooting)
> * [Upgrading Angular 4|5 Projects](https://github.com/cosmicdev2016/angular-sessions/blob/master/Day-1_Angular_CLI.md#upgrading-angular-45-projects)
> * [Upgrading Angular 2 Projects](https://github.com/cosmicdev2016/angular-sessions/blob/master/Day-1_Angular_CLI.md#upgrading-angular-2-projects)

## Setup & Basic Troubleshooting

Depending on the CLI version you're using, you might also need to add the `FormsModule`  to the `imports[]`  array in your `app.module.ts`  file (add it if you don't see it there). You might not fully understand what that all means but we're going to cover that in this course, no worries.

If you don't have `FormsModule`  in `imports[]`  in `AppModule` , please do add it and also add an import at the top of that file: `import { FormsModule } from '@angular/forms';` 

-----

If you want to **dive deeper into the CLI** and learn more about its usage, have a look at its official documentation: [https://github.com/angular/angular-cli/wiki](https://github.com/angular/angular-cli/wiki)

**You encountered issues during the installation of the CLI or setup of a new Angular project?**

A lot of problems are solved by making sure you're using the latest version of NodeJS, npm and the CLI itself.

**Updating NodeJS**

Go to nodejs.org and download the latest version - uninstall (all) installed versions on your machine first.

**Updating npm**

Run `[sudo] npm install -g npm`  (`sudo`  is only required on Mac/ Linux)

**Updating the CLI**

A reasonnable move is to keep your angular-cli version alligned with your angular version, otherwise you risk to stumble into incompatibilities issues. So getting the correct angular-cli version will lead you to getting the desired angular version.

To update Angular CLI to a new version, you must update both the global package and your project's local package.

Global package:
```
npm uninstall -g @angular/cli
npm cache verify
#if npm version is < 5 then use `npm cache clean` 
npm install -g @angular/cli@latest
#or for a specific version
npm install -g @angular/cli@wished.version.here
```

Local project package:
```
rm -rf node_modules dist
#use rmdir /S/Q node_modules dist in Windows Command Prompt; use rm -r -fo node_modules,dist in Windows PowerShell 
npm install --save-dev @angular/cli@latest
npm install
```

**Note:** As of writing this, could not find any compatibility matrix of Angular and @angular/cli.

**Here are some common issues & solutions:**

1. **Creation of a new project takes forever (longer than 3 minutes)**
That happens on Windows from time to time => Try running the command line as administrator.
2. **You get an EADDR error (Address already in use)**
You might already have another ng serve process running - make sure to quit that or use `ng serve --port ANOTHERPORT`  to serve your project on a new port.
3. **My changes are not reflected in the browser (App is not compiling)**
Check if the window running `ng serve`  displays an error. If that's not the case, make sure you're using the latest CLI version and try restarting your CLI.

-----

## Upgrading Angular 4|5 Projects

First, start by installing the Angular CLI 6 locally using the following command (Make sure you are inside your project's root folder):

`npm install @angular/cli@latest`

**Updating Configuration Files**

There are many differences between Angular 4|5 and Angular 6 such as

1. Angular 6 uses `angular.json` instead of `angular-cli.json`.
2. Different versions of dependencies in `package.json` etc.

You can update different configuration files automatically by running the following command from the project's root folder:

`ng update @angular/cli`

**Discovering Packages to Update**

Angular CLI has a new utility that allows you to automatcially analyze your project's `package.json` file and displays dependencies that need to be updated.

Using your terminal from the root folder of your Angular 5 project run the following command:

`ng update`

**Upgrading Core Packages to Angular 6**

Now you need to update the core packages/dependencies to Angular 6. Simply run the following command:

`ng update @angular/core`

**Upgrading RxJS**

You can update RxJS using the ng update command:

`ng update rxjs`

-----

## Upgrading Angular 2 Projects

First check your versions of installed Angular CLI and other dependencies with:

`ng --version` 

Next open your project `package.json` file then change the Angular CLI version. You can check the npm info page for Angular CLI package to find out the latest version.

Next, delete your project `node_modules` folder and run the following command:

`npm install`

You don't need to change the versions of the other dependencies, the Angular CLI will take care of fetching latest versions.

Now you can check again for installed versions with:

`ng --version` 
