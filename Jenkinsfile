// Uses Declarative syntax to run commands inside a container.
pipeline {
    agent {
        kubernetes {
            containerTemplate {
                name 'node'
                image 'node:18-alpine'
                command 'cat'
                ttyEnabled true
            }
            defaultContainer 'node'
            retries 2
        }
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
