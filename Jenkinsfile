pipeline {
    agent {
        label 'AGENT-1'
    }

    environment{
        appVersion = '' 
        ACC_ID = ""
        SECRET_ID = "" 
        REGION = 'us-east-1'
        component = 'catalogue'
    }

    options{
        timeout(time: 30, unit: 'MINUTES')
    }

    //BUILD 
    stages {
        stage('Read package.json'){
            steps{
               script{
                def packageJson = readJSON file: 'package.json' 
                appVersion = packageJson.version 
                echo "package.version: ${appVersion}"
                }
            }    
        }
        stage{
            steps('install depenedncies'){
                script{
                    sh """ 
                       npm install
                    """
                }

            }
        }
    }
    post{
        always{
            deleteDir{} 
        }
        success{
            echo "hello success"
        }
        failure{
            echo "hello failure"
        }
    }
} 