pipeline {
  agent any
	environment {
        // This can be nexus3 or nexus2
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "localhost:8081/Nexus"
        // Repository where we will upload the artifact
        NEXUS_REPOSITORY = "Releases"
        // Jenkins credential id to authenticate to Nexus OSS
        NEXUS_CREDENTIAL_ID = "admin:azerty123"
    }

   // triggers {
     // cron('*/4 * * * *')

//    } 

    stages {
        stage ('GIT') {
             steps {
                echo "Getting Project from Git"; 
                git branch:"main", url : "https://github.com/sami1895/projetjenkins1.git"; 
             }
          }

       stage("Verification du version Maven") {
           steps {
                sh "mvn -version"
              
            }
        }
    stage("Supprimer le contenu du dossier target") {
            steps {
                script {
                    //this step attempts to clean the files and directories generated by Maven during its build
                    sh "mvn clean"
                }
            }
        }
      
   stage ('creation livrable') {  
             steps {
                  sh "mvn package -DskipTests=true"
                  
                  }
                  } 
                  
 //   stage ("Lancement des Tests Unitaires"){
	//	steps{
		//	sh "mvn test"
			//	}
	//	}              

	  stage("Deploiement dans nexus ") {
     		 steps{
                          }
  			sh "mvn deploy"
                }  
    }
}
