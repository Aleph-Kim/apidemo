pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aleph-kim/apidemo.git', credentialsId: 'aleph-github_id'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                // build steps
                sh 'chmod 755 ./gradlew'
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // test steps
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // deploy steps
                 withAWS(credentials: 'lion-user') {
                    sh 'aws s3 cp build/libs/apirdsdemo-0.0.1-SNAPSHOT.jar s3://aleph-jenkins-build/'
                }
            }
        }
    }
}
