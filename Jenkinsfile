pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "mymaven"
    }

    stages {
        stage('Compile') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/Iswarya680/web-app.git'

                // Run Maven on a Windows agent
                bat "mvn compile"
            }
        }

        stage('Package') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/poojabolla/webapp-java.git'

                // Run Maven on a Windows agent
                bat "mvn clean package"
            }
        }
    }

    post {
        success {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.war'
        }
    }
}

