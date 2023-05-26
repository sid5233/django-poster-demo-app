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

        stage('Test'){
               sh 'docker-compose build'
                sh 'docker-compose push'
        }
    }
}