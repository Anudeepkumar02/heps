pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
                git 'https://github.com/Anudeepkumar02/heps.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Artifact download') {
            steps {
                sh 'aws s3 cp target/*.war s3://warfileswebproject/heps/heps.war'
                sh 'aws s3 cp target/*.war s3://warfileswebproject/heps/heps$BUILD_NUMBER.war'
            }
        }
        stage('Build docker image') {
            steps {
                script{
                    sh 'docker build -t 2222s/heps .'
                }
            }
        }
    }
}
