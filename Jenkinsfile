pipeline{
    agent any
    stages{
        stage('Continuous Download'){
            steps{
            git 'https://github.com/intelliqittrainings/maven.git'
            }
         }
        stage('Continuous Build'){
            steps{
                sh 'mvn package'
            }
         }
        stage('Countinuous Deploy'){
            steps{
                sh 'scp /var/lib/jenkins/workspace/ScriptedPipeline1/webapp/target/webapp.war ubuntu@172.31.15.226:/var/lib/tomcat9/webapps/testapp.war'
            }
       
         }
        stage('Continuous Testing'){
            steps{
                 git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline1/testing.jar'
            }
        }   
    }
    post{
        success{
            sh 'scp /var/lib/jenkins/workspace/ScriptedPipeline1/webapp/target/webapp.war ubuntu@172.31.7.50:/var/lib/tomcat9/webapps/prodapp.war'
        }
    }
   
}       
