pipeline{
    agent  any  
    stages{

        stage("Checkout"){
            steps{
                git 'https://github.com/sid5233/django-poster-demo-app.git'
            }
        }

        stage('Docker Build and Tag') {
           steps {
            script {
                    dockerImage.tag('python-openshift:latest')
                    dockerImage.tag('python-openshift:${env.BUILD_NUMBER}')
                }

                // sh 'docker login'
                // sh 'docker build -t python-openshift:latest .' 
                // sh 'docker tag  bizmetric1/python-openshift:latest'
                //sh 'docker tag samplewebapp bizmetric1/python-openshift:$BUILD_NUMBER'
               
          }
        }
        stage('Publish image to Docker Hub') {
          
            steps {
                withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
                sh  'docker push bizmetric1/python-openshift:latest'
                //  sh  'docker push bizmetric1/python-openshift:$BUILD_NUMBER' 
                dockerImage.push('python-openshift:latest')
                dockerImage.push('python-openshift:${env.BUILD_NUMBER}')
                }
                  
          }
        }
    }
}