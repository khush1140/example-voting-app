pipeline{
    agent{label 'worker'}
    stages{
        stage("Docker build and push"){
            steps{
                sh "docker login -u khushbooheda11 -p Khushboo@4321"
                sh '''
                      cd vote
                docker build -t khushboo/vote:v${BUILD_NUMBER} .
                '''
                sh "docker push khushboo/vote:v${BUILD_NUMBER}"
        
            }
        }
        stage("Deploy"){
            steps{
                sh "echo docker deploy"
            }
        }
    }
}
