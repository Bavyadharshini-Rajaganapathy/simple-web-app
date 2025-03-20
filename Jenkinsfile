pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'main', url: 'https://github.com/Bavyadharshini-Rajaganapathy/devops1.git'
            }
        }
        stage('build') {
            steps {
               sh "mvn clean"
               sh "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  sh 'docker build -t bavyadharshini/simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'docker_cred', url: 'https://index.docker.io/v1/') {
                  sh 'docker push bavyadharshini/simplewebapp'
               }
            }
            }
}
}
}
