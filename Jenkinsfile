pipeline{
  agent any
  stages {
    stage('Git cloning'){
      steps{
      script{
        git branch: 'main', url: 'https://github.com/rajeshvardhanbusam/demo-project.git'
      }
      } 
    }
    stage('Unit testing'){
      steps{
        script{
          sh 'mvn test'
        }
      }
    }
  }
}
