pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/teleppathy/kr_4.git', credentialsId: 'github-credentials' 
            }
        }

        stage('Build') {
            steps {
                bat '"path to MSBuild" test_repos.sln /t:Build /p:Configuration=Debug'
            }
        }

        stage('Test') {
            steps {
                bat 'x64\\Debug\\test_repos.exe --gtest_output=xml:test_report.xml' 
            }
        }
    }
    
    post {
        always {
            junit testResults: '**/test_report.xml' 
        }
    }
}