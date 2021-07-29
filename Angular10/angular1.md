# Angular Tutorial 1

## *Introduction to Angular*


1. Angular is open source type script based web development framework developed and maintained by google developers
2. A component-based framework for building scalable web applications
3. A collection of well-integrated libraries that cover a wide variety of features, including routing, forms management, client-server communication, and more
4. A suite of developer tools to help you develop, build, test, and update your code
5. Angular written in typescript language , supports **ivy engine** and **bazel script** 

------------------------------------------------------------------------------------------------

# Angular Tutorial 2

## *Folder Structure and Boot process for angular*

![Alt text](images/e2e.png?raw=true "e2e")
1. e2e folder 
    - folder included end to end test scripts 
    - app.e2e.spec.ts  : e2e says that this script is e2e test scrpt  && spec says when you add specification it becomes **functional** test scrips
    - app.po.ts : app.po.ts is the page object. This is really helpful and important. Here is the place where we will write the codes to find out the elements in our page or View. So, in future, if you are changing the selectors of your element, your changes will impact only in this file, so that you don’t need to change anything in your tests
    - proctactor.config.js : proctactor framework is used for end to end test


------------------------------------------------------------------------------------------------

![Alt text](images/nodemoduls.png?raw=true "node_modules") 
1. When we install new package or library it reside inside node modules

------------------------------------------------------------------------------------------------

![Alt text](images/src.png?raw=true "node_modules") 

![Alt text](images/src2.png?raw=true "node_modules") 

1. Src : This is main folder where we do development . 
     - this folder contains component ,modules ,pipes, services, directives
     - *.component.ts = this correspond to component
     - *.module.ts = this correspond to module file
     - *.service.ts = this corresponds to services file
     - *.component.spec.ts = this corresponds to **unit test scripts**
     - unit tests are written using jasmin framework
     - assets folder =  containes styles icons ie. static data 
     - env  = here you will define the variable or pipeline for dev qa prod 

2. pollyfils = if the browser will outdated then this file will help to do backword compatible with adding es6 functionality  

3. main.ts :
    - Booting the angular application
    - 

4. style.css : 
    - this is common css which are applicable for all components
    - best practices : Dont make it heavy . Add common style only to this file  

5. test.ts : this is the test script for booting process

------------------------------------------------------------------------------------------------

1. Angular.json : 
   - this is configuration for all our angular apllication 

2. Karma.conf.js : 
   - this is karma runner to runnig our karma unit test
   - configuration about test scripts which file to run and which file to skip etc

3. package.json
   - name : name of your application
   - version: version of your application 
   - scrips : it contains all commands to run the applications etc and you can configure scripts as per your req.
   - to understand any new project first refer to package.json
   - private : yes this is private repo : true
   - dependencies : dependencies are which are requires without which your applicaion will not work properly
   - when new package we install then this packafe will be added to dependencies
   - devDependecies : devdependencies are which you will work on development environment


4. package.lock.json
   - package-lock.json contains everything which requied to run your application in production mode
   - it containes all interdependencies also


5. tsconfig.json : add configuration for our typescript  , Exits only for build and compilation for our application 

6. tslint.json : linting configuration 

------------------------------------------------------------------------------------------------


# Booting Process for angular application 

1. main.ts file is which angular will check how to start the angular application 
2. we need at least one module in main.ts By default there is one module i.e appmodule 

```javascipt
// it imports bydefault appmodule bydefault and environmet
import { AppModule } from './app/app.module';
import { environment } from './environments/environment';

// if env is production then it will reduce size for css and all files do serve faster 
if (environment.production) {
  enableProdMode();

// bootstrapmodule is defined actual where angular application starts  ( Interview quetion )
platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
}
```

> notes : 1. we can change the bootstrap module 

3. All the code from main.ts is tested in test.ts 

------------------------------------------------------------------------------------------------

## Modules 

1. modules are logical functionality 
2. Exp. User Moudle 
    - register 
    - forgot password
    - signup
    - login
