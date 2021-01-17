pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                    script{
                        if(isUnix()){
                            sh 'npm install'
                        }else {
                            bat 'npm install'
                        }
                    }
                    
            }
        }
        stage('Test') {
            steps {
                    script{
                        if(isUnix()){
                            sh 'npm test'
                        }else {
                            bat 'npm test'
                        }
                    }
            }
        }
        stage('Generate Report') {
            steps {
                    script{
                        if(isUnix()){
                            sh 'npm run report'
                        }else {
                            bat 'npm run report'
                        }
                    }
            }
        }
        stage('Pulish Report') {
            steps {
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'report', reportFiles: 'cucumber_report.html', reportName: 'HTML Report', reportTitles: ''])
            }
        }
    }
}
