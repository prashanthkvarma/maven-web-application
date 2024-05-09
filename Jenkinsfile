pipeline {
//  agent any 
  agent {
    label 'slave'
  }

triggers{
pollSCM('* * * * *')
}

options{
timestamps()
buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5'))
}

  stages{
    stage('Checkout'){
      steps{
         git branch: 'master', credentialsId: 'github_creds', url: 'https://github.com/prashanthkvarma/maven-web-application.git'
      }
    }

    stage('build_stage'){
      steps{
        sh "mvn clean package"
      }
    }
  } // stages closing
} //pipeline closing
