pipeline {
    agent any

    stages {
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    if test -f /build/index.html; then
                        echo "File exists and is a regular file."
                    npm test
                '''
            }
        }
        stage('build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo 'building...'
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    ls -la
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
