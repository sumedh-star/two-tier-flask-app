pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
            checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'githubtoken', url: 'https://github.com/sumedh-star/two-tier-flask-app.git']])
           echo "webhook connected successfully"
            }
            
        }
    }
}
