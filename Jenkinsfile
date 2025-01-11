pipeline {
    agent any // Définit l'agent ou l'environnement d'exécution
    stages {
        stage('clone') {
            steps {
                sh "rm -rf *"
                sh "git clone https://github.com/MamdiaDiallo/jenkins-hello-world.git"
            }
        }
        stage('Build') {
            steps {
                sh 'cd jenkins-hello-world/ javac Main.java' // Exemple : compilation avec Maven
            }
        }
        stage('run') {
            steps {
                sh 'cd jenkins-hello-world/ && java Main.java' // Déploiement
            }
        }
    }
    post {
        Success {
            echo 'Pipeline completed successfully!'
            emailext(
                subject:'Jenkins job success: ${JOB_NAME}',
                body: 'The job ${JOB_NAME} completed successfully.',
                recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                )
        }
         faillure {
             echo 'Pepeline failed. chech logs for details.'
             emailext(
                 subject: 'Jenkins Job FAILED: ${JOB_NAME}',
                 body: '''The Jenkins job ${JOB_NAME} failed.
                 please check the Jenkins console ''',
                 recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                 )
         }
    }         
    
}
