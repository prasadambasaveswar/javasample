pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                git url: 'https://github.com/prasadambasaveswar/javasample.git'
            }
        }
        stage('build') {
        steps {
        sh 'mvn clean install'
        }
        }
        stage('deploy') {
            steps {
                sh 'sshpass -p "lastchance" scp ${WORKSPACE}/target/*.war root@instance-6:/mnt/'
            }
        }
    }
}
