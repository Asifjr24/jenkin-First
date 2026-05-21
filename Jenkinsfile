pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Pulling code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'chmod +x app.sh'
                sh 'echo Build completed successfully!'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh '''
                    if [ -f app.sh ]; then
                        echo "app.sh exists - Test Passed!"
                    else
                        echo "app.sh missing - Test Failed!"
                        exit 1
                    fi
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Hello World...'
                sh './app.sh'
            }
        }

    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}