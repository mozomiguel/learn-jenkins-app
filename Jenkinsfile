pipeline {
    agent 
        kubernetes {
            yaml """
                    apiVersion: v1
                    kind: Pod
                    spec:
                    containers:
                    - name: node
                        image: node:18-alpine
                """
            defaultContainer 'node'
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