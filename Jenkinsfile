pipeline{
    agent{label 'worker'}
    stages{
        stage("Docker build and push"){
            steps{
                sh "docker login -u khush1140 -p Arvi.1418"
                sh '''
                cd vote
                docker build -t khush1140/vote:v${BUILD_NUMBER} .
                '''
                sh "docker push khush1140/vote:v${BUILD_NUMBER}"
        
            }
        }
        stage("Deploy"){
            steps{
                sh "echo docker deploy"
            }
        }
    }
}
