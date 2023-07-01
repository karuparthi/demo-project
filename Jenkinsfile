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
            nexusUrl: '15.206.213.232:8081', 
            nexusVersion: 'nexus3',
            protocol: 'http', 
            repository: 'http://15.206.213.232:8081/repository/jyothi/',
            version: '1.0.0'
        }
      }
    }
  } 
}      
           
