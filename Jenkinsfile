
pipeline {
    agent any
    def myinputid = input (id: '1', message: "Have you done sanity checks?", ok:'Go ahead?', parameters : [
                    [$class: 'TextParameterDefinition',name:'some_parameter_abcd', appName:'my custom app name', description:'my own description', defaultValue:'abcd'],
                    [$class: 'TextParameterDefinition',name:'some_parameter_efgh', appName:'my custom app name efgh', description:'my own description efgh', defaultValue:'efgh']                                                                                          


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
            steps{                                                                                             ])
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
