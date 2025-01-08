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
}
