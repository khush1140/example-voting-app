pipeline{
    agent{label 'worker'}
    options { 
        buildDiscarder(logRotator(numToKeepStr: '15'))
        disableConcurrentBuilds()
        retry(2)
        timeout(time: 10, unit: 'MINUTES')
    }
    parameters {
        string(name: 'BRNACH', defaultValue: 'develop', description: '')
        booleanParam(name: 'TEST_CASES', defaultValue: true, description: '')
        choice(name: 'ENV', choices: ['dev', 'qa', 'uat'], description: '')
    }
    triggers {
        cron('H/5 * * * *')
    }
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
        stage ("parallel testing")
        when {
                branch 'develop'
                environment name: 'DEPLOY_TO', value: 'qa'
        }
            stages("parallel"){
                stage("Linux Test"){
                    steps{
                        sh "echo linux"
                        sh "sleep 180"
                    }
                }  
                stage("Windows Test"){
                    steps{
                        sh "echo windows"
                        sh "sleep 180"
    }
}
            }
        }
    }
}
}
