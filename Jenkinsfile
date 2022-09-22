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
                deploy adapters: [tomcat9(credentialsId: '1b9ee3d8-fa05-402c-935c-bba3bd0b02dd', path: '', url: 'http://54.157.39.194:8080')], contextPath: '/app', war: '**/*.war'
              
            }
            
        }
        stage("Deploy on Prod"){
            
            
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: '1b9ee3d8-fa05-402c-935c-bba3bd0b02dd', path: '', url: 'http://54.211.60.24.3:8080')], contextPath: '/app', war: '**/*.war'

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
