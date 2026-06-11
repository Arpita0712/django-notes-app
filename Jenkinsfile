@Library('Shared') _

pipeline {

    agent {
        label 'vinod'
    }

    stages {

        stage('Hello') {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('Code') {
            steps {
                script {
                    clone(
                        "https://github.com/sagar2724/django-notes-app.git",
                        "main"
                    )
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    docker_build(
                        "notes-app",
                        "latest",
                        "sagarkorade"
                    )
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker_push(
                        "notes-app",
                        "latest",
                        "sagarkorade"
                    )
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    docker_compose()
                }
            }
        }
    }
}
