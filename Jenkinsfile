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
        stage('Build v1') {
            steps {
                build 'D_o_K_CI'
            }
        }
        stage('Build v2') {
            steps {
                build 'Deploy_on_Kubernetes_CD'
            }
        }
        stage("Dependency Check") {
            steps {
                dependencyCheckAnalyzer datadir: '',
                hintsFile: '',
                includeCsvReports: false,
                includeHtmlReports: false,
                includeJsonReports: false,
                includeVulnReports: false,
                isAutoupdateDisabled: false,
                outdir:'', scanpath: 'src',
                skipOnScmChange: false,
                skipOnUpstreamChange: false,
                suppressionFile: '',
                zipExtensions: ''
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
