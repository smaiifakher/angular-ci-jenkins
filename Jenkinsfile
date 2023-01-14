pipeline {
    agent any
    tools {nodejs "nodejs"}
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '00efe0c8-3554-49dc-b3a3-f76adf79c00b',
                            url: 'https://github.com/smaiifakher/angular-ci-jenkins']]])
                }
            }
        }
        stage('Install') {
             steps{
                script{
                    sh "npm install"
                }
            }
        }
        stage('Version') {
            steps{
                script{
                    sh "ng version"
                }
            }
        }
        stage ('code quality'){
            steps{
                sh 'ng lint'
            }
        }

        stage('Serve') {
            steps{
                script{
                    sh "ng build"
                }
            }
        }
    }
}
