pipeline {
    agent any
   
    tools{
        nodejs 'nodejs'
    }

    stages {
        stage('GIT CHECKOUT') {
            steps {
                git branch: 'master', changelog: false, poll: false, url: 'https://github.com/roxsross/web-nodejs-basic.git'
            }
        }
        
        stage('Intall Dependencies') {
            steps {
               sh "npm install"
            }
        }        
        
        stage('Docker build and Push') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-new') {
                        sh "docker build -t demonodejs ."
                        sh "docker tag demonodejs roxsross12/nodejs:latest"
                        sh "docker push $REGISTRY/nodejs:latest"
    
                    }
                }
               
            }
        }
        
        stage('Docker Deploy') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-new') {
                        sh "docker run -d --name latestnode -p 8081:8081 roxsross12/nodejs:latest"    
                    }
                }
               
            }
        }
    }
}
