pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/poojitha8642/python-jenkins-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest test_app.py'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mkdir -p /tmp/deploy'
                sh 'cp app.py /tmp/deploy/'
                echo "App deployed to /tmp/deploy"
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
        success {
            echo '✅ Build and Tests Passed!'
        }
        failure {
            echo '❌ Build Failed!'
        }
    }
}
