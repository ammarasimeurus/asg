pipeline {
    agent any
    
    parameters {
        string(name: 'ECS_CLUSTER_NAME', defaultValue: 'default', description: 'ECS Cluster Name')
        string(name: 'ECS_SERVICE_NAME', defaultValue: 'default', description: 'ECS Service Name')
        string(name: 'AWS_DEFAULT_REGION', defaultValue: 'us-west-2', description: 'AWS Region')
        string(name: 'DESIRED_COUNT', defaultValue: '2', description: 'Desired count for ECS service')
    }
    
    stages {
        stage('Update ECS Service') {
            steps {
                script {
                    // Update ECS service
                    sh "aws configure set default.region ${params.AWS_DEFAULT_REGION}"
                    sh "aws ecs update-service --cluster ${params.ECS_CLUSTER_NAME} --service ${params.ECS_SERVICE_NAME} --desired-count ${params.DESIRED_COUNT}"
                }
            }
        }
    }
}
