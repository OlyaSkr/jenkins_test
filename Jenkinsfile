pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/OlyaSkr/jenkins_test.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                bat 'build.bat'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                bat 'test.bat'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                bat 'deploy.bat'
               
                script {
                    def htmlContent = readFile(file: 'index.html')
                    echo "Contents of index.html:"
                    echo htmlContent
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
            cleanWs()
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}