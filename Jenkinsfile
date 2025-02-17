pipeline {
    agent { label 'slave4' }
    stages {
        stage('Checkout') {
            steps {
                sh "rm -rf clinic"
                sh "git clone https://github.com/Dev86-git/clinic.git"
                sh "cd clinic"
            }
        }
        stage('Set up Environment') {
            steps {
                sh 'export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))'
                sh 'export MAVEN_HOME=/usr/share/maven'
            }
        }
        stage('build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Run Application') {
            steps {
                echo 'Running Spring Boot application...'
                sh 'nohup mvn spring-boot:run &'
                sleep(time: 15, unit: 'SECONDS')
            }
        }
    }
}
