pipeline {
    agent any

    stages {
        stage('Running collection') {
            steps {
                sh 'newman --version'
                sh 'newman run a_TrelloAPI.postman_collection.json --disable-unicode --reporters cli,htmlextra,junit --reporter-htmlextra-export newman/report.html --reporter-junit-export newman/report.xml'
            }
        }
    }
        post {
        always {
            publishHTML target: [
                reportName: 'Newman',
                reportDir: 'newman',
                reportFiles: 'report.html',
                reportTitles: 'Postman API tests',
                keepAll: true,
                alwaysLinkToLastBuild: true,
                allowMissing: false
            ]
           junit skipPublishingChecks: true, testResults: 'newman/report.xml'

        }
    }
    
}
