pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Compile hello.cpp
                    sh 'g++ -o PES2UG22CS601-1 hello.cpp'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run the compiled hello.cpp
                    sh './PES2UG22CS601-1'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Configure git user information
                    sh 'git config --global user.name "Surabhi S Suvarna"'
                    sh 'git config --global user.email "surabhisuvarna290804@gmail.com"'
                    
                    // Ensure you're on the correct branch (assumes 'main' exists)
                    sh 'git checkout main || git checkout -b main'
                    
                    // Add and commit changes
                    sh '''
                    git add hello.cpp
                    git commit -m "Added hello.cpp file"
                    git push origin main
                    '''
                }
            }
        }
    }

    post {
        failure {
            echo "Pipeline failed"
        }
    }
}
