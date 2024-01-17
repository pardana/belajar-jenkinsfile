pipeline {
    agent any
    environment{
        AUTHOR = "Aditria Pardana"
        WEB = "https://appardana.com"
    }
    options{
        .disableConcurrentBuilds()
        .timeout(time: 10, unit: 'SECONDS')
    }

    stages {
        stage('Prepare') {
            environment{
                APP = credentials("aditria_rahasia")
            }
            
            steps {
                script{
                   echo("Start Job : ${env.JOB_NAME}")
                   echo("Start Build : ${env.BUILD_NUMBER}")
                   echo("Branch Name: ${env.BRANCH_NAME}")
                   echo("Author: ${AUTHOR}")
                   echo("Web: ${WEB}")
                   echo("APP User: ${APP_USR}")
                   sh('echo "App Password : $APP_PSW" > "rahasia.txt"')
                }
            }
        }
        stage('Build') {
            steps {
                script{
                    for(int i=0; i<10; i++){
                        echo "Script ke-${i}"
                    }
                    // Gunakan backtick (`) sebagai karakter escape dalam PowerShell
                    //powershell(". '.\\mvnw.cmd'")
                }
                echo 'Start Build'
                /*sh('./mvnw clean compile test-compile')*/
                echo 'Finish Build'
            }
        }
        stage('Test') {
            steps {
                script{
                    def data = [
                        "firstName" : "Aditria",
                        "lastName" : "Pardana"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
                echo 'Start Test'
                echo 'Finish Test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Hello Deploy1'
                echo 'Hello Deploy2'
                echo 'Hello Deploy3'
            }
        }
    }

    post{
        always{
            echo "I will always say Hello again!"
        }
        success{
            echo "Yay, success"
        }
        failure{
            echo "Oh no. Error!"
        }
        cleanup{
            echo "Don't care success or error"
        }
    }
}
