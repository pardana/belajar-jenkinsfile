pipeline {
    agent any
    environment{
        AUTHOR = "Aditria Pardana"
        WEB = "https://appardana.com"
    }
    options{
        disableConcurrentBuilds()
        timeout(time: 10, unit: 'MINUTES')
    }
    parameters{
        string(name: 'NAME', defaultValue: 'Guest', description: 'What is your name?')
        text(name: 'DESCRIPTION', defaultValue: '', description: 'Tell me about you!?')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Need to deploy?')
        choice(name: 'SOCIAL_MEDIA', choices: ['Instagram','Facebook','Twitter'], description: 'Which sosial media?')
        password(name: 'SECRET', defaultValue: '', description: 'Encrypt Key?')
    }

    //triggers{
        //cron("*/1 * * * *")
        //pollSCM("*/1 * * * *")
        //upstream("upstreamProjects: 'job1,job2', treshold: hudson.model.Result.SUCCESS")
    //}

    stages {
        stage('Preparation'){
            parallel{
                stage('Prepare Java'){
                    steps{
                        echo("Prepare Java")
                        sleep(5)
                    }
                }
                 stage('Prepare Maven'){
                    steps{
                        echo("Prepare Maven")
                        sleep(5)
                    }
                }
            }
        }
        
        stage('Prepare ENV') {
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
        
        stage('Parameter') {
            steps {
                echo "Hello: ${params.NAME}"
                echo "Description: ${params.DESCRIPTION}"
                echo "Deploy: ${params.DEPLOY}"
                echo "Sosial Media: ${params.SOCIAL_MEDIA}"
                echo "Secret: ${params.SECRET}"
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
            input{
                message "Can we deploy?"
                ok "Yes, of course?"
                submitter "appardana"
                parameters{
                    choice(name: "TARGET_ENV", choices: ["DEV", "PROD"], description: "Which environtment?")
                }
            }
            steps {
                echo "Deploy to ${params.TARGET_ENV}"
            }
        }

        stage('Release') {
           when{
                expression{
                    return params.DEPLOY
                }
           }
            steps {
                withCredentials([usernamePassword(
                    credentialsId: "aditria_rahasia",
                    usernameVariable: "USERNAME",
                    passwordVariable: "PASSWORD"
                )]){
                    sh('echo "Release it with -u $USERNAME -p $PASSWORD" > "release.txt"')
                }
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
