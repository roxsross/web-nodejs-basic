pipeline {
    agent any
    environment{
        REGISTRY = 'roxsross12'
        APPNAME = 'web-nodejs'
        VERSION = '1.0.0'
    }   
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
                        sh "docker build -t $APPNAME ."
                        sh "docker tag $APPNAME $REGISTRY/$APPNAME:$VERSION"
                        sh "docker push $REGISTRY/$APPNAME:$VERSION"
    
                    }
                }
               
            }
        }
        
        stage('Docker Deploy') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-new') {
                        sh "docker run -d --name latestnode -p 8081:8081 $REGISTRY/$APPNAME:$VERSION"    
                    }
                }
               
            }
        }
    }
}
