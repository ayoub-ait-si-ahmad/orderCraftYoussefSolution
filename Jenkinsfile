pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ayoub-ait-si-ahmad/orderCraftYoussefSolution'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
            mail to: 'ayoub.ait.si.ahmad.86@gmail.com',
                 // project nname with the build number
                 subject: "Successful Pipeline: ${currentBuild.fullDisplayName}",
                 // build url
                 body: "Build succeeded! Check it out at ${env.BUILD_URL}"
        }

        failure {
            mail to: 'ayoub.ait.si.ahmad.86@gmail.com',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}
