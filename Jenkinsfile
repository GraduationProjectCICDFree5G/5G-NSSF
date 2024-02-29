pipeline {
   agent any

   environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-grad-project')
   }

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

      stage('Login to Dockerhub') {
         steps {
            sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
         }
      }
      stage('docker build') {
         steps {

        sh(script: """
            sudo docker build -t 5ggraduationproject/nssf:latest . 
            sudo docker images -a                  
        """)
            }
            }
      stage('Pushing to Dockerhub') {

               steps {
                  sh 'docker push 5ggraduationproject/nssf:latest'
               }
            }

         }
      }