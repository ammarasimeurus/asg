pipeline {
    agent any
    
    parameters {
        string(name: 'ECS_CLUSTER_NAME', defaultValue: '', description: 'ECS Cluster Name')
        string(name: 'ECS_SERVICE_NAME', defaultValue: '', description: 'ECS Service Name')
        string(name: 'DESIRED_COUNT', defaultValue: '2', description: 'Desired count for ECS service')
        string(name: 'MIN_READY_PERCENT', defaultValue: '50', description: 'Minimum ready percent during deployment')
        string(name: 'MAX_HEALTHY_PERCENT', defaultValue: '200', description: 'Maximum healthy percent during deployment')
    }
    
    stages {
        stage('Update ECS Service') {
            steps {
                script {
                    // Update ECS service
                    sh "aws ecs update-service --cluster ${params.ECS_CLUSTER_NAME} --service ${params.ECS_SERVICE_NAME} --desired-count ${params.DESIRED_COUNT} --min-ready-percent ${params.MIN_READY_PERCENT} --max-healthy-percent ${params.MAX_HEALTHY_PERCENT}"
                }
            }
        }
    }
}
