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
                sh 'docker-compose -p "praeco" down'
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
