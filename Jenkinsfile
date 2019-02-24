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
        stage ('Deploy Build in Staging Area'){
            steps{
                echo "Starting freestyle Jenkins project ..."
                timeout (time: 1, unit: 'MINUTES'){
            		input message: 'Waiting for successful artifact archivisation'
            	}
                build job : 'Deploy_StagingArea_Pipeline'
            }
        }
        stage ('Deploy to production' ){
            steps{
            	timeout (time: 2, unit: 'MINUTES'){
            		input message: 'Approve PRODUCTION Deployment?'
            	}
                build job : 'Deploy_Production_Pipeline' 
            }
            post{
            	success{
            		echo "Deployment on PRODUCTION is Successfull"
            	}
            	failure{
            		echo "Deployment Failure on PRODUCTION"
            	}
            }
        }
    }
}
