@Library("jenkins-pipeline@master") _ 

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            when {
                expression {
                    GIT_BRANCH != "master"
                }
            }
            steps {
                echo 'Deploying....'
            }
        }
        stage('Deploy to production') {
            when {
                expression {
                    GIT_BRANCH == "master"
                }
            }
            steps {
                script {
                    build.buildImage()
                    deploy.deployBackend()
                }
            }
        }
    }
}
