pipeline {

    agent any
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
                  
    stage ("Lancement des Tests Unitaires"){
		steps{
			sh "mvn test"
				}
		}              
        	
    }
}
