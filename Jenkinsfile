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
                    return env.GIT_BRANCH != "master"
                }
            }
            steps {
                echo 'Deploying....'
            }
        }
        stage('Deploy to production') {
            when {
                expression {
                    return env.GIT_BRANCH == "master"
                }
            }
            steps {
                script {
                    build.buildImage("renveg2010/sample-app:1.0.0")
                    deploy.deployBackend()
                }
            }
        }
    }
}
