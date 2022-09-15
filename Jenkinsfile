properties([pipelineTriggers([githubPush()])])

pipeline {
    agent any
     
    stages {
        stage('gitcheckout') {
            steps {
    
                git branch: 'master',
                credentialsId: 'e9ce2ee2-6a2f-44b9-9933-acb378b26f51',
                url: 'https://github.com/chakri1311/website_CICD.git'

                 sh "ls -lat"
                echo "Hello world"
            }
        }
        stage('maven_build') {
            steps {

                 sh "mvn clean package"
            }
        }
        stage('copying war into remote') {
            steps {

                 sh "scp $WORKSPACE/target/*.war ansadmin@172.31.37.224:~"
            }
        }
        stage('copy to webapps and restart tomcat') {
            steps {

                 sh """
                 ssh -tt ansadmin@172.31.37.224 "sudo cp ~/*.war /var/lib/tomcat9/webapps/"
                 ssh -tt ansadmin@172.31.37.224 "sudo service tomcat9 restart"
                 """
            }
        }
        
    }

}
