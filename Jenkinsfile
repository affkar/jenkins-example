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
            steps{
                greet (name: 'Karthick', useFrench: true)   
            }
        }

        stage('Sanity check') {
            steps {
                
                input (message: "Have you done sanity checks?",id: 'myinputid', ok:'Go ahead?', parameters : [[$class: 'TextParameterDefinition',name:'some_parameter_abcd', appName:'my custom app name', description:'my own description', defaultValue:'my own default value']])
                echo ("some_parameter_abcd: "+myinputid['some_parameter_abcd'])
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
