pipeline {
//  agent any 
  agent {
    label 'slave'
  }

  stages{
    stage('Checkout'){
      steps{
         git branch: 'master', credentialsId: 'github_creds', url: 'https://github.com/prashanthkvarma/maven-web-application.git'
      }
    }
  }
}
