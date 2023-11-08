pipeline {
    agent { node { label 'AGENT-1' } }
    stages {
        stage('Install Dependencies'){
            steps {
                sh "npm install"
            }
        }
        stage('unit test'){
            steps {
                echo "unit testing is done here"
            }
        }
        //sonar-scanner command expect sonar-project.properties should be available
        //stage('sonar scanner'){
          //   steps {
            //    sh 'ls -ltr'
              //  sh 'sonar-scanner'
            //}
        //}
        stage('Build'){
             steps {
                sh 'ls -ltr'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deployment"
            }
        }
    }
    post{
        always{
            echo 'Cleaning up workspace'
            deleteDir()
            }
        }
    }


    
    
    
    
    
    