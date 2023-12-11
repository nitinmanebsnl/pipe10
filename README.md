# pipe10

//pipeline script 

pipeline{
    agent any
    tools{
        maven "Maven"
    }
    stages{
        stage("Build Maven"){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/VedantK1610/HelloWorld']])
            }
        }
        stage("Build Docker image"){
            steps{
            script{
                bat "docker build -t vedantk1610/assignment10 ."
            }
            }
        }
        stage("push docker"){
            steps{
            script{
                bat "docker login -u vedantk1610 -p VedantDocker@123"
                bat "docker push vedantk1610/assignment10"
            }
            }
        }
    }
}
