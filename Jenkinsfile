pipeline {
  agent any
  tools {
    maven 'Maven-3.6.3' 
  }
  stages {
    stage ('clone') {
      steps {
        git 'https://github.com/ratnareddypaluri/hello-world.git'
      }
    }
    stage ('Build') {
      steps {
        sh 'mvn clean package'
        sh "mv target/*.war target/myweb.war"
      }
    }
    stage ('Deploy') {
      steps {
        sshagent(['tomcat'])  {
          sh """
          scp -o StrictHostKeyChecking=no target/myweb.war ubuntu@52.66.138.6:/var/lib/tomcat9/webapps"""
          }
      }
    }
  }
}
