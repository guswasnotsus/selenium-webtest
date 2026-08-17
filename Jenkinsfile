pipeline {

    agent any

    stages {
stage('Check Python') {
    steps {
        bat 'dir "C:\\Users\\fe\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe"'
        bat '"C:\\Users\\fe\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe" --version'
    }
}
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/guswasnotsus/selenium-webtest.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '"C:\\Users\\fe\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe" -m pip install -r requirements.txt'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                bat '"C:\\Users\\fe\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe" -m pytest -v --html=report.html --self-contained-html'
            }
        }
    }

    post {

        always {
            archiveArtifacts artifacts: 'report.html',
                             allowEmptyArchive: true
        }

        success {
            echo 'Selenium tests completed successfully.'
        }

        failure {
            echo 'Selenium tests failed.'
        }
    }
}