pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
            }
        }
        stage('Test'){
            agent{
                docker{
                    image 'node:18-alpine'
                }
            }
            steps{
                sh '''
                    echo "Test stage"
                    find /var/jenkins_home/workspace/learn-jenkins-app/build -name index.html
                    npm test
                '''
            }
        }
    }
}
