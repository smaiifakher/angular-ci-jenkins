pipeline {
    agent any
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
        stage('NPM') {
             steps{
                script{
                    sh "npm --version"
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
        stage('Build'){
            steps{
                script{
                    sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }
        }

    }
}
