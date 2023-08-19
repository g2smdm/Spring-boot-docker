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
// bat "set PATH=%PATH%;C:\Users\dhyan\Downloads\apache-maven-3.9.4-bin\apache-maven-3.9.4\bin
// To run Maven on a Windows agent, use
bat "mvn -Dmaven.test.failure.ignore=true clean package"
}

// post {
// If Maven was able to run the tests, even if some of the test
// failed, record the test results and archive the jar file.
success {
junit '**/target/surefire-reports/TEST-*.xml'
archiveArtifacts 'target/*.jar'
}
}
}
}
}
