pipeline {
agent any 
tools {
  maven 'Maven'
}

stages {
stage('Checkout') {
steps {
checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git', url: 'https://github.com/g2smdm/Spring-boot-docker.git']]])
}
}

stage('Build') {
steps {
// Run Maven on a Unix agent.
// sh "mvn -Dmaven.test.failure.ignore=true clean package"
// To run Maven on a Windows agent, use
bat "mvn -Dmaven.test.failure.ignore=true clean package"
}
}
stage("Docker package"){
  steps{
    bat 'docker build  -t jenkinsdocker .'
  }
}
stage("Docker run"){
  steps{
    bat 'docker run -it -p 8585:8080 -d jenkinsdocker'
  }
}
}
}
