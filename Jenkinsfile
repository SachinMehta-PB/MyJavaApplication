pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("JavaApplication-GithubPull"){
            steps{
                //Testing the Java Maven Application
                sh "mvn --version"
                echo "========executing A========"
            }
        }
        stage("JavaApplication-Build"){
            steps{
                //Maven clean installing and Creating a .WAR file
                echo "========executing A========"
            }
        }
        stage("JavaApplication-DeployOnTestingServer"){
            steps{

                deploy adapters: [tomcat9(credentialsId: 'afd4bc9f-39b5-44b7-9074-fe1acd1d277d', path: '', url: 'http://35.230.98.49:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
        stage("JavaApplication-DeployOnProductionServer"){
            steps{

                deploy adapters: [tomcat9(credentialsId: 'afd4bc9f-39b5-44b7-9074-fe1acd1d277d', path: '', url: 'http://34.127.121.220:8080/')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
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
