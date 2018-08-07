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
        stage('Greet in French'){
         greet (name: 'Karthick', useFrench: true)   
        }

        stage('Sanity check') {
            steps {
                
                input (message: "Have you done sanity checks?",id: '1', ok:'Go ahead?', parameters : ['some parameter abcd'])
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
