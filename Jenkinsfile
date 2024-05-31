pipeline {
    agent any
    
    tools{
        nodejs 'nodejs'
    }

    stages {
        stage('GIT CHECKOUT') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/roxsross/web-nodejs-basic.git'
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
                    withDockerRegistry(credentialsId: 'docker-new', toolName: 'docker') {
                        sh "docker build -t demonodejs ."
                        sh "docker tag demonodejs roxsross12/nodejs:latest"
                        sh "docker push roxsross12/nodejs:latest"
    
                    }
                }
               
            }
        }
        
        stage('Docker Deploy') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-new', toolName: 'docker') {
                        sh "docker run -d --name latestnode -p 8081:8081 roxsross12/nodejs:latest"
    
                    }
                }
               
            }
        }
    }
}
