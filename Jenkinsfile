pipeline {
    environment {
        springF = "ams_back"
        angularF = "ams_front"
        DOCKERHUB_CREDENTIALS=credentials('dockerhub_cred') 

            }

    agent any

    stages {

        stage('Création d\'une image ams-backend') {
            steps {
                sh 'docker build -t ams-backend ${springF}'
            }
        }

        stage('tag and push image ams-backend to dockerhub') {

                    steps {

                    echo "tag and push image ..."

                    sh "docker tag ams-backend akryos/ams-backend"

                    sh "docker login -u $DOCKERHUB_CREDENTIALS_USR -p  $DOCKERHUB_CREDENTIALS_PSW"

                    sh "docker push akryos/ams-backend"

                    sh "docker logout"

                    }

               post{

                    success{
                         echo "====++++success++++===="
                         }

                    failure{
                         echo "====++++failed++++===="
                         }
          
        
               }
        }


        stage('Création d\'une image ams-frontend') {
            steps {
                sh 'docker build -t ams-frontend ${angularF}'
            }
        }

        stage('tag and push image ams-frontend to dockerhub') {

                    steps {

                    echo "tag and push image ..."

                    sh "docker tag ams-frontend akryos/ams-frontend"

                    sh "docker login -u $DOCKERHUB_CREDENTIALS_USR -p  $DOCKERHUB_CREDENTIALS_PSW"

                    sh "docker push akryos/ams-frontend"

                    sh "docker logout"

                    }

               post{

                    success{
                         echo "====++++success++++===="
                         }

                    failure{
                         echo "====++++failed++++===="
                         }
          
        
               }
        }

        stage('Docker-compose') {
            steps {
                sh 'docker compose -f docker-compose.yml up -d'
            }
        }
    
     }

}


       
