pipeline
{
    agent any
    stages
    {
        stage('Continous Download')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('Continous Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
    }
}
