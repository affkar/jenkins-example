pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'currentmvn') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'currentmvn') {
                    sh 'mvn test'
                }
            }
        }

        stage('Sanity check') {
            steps {
                input "Have you done sanity checks?"
            }
        }
        

        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'currentmvn') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
