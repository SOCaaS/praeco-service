pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                echo 'Installing....'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                
           }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh 'PRAECO_ELASTICSEARCH=10.0.2.15  docker-compose up --force-recreate --build -p "praeco" up -d'
            }
        }
    }
    post {
        success {
            discordSend description: "Build Success", footer: "Praeco Service", link: env.BUILD_URL, result: currentBuild.currentResult, title: JOB_NAME, webhookURL: env.SOCAAS_WEBHOOK
        }
        failure {
            discordSend description: "Build Failed", footer: "Praeco Service", link: env.BUILD_URL, result: currentBuild.currentResult, title: JOB_NAME, webhookURL: env.SOCAAS_WEBHOOK
        }
    }
}
