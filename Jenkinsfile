pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/MamdiaDiallo/jenkins-hello-world.git'
            }
        }
        stage('Build') {
            steps {
                sh 'cd /jenkins-hello-world/javac Main.java'
            }
        }
        stage('Run') {
            steps {
                sh 'cd /jenkins-hello-world/java Main'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
            // Exemple : Envoi d'une notification (email, Slack, etc.)
            emailext(
                subject: 'Jenkins Job SUCCESS: ${JOB_NAME}',
                body: 'The Jenkins job ${JOB_NAME} completed successfully.',
                recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            )
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
            // Exemple : Remonter les logs d'erreur
            emailext(
                subject: 'Jenkins Job FAILED: ${JOB_NAME}',
                body: '''The Jenkins job ${JOB_NAME} failed.
                Please check the Jenkins console logs for details.''',
                recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            )
        }
    }
}
