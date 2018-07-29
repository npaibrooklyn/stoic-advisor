# Demo
https://stoic-advisor.appspot.com/vue-gen.html  
Demonstrates a simple form validation and submit using Ajax to a mock REST API



# Credits
* This project was build using the Vue.js webpack template at:  
https://github.com/vuejs-templates/webpack/tree/develop/template  

* Documentation for the template is here:  
https://vuejs-templates.github.io/webpack/

* I tweaked the files in build/ and config/ folder in following ways:   
    * Generate frontend files into the src/main/webapp/ folder of App Engine (instead of the dist/ folder) as per: 
        https://vuejs-templates.github.io/webpack/backend.html  

    * Changed the name of generated index file (from index.html to vue-gen.html) and assets folder (from static/ to vue-gen/)



# One time setup
* Signup for Google cloud account at https://console.cloud.google.com/ and enable billing

* Download and install Google cloud SDK at https://cloud.google.com/sdk/

* Download and install JDK 8 at http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

* Download and install the latest version of Eclipse IDE for Java developers

* Install Cloud tools for Eclipse plugin at https://cloud.google.com/eclipse/docs/quickstart

* Install homebrew: 
    ```
    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    ```

* Install npm: brew install node

* Download and install maven:   
    * https://maven.apache.org/download.cgi  
    * https://maven.apache.org/install.html



# Building Vue.js app
```
## Install dependencies (one time only; creates the node_modules folder)
npm install

## Serve with hot reload at localhost:8080
npm run dev

## Build for production with minification. This will generate the 
## src/main/webapp/vue-gen folder and src/main/webapp/vue-gen.html file
npm run build

## Build for production and view the bundle analyzer report
npm run build --report
```



# Deploy and start the web app on App Engine in Google cloud using Eclipse
#### Generate the Vue.js app
```  
npm run build
```

#### Deploy and start App Engine app using either Maven or Eclipse  
##### Using Maven 
```
mvn appengine:deploy  
```    
  
##### Using Eclipse
* Right click on project in Eclipse and click "Deploy to App Engine Standard...".

* In the resulting window, select the google account associated with the cloud console and 
    select cloud project (for example: stoic-advisor) to push the application to. 

* Also, check the following: 
    * "Promote deployed version to receive all traffic", 
    * "Stop previous version",
    * "Include optional app engine configuration files" 

* Click "Deploy"

* Go to the website, for example: https://stoic-advisor.appspot.com/vue-gen.html 



# Running locally on App Engine using Eclipse
#### Generate the Vue.js app
```
npm run build
```

#### Run App Engine locally
* Right click on the project

* Run as... -> App Engine

* Got to http://localhost:8080/vue-gen.html



# Maven
#### See all available maven goals
```
mvn help:describe -Dplugin=appengine
```

You will see something like this:
```
appengine:deploy
  Description: Stage and deploy an application to Google App Engine standard
    or flexible environment.

appengine:deployCron
  Description: Stage and deploy cron.yaml to Google App Engine standard or
    flexible environment.

appengine:deployDispatch
  Description: Stage and deploy dispatch.yaml to Google App Engine standard
    or flexible environment.

appengine:deployDos
  Description: Stage and deploy dos.yaml to Google App Engine standard or
    flexible environment.

appengine:deployIndex
  Description: Stage and deploy index.yaml to Google App Engine standard or
    flexible environment.

appengine:deployQueue
  Description: Stage and deploy queue.yaml to Google App Engine standard or
    flexible environment.

appengine:genRepoInfoFile
  Description: Generates repository information files for the Stackdriver
    Debugger.

appengine:help
  Description: Display help information on appengine-maven-plugin.
    Call mvn appengine:help -Ddetail=true -Dgoal=<goal-name> to display
    parameter details.

appengine:run
  Description: Run App Engine Development App Server synchronously.

appengine:stage
  Description: Generates a deploy-ready application directory for App Engine
    standard or flexible environment deployment.

appengine:start
  Description: Starts running App Engine Development App Server
    asynchronously.

appengine:stop
  Description: Stops a running App Engine Development App Server.

```

Run one of the goals, for example:  
mvn appengine:deploy



# Documentation
 * Vue.js: https://vuejs.org/v2/guide/


