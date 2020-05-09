# Jenkins-Code-Deployment
This is a project which mentions the steps (along with screenshots) to do a Jenkins Deployment Using a War File.

Step 1: Push the code which you want deploy to the github.

Step 2: Install the Jenkins on your Local.

Step3: If you are deploying a Maven Project, install Maven on your local along with Java. Setup MAVEN_HOME, JAVA_HOME, M2_HOME variables in System Variables.

Step4: In the Jenkins, go to "Manage Jenkins" option and set up the JDK and Maven Insallation folders (point to your local directories)
Refer screenshot 1 and 2.

Step5: create a new job in jenkins, by selecting new job option on the jenkins UI and configure the "source code management" and point it to

your github repo where the code resides.If your github has credentials, provide that in the credentials option.

In the Build option, specify "pom.xml", default value when deloying in Jenkins using project type as "Maven".

Now, in the post build speciy the .war location of application. .WAR file will gets generated when you run "mvn clean install" in your maven project using maven war plugin in pom.xml. The genartion of .WAR is taken care
in this Jenkins by the command "clean install package" which we specified in "Goals and Options" in Build step.

Now specify the tomcat url where the application has to be deployed (can be a local tomcat or a remote running tomcat). Also, specify the credential for that tomcat(credential is mandatory).

Step6: Do a build now on your jenkins project, this will build and deploy your .WAR file on the tomcat running locally or remote. You can verify this by going to localhost followed
by the server port number of tomcat and "name of warfile". Example: http://localhost:8080/webapps as in our case. The default page of your application (index.html or any other) will be rendered in the UI.

Also, you can verify this by going to the tomcat folder and there you will see your application .WAR file copied which means jenkins copied the .WAR file generated using the build job
in Jenkins (build and post deploy steps mentioned in configure interface). 
