pipeline {
    agent any
    tools {
        Maven "M2_HOME"
        Java "JAVA_HOME"
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage('Build v1') {
            steps {
                build 'D_o_K_CI'
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
                
            }
        }
        stage ('Anchore Image Scanning') {
            steps {
                sh '''
                    echo "asaluena/simple-devops-image:latest" > anchore_images
                '''
                anchore engineCredentialsId: '148601be-a3db-4b5a-b468-f25de3498565', engineRetries: '500', engineurl: 'http://172.31.13.28:8228/v1', name: 'anchore_images'
            }
        }
        stage('Build v2') {
            steps {
                build 'Deploy_on_Kubernetes_CD'
            }
        }
        
        
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

}
