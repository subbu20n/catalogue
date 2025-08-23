pipeline {
    agent {
        label 'AGENT-1'
    } 
    environment {
        appVersion = ''
    } 
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
    }/* 
     parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password') 
    } */
    stages{
        stage('Read Package.json'){
            steps {
                script {
                  def packageJson = readJSON file: 'package.json'
                  appVersion = packageJson.version 
                  echo "package version: ${appVersion}"
                }
            }
        }
        stage('Install Dependencies'){
            steps{
                script{
                    sh """
                       npm install 
                    """
                }
            }
        }
        stage('Build'){
            steps {
                script{
                    sh """
                      echo "Building"   
                      sleep 10 
                
                    """
                }
            }    
        }
        stage('Test'){
            steps {
                script {
                      echo "Testing"
                }
            }

        }
    }
    post {
        always {
            echo "I will say always Hello Again!"
            deleteDir()
        }
        success {
            echo "Hello Success"
        }
        failure {
            echo "Hello Failure"
        }
    }
}
 