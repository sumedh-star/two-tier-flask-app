pipeline {
    agent { label "prod" }
    
    stages {
        stage ("git clone") {
            steps {
                echo "git repo is cloning in progress"
        git url: "https://github.com/sumedh-star/two-tier-flask-app.git" , branch: "master"
        echo "git repo is cloned successfully"
        
            }
        }
        
        stage ("Build Image") {
            steps {
                echo "build image is in progres"
                sh "docker build -t fuck-app-hot:latest ."
                echo "docker image build successfully"
            }
        }
        
        stage ("image push to docker hub") {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: "dockerHubfuck",
                    passwordVariable: "dockerhubpass",
                    usernameVariable: "dockerhubuser"
                )]){
            sh "docker login -u ${env.dockerhubuser} -p ${env.dockerhubpass} "
            sh "docker image tag fuck-app-hot:latest ${env.dockerhubuser}/fuck-app-hot "
            sh "docker push ${env.dockerhubuser}/fuck-app-hot"
                }
            }
        }
        stage ("app deploy") {
            steps {
                sh "docker compose up -d"
                
            }
        }
        
    }
}
