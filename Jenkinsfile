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
                sh 'echo  "Deploying to tomcat server" '
                sshagent(['tomcat-agent']) {
                   sh " scp -o StrictHostKeyChecking=no target/*.war ec2-user@13.233.197.170:/var/lib/tomcat9/webapps/ROOT "
                }
            }
        }
    }
}
