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
                input (message: "Have you done sanity checks?",id: '1')
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
