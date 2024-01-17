pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Start Build'
                sh('./mvnw clean compile test-compile')
                echo 'Finish Build'
            }
        }
        stage('Test') {
            steps {
                echo 'Start Test'
                sh('./mvnw test')
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
