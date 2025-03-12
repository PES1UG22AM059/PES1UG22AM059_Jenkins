pipeline {
    agent any

    stages {
        // Clone the repository
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                branches: [[name: '*/main']],
                userRemoteConfigs: [[url: 'https://github.com/PES1UG22AM059/PES1UG22AM059_Jenkins.git']]])
            }
        }

        // Build Stage: Compile the C++ file
        stage('Build') {
            steps {
                sh 'g++ main/hello.cpp -o main/hello_exec'
            }
        }

        // Test Stage: Run the compiled C++ program
        stage('Test') {
            steps {
                sh './main/hello_exec'
            }
        }

        // Deploy Stage: Simulate deployment
        stage('Deploy') {
            steps {
                sh '''
                    echo "Simulating deployment..."
                    echo "Copying files to a deployment directory..."
                    mkdir -p deploy
                    cp main/hello_exec deploy/
                    echo "Deployment complete!"
                '''
            }
        }
    }

    // Post-build actions
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
