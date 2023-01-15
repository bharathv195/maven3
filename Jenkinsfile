pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                script
                {
                try
                {
                    git 'https://github.com/bharathv195/maven3.git'
                }
                catch(Exception e1)
                {
                    mail bcc: '', body: 'Continuous Delivery has been failed', cc: '', from: '', replyTo: '', subject: 'Continuous Delivery has been failed', to: 'bharathvallepu01@gmail.com'
                    exit(1)
                }
                }
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'mvn package'
                    }
                    catch(Exception e2)
                    {
                        mail bcc: '', body: 'Continuous Delivery has been failed', cc: '', from: '', replyTo: '', subject: 'Continuous Delivery has been failed', to: 'bharathvallepu01@gmail.com'
                        exit(1)
                    }
                }
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline2/webapp/target/webapp.war ubuntu@172.31.0.136:/var/lib/tomcat9/webapps/testapp7.war'
                    }
                    catch(Exception e3)
                    {
                        mail bcc: '', body: 'Continuous Delivery has been failed', cc: '', from: '', replyTo: '', subject: 'Continuous Delivery has been failed', to: 'bharathvallepu01@gmail.com'
                        exit(1)
                    }
                }
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/bharathv195/FunctionalTesting.git'
                        sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline2/testing.jar'
                    }
                    catch(Exception e4)
                    {
                        mail bcc: '', body: 'Continuous Delivery has been failed', cc: '', from: '', replyTo: '', subject: 'Continuous Delivery has been failed', to: 'bharathvallepu01@gmail.com'
                    }
                }
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'scp /home/ubuntu/.jenkins/workspace/DeclarativePipeline2/webapp/target/webapp.war ubuntu@172.31.0.135:/var/lib/tomcat9/webapps/prodapp7.war'
                    }
                    catch(Exception e5)
                    {
                         mail bcc: '', body: 'Continuous Delivery has been failed', cc: '', from: '', replyTo: '', subject: 'Continuous Delivery has been failed', to: 'bharathvallepu01@gmail.com'
                    }
                }
                
            }
        }
    }
}
