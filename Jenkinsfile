pipeline {
    agent any
    tools {
        maven "M2_HOME"
        jdk "JAVA_HOME"
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
        /* stage('Build v1') {
            steps {
                build 'D_o_K_CI'
            }
        }
        stage('Build v2') {
            steps {
                build 'Deploy_on_Kubernetes_CD'
            }
        } */
        
        stage ('OWASP Dependency-Check Vulnerabilities') {
            steps {
                dependencyCheck additionalArguments: '--scan=/ --format XML', odcInstallation: 'Home'

                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
        stage ('Anchore Image Scanning') {
            steps {
                anchore engineCredentialsId: '148601be-a3db-4b5a-b468-f25de3498565', engineRetries: '500', engineurl: 'http://172.31.13.28:8228/v1', name: 'anchore_images'
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
