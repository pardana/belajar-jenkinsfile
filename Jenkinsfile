pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hello Build1'
                echo 'Hello Build2'
                echo 'Hello Build3'
            }
        }
        stage('Test') {
            steps {
                echo 'Hello Test1'
                echo 'Hello Test2'
                echo 'Hello Test3'
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
