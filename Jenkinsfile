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
        stage ('Build '){
            steps{
                echo "Hello World"
            }
        }
        stage ('Deploy' ){
            steps{
                echo "Deployed Artifact"
            }
        }
    }
}
