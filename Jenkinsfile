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
  } 
}      
           
