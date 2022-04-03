pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                echo 'Install Depedencies'
                script{
                    if(isUnix()){
                        sh 'npm install'
                    }else{
                        bat 'npm install'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Execute tests'
                script{
                    if(isUnix()){
                        sh 'npm test'
                    }else{
                        bat 'npm test'
                    }
                }
            }
        }
        stage('Report') {
            steps {
                echo 'Reports'
                script{
                    if(isUnix()){
                        sh 'npm run report'
                    }else{
                        bat 'npm run report'
                    }
                }
            }
        }
        stage('Publish Report') {
            steps {
                echo 'Publish Reports'
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'report', reportFiles: 'cucumber_report.html', reportName: 'Cucumber Report', reportTitles: ''])
            }
        }
    }
}
