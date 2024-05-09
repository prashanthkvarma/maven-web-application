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
         git branch: 'master', credentialsId: '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', url: 'https://github.com/prashanthkvarma/maven-web-application.git'
      }
    }

    stage('build_stage'){
      steps{
        sh "mvn clean package"
      }
    }
  } // stages closing
} //pipeline closing
