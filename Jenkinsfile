pipeline {
    environment {
        springF = "ams_back"
        angularF = "ams_front"
        

            }

    agent any

    stages {

        stage('Création d\'une image ams-backend') {
            steps {
                sh 'docker build -t ams-backend ${springF}'
            }
        }


        stage('Création d\'une image ams-frontend') {
            steps {
                sh 'docker build -t ams-frontend ${angularF}'
            }
        }


        stage('Docker-compose') {
            steps {
                sh 'docker compose -f Docker-compose.yml up -d'
            }
        }
    
    }

}