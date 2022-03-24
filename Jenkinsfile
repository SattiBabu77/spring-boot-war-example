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
                
               
                
                deploy adapters: [tomcat7(credentialsId: 'Tomcat-Credentials2', path: '', url: 'http://13.233.153.183:8084')], contextPath: '/guru', war: '**/*.war'
                
            }
            
        }
        stage("Deploy on Prod"){
            steps{
                // deploy on container -> plugin
                
               
                
                deploy adapters: [tomcat7(credentialsId: 'Tomcat-Credentials2', path: '', url: 'http://52.66.247.104:8080')], contextPath: '/guruprod', war: '**/*.war'
                
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
