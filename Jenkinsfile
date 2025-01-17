pipeline{
    agent any
    stages{
        stage('Checkout the code from github'){
            steps{
                 git url: 'https://github.com/akshu20791/Banking-java-project/'
                 echo 'github url checkout'
            }
        }
        stage('Code Compile'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('Code Testing'){
            steps{
                sh 'mvn test'
            }
        }
        stage('QA'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('Package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
