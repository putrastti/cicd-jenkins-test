pipeline {
    agent any

    stages {
        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_5_0'){
                    sh 'mvn clean package'
                }
            }
        }

        stage ('Deploy'){
            steps {
                withCredentials([[$class    : 'UsernamePasswordMultibinding',
                      credentialsId         : 'PCF_LOGIN',
                      usernameVariable      : 'putra.tkd@gmail.com',
                      passwordVariable      : 'P@ssw0rd*1']]){
                sh '/usr/local/bin/cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD'
                sh '/usr/local/bin/cf push'
                }
            }
        }
    }
}