pipeline {
    agent any
    stages{
        stage('Clone FinanceMeProject'){
            steps{
                git url:'https://github.com/Ashish-kumar-8185/finance.git'
            }
        }

        stage('Packaging the code'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Building Docker image'){
            steps{
                script{
                    sh 'docker build -t financebanking .'
                    sh 'docker images'
                }
            }
        }

        stage('Containerization and Deployment'){
            steps{
                sh 'docker run -itd --name CBS -p 8082:8081 financebanking'
            }
        }

        stage('Image tag and push to DockerHub'){
            steps{
                script{
                        sh 'docker tag financebanking ashish8185/bankingimage:v1'
                        sh 'sudo docker push ashish8185/bankingimage:v1'
                }

            }
        }


   }
}
