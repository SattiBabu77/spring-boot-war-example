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
                
                deploy adapters: [tomcat7(credentialsId: 'Tomcat-Credentials1', path: 'app2', url: 'http://35.154.234.219:8084')], contextPath: '/app2', war: '**/*.war'
              
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
