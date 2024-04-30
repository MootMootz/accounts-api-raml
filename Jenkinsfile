pipeline {
    agent any
    triggers{
        pollSCM('H/2 * * * *')
    }
    stages {
    stage('Build Application') {
        steps {
            sh 'mvn clean install'
            }
        }
    stage('Deploy CloudHub') {
        environment {
            ANYPOINT_CREDENTIALS = credentials('04269f79-9bd5-4899-82e2-86512fde0003')
        }
    steps {
        sh "mvn deploy -DmuleDeploy -Dcloud.env=Sandbox -DcloudhubAppName=accounts-raml-api  -Dmule.version=4.6.1 -Dcloud.user=${ANYPOINT_CREDENTIALS_USR} -Dcloud.password=${ANYPOINT_CREDENTIALS_PSW}"
        }
    }
    }
}
