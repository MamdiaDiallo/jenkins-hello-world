pipeline {
    agent any // Utilise un agent disponible pour exécuter la pipeline
    stages {
        stage('Clone Repository') {
            steps {
                // Clone le dépôt
                git branch: 'main', url: 'https://github.com/MamdiaDiallo/jenkins-hello-world.git'
            }
        }
        stage('Build') {
            steps {
                // Compile le fichier Main.java
                sh 'cd /jenkins-hello-world/javac Main.java'
            }
        }
        stage('Run') {
            steps {
                // Exécute le programme Java
                sh 'cd /jenkins-hello-world/java Main'
            }
        }
    }
}
