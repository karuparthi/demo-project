pipeline{
  agent {label 'java-builds'}
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
      stage('upload to nexus'){
        steps{
          script{
            nexusArtifactUploader artifacts: 
            [
              [
                artifactId: 'springboot', 
                classifier: '', 
                file: 'target/Uber.jar', 
                type: 'jar'
              ]
            ], 
              credentialsId: 'nexus', 
              groupId: 'com.example', 
              nexusUrl: '13.49.221.141:8081', 
              nexusVersion: 'nexus3', 
              protocol: 'http', 
              repository: 'evening-batch', 
              version: '1.0.0'
          }
        }
      }
    
  }
}
