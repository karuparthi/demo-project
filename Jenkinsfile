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
    stage('integration testing'){
      steps{
        script{
          sh 'mvn verify'
        }
      }
    }
    stage('build step'){
      steps{
        script{
          sh 'mvn clean install package'
        }
      }
    }
    stage('code quality test'){
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
