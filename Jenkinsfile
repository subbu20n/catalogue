pipeline {
    agent {
        label 'AGENT-1'
    }

    environment{
        appVersion = ''
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
            steps{
                script{
                    sh """ 
                         echo "hello test" 
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