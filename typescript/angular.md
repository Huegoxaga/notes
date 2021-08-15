# Angular

## Introduction

* is a TypeScript-based open-source web application framework.
* It provides a completed solution for building website.
* Use Hot Module Replacement, compile the code whenever modified codes are saved.
* Convert TypeScript file into the following js bundle files using Webpack.
  * `polyfills.bundle.js` translate between different JavaScript versions for the browsers.
  * `main.bundle.js` source code.
  * `style.bundle.js` style sheet.
  * `vendor.bundle.js` third-party libraries.
  * `inline.bundle.js`
* The bundle files are injected into the `index.html` at runtime.
* when importing a file, file extension `.ts` is not needed in Angular.

## History

* This project is led by Google.
* AngularJS is Angular 1.X, released in 2010 and written in JavaScript.
* Angular 2, released in 2016, written in TypeScript.
* Angular 4 was announced in 2016. Angular 3 was skipped.
* Angular 8 is the current active version released on May 28, 2019.

## Setup a New Project

1. Install node latest stable version [here](https://nodejs.org/en/)
2. run `npm i -g @angular/cli` to instal Angular CLI. Prepend `sudo` for Mac.
3. In the project folder create run: `ng new project-name` to create a new project.
4. run `ng serve` or `npm start` to serve the website on `localhost:4200`
   * run `npm install` for install dependencies for imported projects
   * A local `@angular/cli` package will be installed for the project, its version should match global
5. run `ng build --prod --build-optimizer` to build and deploy the project
   * This will generate the `/www` folder inside current project folder

## Angular Web App Structure

* It is made up by components and modules.
* One Angular App has one app module call `AppModule`.
  * A component is a piece of UI.
* One Angular App has one `AppComponent` that holds everything together.
  * Modules contains all related components.

### In the Project Root Folder

* `index.html` is the actually webpage for the app that add `AppComponent`\(`app-root`\) and any customized components that `<app-root>` component has dynamically.
* `main.ts` is the entry point of the app that add the `AppModule` into the web app.
* `styles.css` is the global style sheet for the web app.

### In the `app` Folder

* `app.component.ts` is the AppComponent class definition.
* `app.component.html` the layout of the app component.
* `app.component.css` the style sheet of the app component.
* `app.module.ts` the AppModule definition.

```typescript
import { BrowserModule } from "@angular/platform-browser";
import { NgModule } from "@angular/core";
import { AppRoutingModule } from "./app-routing.module";
import { AppComponent } from "./app.component";
//import customized component.
import { ComponentComponentName } from "./component-name/component-name.component";
@NgModule({
  declarations: [
    AppComponent,
    ComponentName, //register the customized component in the app module.
  ],
  imports: [BrowserModule, AppRoutingModule],
  providers: [
    ServiceName, //register a dependency for all service in use.
  ],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

* Any other folders that hold files related to customized components.

## Customized Component

### Create Component

In project folder, run: `ng g c component-name`.

### Files

Each component is related to the following files.

* `component-name.component.ts`, this is the exported component class file.

  ```typescript
  import { Component, OnInit } from "@angular/core"; //import decorator.
  // The decorator function turns the class into a component with meta data.
  import { ServiceNameService } from "../service-name.service"; //import service
  @Component({
    selector: "app-component-name", // define the name of the component tag in app component html file.
    templateUrl: "./component-name.component.html", //link to the layout of the component.
    styleUrls: ["./component-name.component.css"], //link to the style sheet of the component.
  })
  export class ComponentTestComponent implements OnInit {
    dataName = 100; //Declare any data here for template file to use.
    arrayName = [1, 2, 3]; // data for demonstrate directive in template.
    serviceData;
    constructor(service: ServiceNameService) {
      //declare new service object and pass it as an argument.
      this.serviceData = service.anyFunction(); // get service data from service method.
    }
    ngOnInit() {}
  }
  ```

* `component-name.component.css`, this is style sheet for the component.
* `component-name.component.html`, this is template for the component.

  ```markup
  <!--in { {..} } data and methods from ts file can be used as an expression.-->
  <h1>{{dataName}}</h1>
  <ul>
    <!--ngfor directive work as for each loop the an array-->
    <!--* is required for any directive that will change the template structure-->
    <li *ngfor="let item of arrayName">{{item}}</li>
  </ul>
  ```

* `component-name.component.spec.ts`, this is used for component's unit testing.
* Lastly, newly created component is imported and registered in the AppModule class.

## Service

* Service is just a plain TypeScript class that holds variables, properties, and methods.
* Service can be used to handle any services that is not related to presentation of the components.
* Create service as the component constructor argument and register it in the module will allows the web app create one object and reuse it for the entire app.
* The single service object\(dependency\) created will be injected to all component class that uses it.

### Create Service

In project folder, run: `ng g s service-name`.

### Service File

* `service-name.service.ts` in the app folder.

```typescript
import { Injectable } from "@angular/core";
@Injectable({
  providedIn: "root",
})
export class ServiceNameService {
  anyFunction() {
    return "Here is the service.";
  }
  constructor() {}
}
```

* `service-name.service.spec.ts` in the app folder. It is used for unit test.

