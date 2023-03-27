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
    stage('Integration testing'){
      steps{
        script{
          sh 'mvn verify'
        }
      }
    }
    stage('Build'){
      steps{
        script{
          sh 'mvn clean install'
        }
      }
    }
    stage('Code quality test'){
      steps{
        script{
          withSonarQubeEnv(credentialsId: 'jenkins-access') {
            sh 'mvn clean package sonar:sonar'
           }
        }
      }
    }
  }
}
