node('master') {
    stage('ContinousDownload')
    {
        git 'https://github.com/ArkLearnersEdge/maven.git'
    }
     stage('ContinousBuild')
     {
         sh 'mvn package'
     }
    stage('Continous Deploy')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/dev_1/webapp/target/webapp.war ubuntu@172.31.92.88:/var/lib/tomcat8/webapps/testapp'
    }
    stage('Continous Testing')
    {
        git 'https://github.com/ArkLearnersEdge/FunctionalTesting.git'
        sh 'java -jar  /home/ubuntu/.jenkins/workspace/dev_1/testing.jar'
    }
    stage('Continous Delivery')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/dev_1/webapp/target/webapp.war ubuntu@172.31.83.133:/var/lib/tomcat8/webapps/prodapp'
    }
}
