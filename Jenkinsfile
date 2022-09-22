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
        stage("deploytest"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '5cd79529-2435-4327-9cef-5b2a16a65e39', path: '', url: 'http://54.175.69.79:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
        stage("deployprod"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '5cd79529-2435-4327-9cef-5b2a16a65e39', path: '', url: 'http://18.233.166.130:8080')], contextPath: '/app', war: '**/*.war'
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
