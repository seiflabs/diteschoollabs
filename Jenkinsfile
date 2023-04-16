pipeline {
    agent any
    environment {
		DOCKERHUB_CREDENTIALS=credentials('docker_hub_creds')
	}
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
                #echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin
                echo "dckr_pat_aUI53BiZkGQUIRUWaAuvUqFFWNA" | sudo docker login -u seiflabs --password-stdin
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
