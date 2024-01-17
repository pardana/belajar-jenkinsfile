pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script{
                    for(int i=0; i<10; i++){
                        echo "Script ke-${i}"
                    }
                }
                echo 'Start Build'
                /*sh('./mvnw clean compile test-compile')*/
                Powershell(". '.\mvnw.cmd'")
                echo 'Finish Build'
            }
        }
        stage('Test') {
            steps {
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
