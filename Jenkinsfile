pipeline { 

  

    agent any 

  

    stages { 

  

        stage('Checkout') { 

            steps { 

                git branch: 'main', 

                    url: 'https://github.com/USERNAME/SeleniumJenkinsProject.git' 

            } 

        } 

  

        stage('Install Dependencies') { 

            steps { 

                bat 'python -m pip install -r requirements.txt' 

            } 

        } 

  

        stage('Run Selenium Tests') { 

            steps { 

                bat 'python -m pytest -v --html=report.html --self-contained-html' 

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