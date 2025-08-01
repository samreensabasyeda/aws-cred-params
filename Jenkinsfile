pipeline {
    agent any

    parameters {
        string(name: 'MESSAGE', defaultValue: 'hello kloud kampus', description: 'Enter your custom message')
    }

    stages {
        stage("aws-jenkins-demo") {
            steps {
                echo "Message is: ${params.MESSAGE}"
                
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'aws-jenkins-demo',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                ]]) {
                    sh "aws ec2 describe-instances --region ap-south-1"
                }
            }
        }
    }
}
