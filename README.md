# The Governance Events Sample

The Gov-Events-Sample project provides a sample application that renders some amazing charts showing Information Server events statistics. The statistics are gathered by an Events Kafka client sample deployed on the Information Server side.

## What you'll need

* A [Bluemix](https://developer.ibm.com/sso/bmregistration?lang=en_US&ca=dw-_-bluemix-_-wa-simplenode1-app-_-article) account
* A [DevOps Services](https://hub.jazz.net/?utm_source=dw&utm_campaign=bluemix&utm_content=wa-simplenode1-app&utm_medium=article) account

## Building the sample app on Bluemix

Use the magical buttonbelow to automatically deploy this sample application to Bluemix. 

0. Click <a href="https://bluemix.net/deploy?repository=https://github.com/grassmik/governance-events" target="_blank"><img src="http://bluemix.net/deploy/button.png" alt="Bluemix button" /></a> to open the Deploy to Bluemix page.
0.Log in to or sign up for Bluemix.
0.Name your new app and specify any options as needed if you do not like the defaults.
0.Click DEPLOY.

When the deployment is completed, a private DevOps Services project is set up. The project contains a running instance of the sample application, a configured build pipeline and a dedicated Git repository that you can use to make updates to the application.

After the application is deployed, you need to complete the build pipeline and rebuild the project with the following steps:

0. Click EDIT CODE
0. Click BUILD & DEPLOY to open the pipeline page
0. In the Build Stage, click the Stage Configuration icon and select Configure Stage
0. Modify the second line of the build script to "mvn -B package install"
0. In the Build Archive Directory field, enter "app"
0. Click SAVE
0. In the Build Stage, click the Run Stage icon. The Build Stage will automatically trigger the Deploy Stage. Wait for the Deploy Stage to finish.




0. Click **Open deployed application** to open the web interface. The application is now waiting for events sent by the Information Server Events Kafka client sample.

## Downloading the Information Server Kafka client

0. At the bottom of the deployed application, click on the **deployment page** link.
0. Follow the instructions to deploy the Events kafka client sample.

The application now updates the displayed charts as events come in.

## Building the source code:

The source code of the Bluemix application is available in the app.js and public/index.html files. 

The java source code Events Kafka client sample source is available in the src directory.

To build the Bluemix application and the Events Kafka client sample source code, follow these steps:

0. In your forked Bluemix project, click the **EDIT CODE** button to go to the edition view.
0. Click the **BUILD & DEPLOY** button to go to the pipeline view.
0. If not already defined, create a first step to build the project:
   * Give a name of your choice, for example Build.
   * In the "Input" tab, make sure that the input type is "SCM reference" and that the GIT referenced is correct.
   * In the "Work" tab, add a "Build" work, give it a name of your choice, for example "Build", select Maven as type, modify the build script to "mvn -B package install" and replace the output directory from default "target" to "app".
0. If not already defined, create a second step to deploy the project:
   * Give a name of your choice, for example Deploy.
   * In the "Input" tab, make sure that the input type is "building artefacts" and that previous step and work name are selected.
   * In the "Work" tab, add a "Deploy" work and give it a name of your choice, for example "Deploy". You can keep the default value of all other configuration parameters.

You can now edit the source code in your Bluemix project. Each time a code modification is synchronized into the GIT repository, the Bluemix app will be built and deployed automatically.
