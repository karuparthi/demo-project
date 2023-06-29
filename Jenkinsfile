pipeline{
  agent {label 'java-projects'}
  stages {
    stage('Git cloning'){
      steps{
      script{
        git branch: 'main', url: 'https://github.com/rajeshvardhanbusam/demo-project.git'
      }
      } 
    }
  } 
}       
           
