// Uses Declarative syntax to run commands inside a container.
pipeline {
    agent any
    // {
    //     kubernetes {
    //         containerTemplate {
    //             name 'node'
    //             image 'node:18-alpine'
    //             command 'cat'
    //             ttyEnabled true
    //         }
    //         defaultContainer 'node'
    //         retries 2
    //     }
    // }
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
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
        stage('test') {
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh 'test -f build/index.html'
                sh 'npm test'
            }
        }
        // stage('E2E') {
        //     agent {
        //         kubernetes {
        //             containerTemplate {
        //                 name 'node'
        //                 image 'node:18-alpine'
        //                 command 'cat'
        //                 ttyEnabled true
        //             }
        //             defaultContainer 'node'
        //             retries 2
        //         }
        //     }
        //     steps {
        //         sh 'test -f build/index.html'
        //         sh 'npm test'
        //     }
        // }

    }
    // post {
    //     always {
    //         junit 'test-results/junit.xml'
    //     }
    // }
}
