pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'g++ -o PES2UG22CS601-1 program.cpp'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS601-1'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh '''
                    git config --global user.name "Surabhi S Suvarna"
                    git config --global user.email "surabhisuvarna290804@gmail.com"
                    
                    git checkout main || git checkout -b main
                    git add program.cpp
                    git commit -m "Added new C++ file"
                    git push origin HEAD:main
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

