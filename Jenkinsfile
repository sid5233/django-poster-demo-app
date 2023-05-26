pipeline{
    agent{
        label "any"
    }
    stages{

        stage("Checkout"){
            steps{
                git 'https://github.com/sid5233/django-poster-demo-app.git'
            }
        }

        stage("Build"){
            steps{
                sh 'docker build -t myapp .'
            }
        }
        stage('Test'){
            sh 'docker-compose up'
        }
    }
}