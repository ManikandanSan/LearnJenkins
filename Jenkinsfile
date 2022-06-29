pipeline{
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }

    parameters{
        string(name:'repoName', defaultValue:'https://github.com/Sonal0409/DevOpsCodeDemo.git', description:'Enter repo Path ')
    }
    agent any

    stages{
        stage('Clone git repo')
        {
            steps{
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }
        stage('Compile the code')
        {
            steps{
                sh 'mvn compile'
            }
        }
         stage('Review the code')
        {
            steps{
                sh 'mvn pmd:pmd'
            }
        }
        stage('Testing')
        {
            steps{
               sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage ('Package')
        {
            steps{
                sh 'mvn package'
            }
        }
    }
}
