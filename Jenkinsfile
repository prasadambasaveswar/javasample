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
            
               sh '''
              
                cp ${WORKSPACE}/target/*.war /usr/share/tomcat/webapps/
                chown tomcat:tomcat /usr/share/tomcat/webapps/*
                ls -lrth /usr/share/tomcat/webapps/
                systemctl restart tomcat
                systemctl status tomcat
EOF
'''
	}
        }
    }
}
