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


//Docker code for 9th assi
FROM openjdk:latest
WORKDIR /usr/src/app
COPY HelloWorld.java .
RUN ["javac","HelloWorld.java"]
CMD  ["java","HelloWorld"] 

//tomcat user script on notepad
<role rolename="manager-script"/>
<user username="admin" password="admin" roles="manager-script"/>

//python windows batch command assi5
virtualenv venv
source venv/bin/activate # for Linux/Mac, use 'venv\Scripts\activate' on windows 
pip install -r requirements.txt
python .\helloworld.py 


