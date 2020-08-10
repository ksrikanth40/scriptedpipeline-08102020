node('master') 
{
    stage('continuous download') 
    {
    git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('continuous build') 
    {
    sh label: '', script: 'mvn package'
    }
    stage('continuous deployment')
    {
    sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.54.41:/var/lib/tomcat8/webapps/testapp.war'
    }
    stage('continuous testing') 
    {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    
    sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    
    }
    stage('continuous delivery')
    {
    sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.55.94:/var/lib/tomcat8/webapps/spprodapp.war'
    }
}

