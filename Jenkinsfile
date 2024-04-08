pipeline {
    agent any

    stages {
        stage('maven build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Tomcat deploy') {
            steps {
                sh "echo tomcat"
                sshagent(['tomcat-agent']) {
                   sh " scp -o StrictHostKeyChecking=no target/*.war ec2-user@3.110.179.31:/home/ec2-user/tomcat10/webapps"
                }
            }
        }
    }
}
