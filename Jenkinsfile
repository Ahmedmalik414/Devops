
pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh '''
                    test -f index.html
                    grep -qi '<html' index.html
                    echo "TEST PASSED"
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    mkdir -p dist
                    cp index.html dist/
                    echo "BUILD PASSED"
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    mkdir -p deployed
                    cp dist/index.html deployed/index.html
                    test -f deployed/index.html
                    echo "DEPLOY PASSED"
                '''
            }
        }
    }
}
