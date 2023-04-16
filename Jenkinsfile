pipeline {
    agent any

    stages {
        stage ('checkout') {
            steps {
            checkout([$class: 'GitSCM',
            branches: [[name: '*/seif']],
            doGenerateSubmoduleConfigurations: false,
            extensions: [[$class: 'CleanCheckout']],
            submoduleCfg: [],
            userRemoteConfigs: [[credentialsId: 'git-key', url: 'git@github.com:seiflabs/diteschoollabs.git']]
         ])
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
