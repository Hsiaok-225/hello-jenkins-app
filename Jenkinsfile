pipeline {
    agent any

    stages {
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
