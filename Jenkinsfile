@Library("Shared") _
pipeline {
    agent {label "vinod"}

    stages {
        stage('Hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code Checkout') {
            steps {
                script{
                    code_checkout("https://github.com/promise-dash/node-todo-cicd.git", "master")
                }
            }
        }
        stage('Docker build') {
            steps {
                script{
                    docker_build("todo-app", "latest", "promise779")
                }
            }
        }
        stage('Push to Dockerhub') {
            steps {
                script{
                    docker_push("todo-app", "latest")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the code'
                sh "docker compose up -d"
            }
        }
    }
}
