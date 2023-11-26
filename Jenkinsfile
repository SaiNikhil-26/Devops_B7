pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/SaiNikhil-26/Devops_B7.git']]])
                sh 'mvn clean install'
            }
        }

        stage('build docker image') {
            steps {
                script {
                    sh 'docker build -t sai:1.0 .'
                }
            }
        }
stage('push image to Hub'){
steps{
script{
     withCredentials([string(credentialsId: 'Sainikhil_docker', variable: 'Sainikhil_docker')]) {
           sh 'docker login --username sainikhil26 -p ${Sainikhil_docker}'
            sh 'docker push sainikhil26/sai:1.0'
}

    }
}
}

 }
}

