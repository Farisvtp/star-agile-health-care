pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/Farisvtp/star-agile-health-care/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with faris'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with faris'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with faris'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with faris'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8082:8082 --name c000 myimg'
            }
        }   
    }
}
