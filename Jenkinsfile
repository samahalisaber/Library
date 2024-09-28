pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Create Docker Image') {
            steps {
                sh 'docker build -t my-ui-library:$BUILD_NUMBER . -f Dockerfile'
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker push docker.io/samahalisaber/my-ui-library:$BUILD_NUMBER'
            }
        }
        stage('Deploy') {
            steps {
                sed -i "s|@BUILD_NUMBER@|${BUILD_NUMBER}|g" ./deploy.yaml
                 sh 'kubectl apply -f ./deploy.yaml'
    }
}
