pipeline
{
    agent any
    tools {
        maven 'Maven_New'
    }
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git branch: 'main', credentialsId: 'github_creds', url: 'https://github.com/satispat/maven-jenkins.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn clean package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'tomcat_creds', path: '', url: 'http://172.31.55.133:8090/')], contextPath: 'test_path', war: '**/*.war'
            }
        }
        
        
       
    }
    

    
    
    
}
