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
                sh '''
                sshpass -p "lastchance" ssh -o StrictHostKeyChecking=no root@instance-6 <<EOF
	            cd /mnt
                ls -lrth
                cp /mnt/*.war /usr/share/tomcat/webapps/
                chown tomcat:tomcat /usr/share/tomcat/webapps/*
                ls -lrth /usr/share/tomcat/webapps/
                systemctl restart tomcat
                systemctl status tomcat
EOF
            }
        }
    }
}
