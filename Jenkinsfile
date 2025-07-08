pipeline {
    agent any
    environment {
        TALEND_ZIP = 'CustomerLoggerJob_0.1.zip'
        UNZIP_DIR = 'unzipped_job'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Siriivalli/talend-ci-demo.git'
            }
        }
        stage('Unzip Talend Job') {
            steps {
                bat 'powershell -Command "Expand-Archive -Force %TALEND_ZIP% %UNZIP_DIR%"'
            }
        }
        stage('Run Talend Job') {
            steps {
                bat '''
cd unzipped_job\\CustomerLoggerJob_0.1
call CustomerLoggerJob_0.1_run.bat --context=Default
'''
            }
        }
    }
}
