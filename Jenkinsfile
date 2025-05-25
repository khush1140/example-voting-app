pipeline{
    agent{label 'worker'}
    stages{
        stage("Docker build and push"){
            steps{
                sh "docker login -u khushbooheda11 -p Khushboo@4321"
                sh '''
                cd vote
                docker build -t khushbooheda11/vote:v${BUILD_NUMBER} .
                '''
                sh "docker push khushbooheda11/vote:v${BUILD_NUMBER}"
        
            }
        }
        stage("Deploy"){
            steps{
                sh "echo docker deploy"
            }
        }
    }
}
