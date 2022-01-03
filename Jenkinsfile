pipeline {




agent any
environment {
//adding a comment for the commit test
DEPLOY_CREDS = credentials('deploy-anypoint-user')
MULE_VERSION = '4.4.0'
BG = "Capgemini"
WORKER = "Micro"
}
stages {
stage('Build Application') {
steps {
bat 'mvn clean install'
}
}
stage('Test') {
steps {
bat "mvn test"
}
}



stage('Sonarqube'){
steps{
bat 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=admin -Dsonar.password=vishu@1234'
}
}



stage('Deploy Application to Mulesoft Cloudhub'){
steps{
bat 'mvn package deploy -DmuleDeploy'
}
}
}
}
