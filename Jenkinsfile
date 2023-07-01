pipeline{
  agent any
  stages {
    stage('Git cloning'){
      steps{
      script{
        git branch: 'main', url: 'https://github.com/karuparthi/demo-project.git'
      }
    }
  }
     stage('unit testing'){
       steps{
         script{
           sh 'mvn test'
         }
       }
     }
    stage('integration testing'){
      steps{
        script{
          sh 'mvn verify'
        }
      }
    }
    stage('code compilation'){
      steps{
        script{
          sh 'mvn clean install'
        }
      }
    }
    stage('sonarqube analsys'){
      steps{
        script{
          withSonarQubeEnv(credentialsId: 'jenkins-1') {
            sh 'mvn clean package sonar:sonar'
          }
        }
      }
    }
  } 
}      
           
