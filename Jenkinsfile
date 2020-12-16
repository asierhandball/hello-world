pipeline {
    agent any
    stages {

        stage('Build') {
            steps {
              withMaven () {
                sh 'mvn -B -f /var/lib/jenkins/workspace/Pipeline_Test/pom.xml clean install package'
              }
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
