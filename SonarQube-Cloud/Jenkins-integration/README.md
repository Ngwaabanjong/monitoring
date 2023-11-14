STEPS:
1. ## Create Account:
- https://sonarcloud.io/
- Login: with GitHub Account

2.  ## Generate an authentication token on SonarQube:
	- Account --> my account --> Security --> Generate Tokens
	- xxxxxx49b24ada457xxxxxxxxfa670b879xxxxx

3.  ## Create Credentials for token in Jenkins:
	- Manage Jenkins --> manage credentials --> system --> Global credentials --> add credentials  - Credentials type: Secret text  -> Secret: insert the token  -> ID: sonarqube-key.

4.  ## Download SonarQube Scanner" plugin on Jenkins:
	- Manage Jenkins --> Available plugins     Search for sonarqube scanner.
	- Make sure you download so you can see it in Jenkins.

5.  ## Configure SonarQube Server:
	- Manage Jenkins --> Configure System --> sonarqube server    
    - Add Sonarqube server    
    - Name: sonar-server    
    - Server URL: https://sonarcloud.io/    
    - Server authentication token: sonarqube-key

6.  ## Add SonarQube Scanner to Jenkins:
	- Manage Jenkins --> tools --> Sonarqube scanner -> Add SonarQube Scanner  ->  Give name: sonarqube-scanner -> select latest version. 
	- Apply and save.

7.  ## Create Organization on Sonar Qube:
	- Profile -> my account -> Organization 
	- Create Account -> name: mysonar1 -> Key: mysonar1-key -> Create
	- Click on Analize new project
	- Create project -> give prj name: myjkcicd -> Key: mysonar1-key_myjkcicd -> create
	- On Information you will see the keys.

8. ## Create Organization:
   Make sure you copy each name and key name on a nodepad.
	- On profile: click Orgamizations -> create.
	- Create an Organization manually -> name -> key name.
	- Free plan
        ## Create Project
   	- In the create organization
   	- Create project -> name -> project key name
   	- On project click information to see details on the just created project. 

10.  Create SonarQube properties file:
	- Browse: sonarqube properties file
**Property file Code:**
- Filename with no extension: **sonar-project.properties**
``````
sonar.verbose=true
sonar.organization=<insert sonarqube organization key name>
sonar.projectKey=<insert sonarqube project key name>
sonar.projectName= <insert sonarqube project name>
sonar.language=java
sonar.sourceEncoding=UTF-8
sonar.source=.
sonar.java.binaries=target/classes
sonar.coverage.jacoco.xmlReportPaths=tagrget/site/jacoco/jacoco.xml
``````

10. Add SonarQube properties file in Source Code Directory;
	- On your GitHub root add the file.

11. Add SonarQube stage in the Jenkinsfile:
	- Browse: sonarqube stage for Jenkinsfile.

11a. **Add SonqrQube Scanner Stage:**
``````
  stage('SonarQube analysis') {
  environment {
    scannerHome = tool 'sonarqube-scanner'
  }
  ``````
11b. **Add SonarQube Steps:**
``````
  steps{
    withSonarQubeEnv('sonar-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
``````
12. On SonarQube:
	- Go to project main directory and see report details.
	- Click information
	- Click main branch and view each page

13. Quality Gates:
	- SonarQube have inbuild quality Gates which defines the state of the code
	- But we can Build a Manual Quality Gate which will determine if our code is a pass or fail.
    - Go to your organization and see Qualify Gate features. 
