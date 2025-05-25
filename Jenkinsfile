pipeline{
    agent{label 'worker'}
    stages{
        stage("Docker build and push"){
            steps{
                sh "echo docker build"
            }
        }
        stage("Deploy"){
            steps{
                sh "echo docker deploy"
            }
        }
    }
}
