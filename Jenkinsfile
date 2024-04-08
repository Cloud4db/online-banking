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
                   sh " sudo scp -o StrictHostKeyChecking=no target/*.war tomcat@3.6.90.203:/var/lib/tomcat9/webapps/ROOT"
                }
            }
        }
    }
}
