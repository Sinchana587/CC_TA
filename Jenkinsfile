pipeline {
    agent any 

    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/Sinchana587/CC_TA']]
                ])
            }
        }
        
        stage('Build') {
            steps {
                sh 'g++ main/hello.cpp -o output'
                sh 'chmod +x output'  // Ensure output is executable
            }
        }

        stage('Test') {
            steps {
                sh './output'  // Run the compiled program
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
