pipeline {
    agent any
    stages {
        stage ('Build Servlet Project') {
            steps {
               //echo "Initializing the Code File"
               /* For Windows machine */
               bat 'mvn clean package'
               
               /* For Mac & Linux machine */
               //sh 'mvn clean package'
            }
            post {
            	success{
            		echo "Now archiving"
               		archiveArtifacts artifacts : '**/*.war'
            	}
            }
        }
        stage ('Deploy Build inStaging Area'){
            steps{
                echo "Starting freestyle Jenkins project ..."
                build job : 'Deploy_StagingArea_Pipeline'
            }
        }
        stage ('Deploy' ){
            steps{
                echo "Deployed Artifact"
            }
        }
    }
}
