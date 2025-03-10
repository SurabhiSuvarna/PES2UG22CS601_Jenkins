pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Compile hello.cpp instead of program.cpp
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
                    sh '''
                    git config --global user.name "Surabhi S Suvarna"
                    git config --global user.email "surabhisuvarna290804@gmail.com"
                    
                    git checkout main || git checkout -b main
                    git add hello.cpp
                    git commit -m "Added hello.cpp file"
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


