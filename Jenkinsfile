pipeline {
    agent { label 'slave4' }
    stages {
        stage('Checkout') {
            steps {
               // sh "rm -rf clinic"
             //   sh "git clone https://github.com/Dev86-git/clinic.git"
             //   sh "cd clinic"
                checkoutcode()
            }
        }
        stage('Set up Environment') {
            steps {
                sh 'export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))'
                sh 'export MAVEN_HOME=/usr/share/maven'
            }
        }
                stage('setupjava17') {
            steps {
                setupjava('openjdk-17-jdk')
            }
        }
        stage('setupmaven') {
            steps {
                //   echo " installing maveen"
                //sh "sudo apt install -y maven"
                setupjava('maven')
            }
        }
        stage('build') {
            steps {
               // sh "mvn clean install"
                buildproject()
            }
        }
        stage('Run Application') {
            steps {
                echo 'Running Spring Boot application...'
                sh 'mvn spring-boot:run'
                
            }
        }
    }
}
