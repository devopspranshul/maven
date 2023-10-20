pipeline {
    agent any
    environment{
        PATH = "/opt/apache-maven-3.9.5/bin:$PATH"
    }
    stages {
        stage('Clone Code') 
        {
            steps {
                git branch: "main", url: "https://github.com/devopspranshul/maven.git"
            }
        }
        stage('Build Code') 
        {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Upload S3') 
        {
            steps {
                sh "aws s3 cp /var/lib/jenkins/workspace/ s3://mymavenproject --recursive"
            }
        }
    }
}
