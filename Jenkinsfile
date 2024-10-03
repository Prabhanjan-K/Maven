pipeline
{
    agent any
    stages
    {
        stage('master Download')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('master Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('master Deploy')
        {
            steps
            {
                  deploy adapters: [tomcat9(credentialsId: '230fddb6-7cbb-498a-b57f-54a9e27c4ea8', path: '', url: 'http://172.31.1.230:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('master Testing')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
            }
        }
        stage('master Delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '230fddb6-7cbb-498a-b57f-54a9e27c4ea8', path: '', url: 'http://172.31.1.73:8080')], contextPath: 'Prodapp', war: '**/*.war'
            }
        }
    }
}
