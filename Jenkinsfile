pipeline {
    environment {
        registry = 'nishu24/ProjectDemoJenkins'
        dockerHubCreds = 'docker_hub'
        dockerImage = ''
    }
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
           script{
           echo "$registry:$currentBuild.number"
           dockerImage = docker.build "$registry"
           }
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