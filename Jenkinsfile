pipeline {
//  agent any 
  agent {
    label 'slave'
  }

tools{
maven 'maven3.9.6'

}

if (env.BRANCH_NAME == 'master') {
parameters {
  choice choices: ['test', 'master',], description: 'Select required branch name', name: 'BranchName', defaultValue: 'master'
}
} else (env.BRANCH_NAME == 'test') {
  parameters {
  choice choices: ['test', 'master',], description: 'Select required branch name', name: 'BranchName', defaultValue: 'test'
}}

triggers{
pollSCM('* * * * *')
}
  
options{
timestamps()
buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '2', daysToKeepStr: '', numToKeepStr: '2'))
}


  stages{
    stage('Checkout'){
      steps{
          git branch: "${params.BranchName}", credentialsId: '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', url: 'https://github.com/prashanthkvarma/maven-web-application.git'
      }
    }
    stage('build_stage'){
      steps{
        sh "mvn clean package"
      }
    }
  } // stages closing
} //pipeline closing
