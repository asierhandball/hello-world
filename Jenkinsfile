pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean install package'
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
