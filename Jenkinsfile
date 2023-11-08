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
                sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip'
            }
        }
        //install pipeline utility steps plugin, if not installed
        stage('Publish Artifact') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '172.31.32.147:8081/',
                    groupId: 'com.roboshop',
                    version: "$packageVersion",
                    repository: 'catalogue',
                    credentialsId: 'nexus-auth',
                    artifacts: [
                        [artifactId: 'catalogue',
                        classifier: '',
                        file: 'catalogue.zip',
                        type: 'zip']
                    ]
                )
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


    
    
    
    
    
    