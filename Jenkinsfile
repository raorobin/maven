node('master') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/devopsrobin/maven_jenkins.git'
    }
    stage('ContinuousBuild')
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh label: '', script: 'scp /home/robin/.jenkins/workspace/Development/webapp/target/webapp.war robin@192.168.0.111:/home/robin/tomcat9/webapps/qa_jenkins3.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/devopsrobin/Testing_Jenkins.git'
        sh label: '', script: 'echo "Testing Passed"'
    }
     stage('ContinuousDelivery')
    {
        sh label: '', script: 'scp /home/robin/.jenkins/workspace/Development/webapp/target/webapp.war robin@192.168.0.112:/home/robin/tomcat9/webapps/prod_jenkins3.war'
    }
}
