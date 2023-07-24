pipeline{
  agent any
  stages{
    stage('git clone'){
      steps{
        script{
          git branch: 'main', url: 'https://github.com/karuparthi/demo-project.git'
        }
      }
    }
    stage('unit test'){
      steps{
        script{
        sh 'mvn test'
        }
      }
    }
  }
}
