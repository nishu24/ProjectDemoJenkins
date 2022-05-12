pipeline {
  agent any
  stages {
    stage('Quality Gate') {
        steps{
            echo 'Quality Gate'
        }
    }
    stage('Unit Testing') {
        when{
            anyOf {branch 'ft_*'; branch 'bg_*'}
        }
        steps{
        withMaven {
        sh 'mvn test'
            }
         }
    }
    stage('Build') {
        when{branch 'main'}
        steps{
            withMaven{
                sh 'mvn package -DskipTests'
            }
        }
    }
    stage('Docker Image') {
        steps{
            echo 'Docker Image'
        }
    }
    stage('Docker Deliver') {
        steps{
            echo 'Docker Deliver'
        }
    }
    stage('Wait for approval') {
        steps{
        echo 'Wait for approval'
        }
    }
    stage('Deploy') {
        steps{
        echo 'Deploy'
        }
    }
  }
}