3. modules can have own componnents pipes, directives etc
4. we can load each module independetly when it needed. it helps to maintain , low load on browser , 
5. Every angular application has own module that is app module
6. We need to import required modules from inbuilt packages 
   - some Inbuild modules are : browsermodule , ngmodule  etc 

7. App.module.ts
    - Every module is defined by @ngmodule it is begining 
    - in **@ngmodule consiste of** :
       1. declarations : It consists we mention all components 
       2. imports: imports consiste of all the modules we required
       3. provides we add any servicess that we want to add 
       4. bootstrap : is which we tell module to which component to load first
       5. export : you are exporing the module and imporing to another module to use it



## Angular components (part -13)


1. component is smallest functinality that u execute in your application
2. when you group multiple components together then its become module
3. we can have parent child relationship in components
exp:
   1. Dashboard 
      1. display contact list
         1. contact grid 
         2. contact-options
         3. contact-export 


4. Each component have  .html .spec.ts  .ts .scss 
5. In .ts file @component decorator 
6. @component consist of  
   1. selector - unique identifier of the component 
   2. templateurl --> html code that u link ie .html file 
   3. styleurl --> this is style file path



## component lifecyle hooks (part-14)

1. Why do we need lifecycle hooks ?
   - while creating the component or loading component there may be lots of changes may happen like data loading, data change etc
   - to keep track of such chnages the lifecycle  hooks are implemented 

2. ngOnchanges() : 
   - used when you have input from anothe component or module
   - its called when data from input chanegs 
   - first called before ngoninit 

3. ngOnInit() :
   - used to initialise data in component 
   - called after input values are initialised 
   - default set by angular cli 
   - only once called

4. ngDoCheck()
   - Called when there is update detection or change detectios

5. ngAfterContentInit()
   - after first ngdocheck this method is called

6. ngAfterContentChecked()
   - called after every ngdockeck

7. ngafterviewInit():
   - initialise aftrer initailise all component and child components 

9. ngafterviewchecked()
   - called after content intiailised and checked 
   - called after every after content checked  is completed 

10. ngondestroy():
   - used when component is removed from dom 
   - fairly often used to unsubscribe from things like services 
   

## component communication (part-15)
- *exp :*

1. contact-module
   - contact-component-child1 
       - contact-component-subhild1
       - contact-component-subhild2
   - contact-component-child2

2. leads-module
   - leads-component-child1 
       - leads-component-subhild1
       - leads-component-subhild2
   - leads-component-child2

   #### Communications :
   - Related components :
   1. parent component -> child component  @input 
   2. parent componet <- child component   @output 

   - Unrelated components :
   1. component 1 from module 1 <--> SERVICE <---> component 2 from module 2


### Angular Directives (part-17)

1. You cannot make angular application without directiive 
2. Angular directives are used to extend power of html by extending new syntax
3. Directive can change ,exxtend , modify the behaviour of DOM 


##### Note : In angluar string shold be `''`   like ngswtchcase ="'omkar'"

- Types of Directives 
   1. Component Directive 
      1. Every angular application must have at least one component
      2. have its own template
      3. events attached
         - app-component --> why they have its own template 
   
   2. structural directive 
      1. updates structure of view 
         - ngif , ngswitch , ngfor 
      
   3. Attributes directives 
      1. updates attributes of view 
         - ngstyle ,ngclass 
            - ngstyle helps to style dom elements 
            - you can add dynamic value via ngstyle
            - <div [ngStyle] = "{'background_color':styleDynmivar}">
            - <div [ngClass] = "'c1'">
            - <div [ngClass] = "'c1 c2'">
            - <div [ngClass] = "clsNameVarTs">
            


   4. Custom Directives 
      1. create `ng g d <-DirName->`


## Data Binding (part - 24)
1. Bind data from component.html to component.ts
2. Its defines basicaaly how data flows and data updated based on buisness logic 

**Types Of Data Binding**

1. One Way Data Binding:
     - Component to view 
       - Interpolation
          - Its technique bind data from component to template 
          - string , objects , arrays etc
          - Use : `{{VaraibleName}}`
       - Property Binding
       - Style Binding
       - Attribute Binding
     - views-component 
       - Event Binding
2. Two way data binding :
    - template <--> component.ts

    




       