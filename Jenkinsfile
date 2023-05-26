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

        stage('Docker Build and Tag') {
           steps {
                sh 'docker login'
                sh 'docker build -t  python-openshift:latest .' 
                sh 'docker tag python-openshif  bizmetric1/python-openshift:latest'
                //sh 'docker tag samplewebapp shivalikirdat/samplewebapp:$BUILD_NUMBER'
               
          }
        }
        stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
          sh  'docker push bizmetric1/python-openshift:latest'
        //  sh  'docker push shivalikirdat/samplewebapp:$BUILD_NUMBER' 
        }
                  
          }
        }
    }
}