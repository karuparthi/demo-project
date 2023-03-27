pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/rajeshvardhanbusam/demo-project.git'
                }
            }
        }
        stage('UNIT testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        stage('Integration testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('Maven build'){
            
            steps{
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        stage('Static code analysis'){
            
            steps{
                
                script{
                    
                    withSonarQubeEnv(credentialsId: 'jenkins-access') {
                        
                        sh 'mvn clean package sonar:sonar'
                    }
                   }
                    
                }
            }
        stage('upload artifact to nexus'){
            steps{
                script{
                    nexusArtifactUploader artifacts: 
                    [
                        [
                            artifactId: 'springboot', 
                            classifier: '', 
                            file: 'targets/Uber.jar', 
                            type: 'jar'
                        ]
                    ], 
                        credentialsId: 'nexus', 
                        groupId: 'com.example', 
                        nexusUrl: '13.49.221.141:8081', 
                        nexusVersion: 'nexus3', 
                        protocol: 'http', 
                        repository: 'demo', 
                        version: '1.0.0'
                }
            }
        }
        }
        
}
