pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/satispat/maven-jenkins.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'tomcat_creds', path: '', url: 'http://172.31.24.208:8090')], contextPath: 'test1', war: '**/*.war'
            }
        }
        
       
    }
    
    post
    {
        always {
            archiveArtifacts artifacts: '**/*.war', fingerprint: true
        }
       
    }
    
    
    
    
    
    
}
