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
                sh '''
                sudo docker build -t nodeapp .
                sudo docker tag nodeapp:latest seiflabs/diteschool:0.0.2
                sudo docker push seiflabs/diteschool:0.0.2
                
                
                
                '''
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
