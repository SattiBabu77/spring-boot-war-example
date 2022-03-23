pipeline {
    agent any
     tools {
        maven 'Maven' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
                
                deploy adapters: [tomcat7(credentialsId: '5f7a713d-9937-4e1e-9358-ebf6d466839a', path: 'app1', url: 'http://35.154.234.219:8084/')], contextPath: 'app1', war: '**/*.war'
              
            }
            
        }
        
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
            
        }
        failure{
            echo "========pipeline execution failed========"
             
        }
    }
}
