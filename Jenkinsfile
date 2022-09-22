pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                sh "mvn test"
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
            }
            
        }
        stage("Deploytest"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '392444ff-9733-4baf-a36a-2dc2dd2bc97d', path: '', url: 'http://54.175.69.79:8080')], contextPath: '/app', war: '**/*.war'
            }
            
        }
        stage("Deployprod"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '392444ff-9733-4baf-a36a-2dc2dd2bc97d', path: '', url: 'http://44.204.5.18:8080/')], contextPath: '/app', war: '**/*.war'
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
