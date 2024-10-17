pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }

    post {
        always {

            script {
                // Envia informações do build para o Jira
                jiraSendBuildInfo(
                    site: 'lohan-petermann.atlassian.net' // Nome do site Jira configurado no Jenkins
                )
            }

            script {
                // Envia informações de deployment para o Jira
                jiraSendDeploymentInfo(
                    site: 'lohan-petermann.atlassian.net', // Nome do site Jira configurado no Jenkins
                    environmentId: 'main', // ID único do ambiente
                    environmentName: 'JIRA-2', // Nome do ambiente no Jira
                    environmentType: 'staging', // Tipo do ambiente (production, staging, testing, etc.)
                    serviceIds: ['service-2'] // IDs de servico relevantes
                )
            }
        }
    }
}
