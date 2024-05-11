pipeline {
//  agent any 
  agent {
    label 'slave'
  }

tools{
maven 'maven3.9.6'

}


  
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
         git branch: "master", credentialsId: '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', url: 'https://github.com/prashanthkvarma/maven-web-application.git'
      }
    }


    stage('build_stage'){
      steps{
        sh "mvn clean package"
      }
    }


  } // stages closing

} //pipeline closing
