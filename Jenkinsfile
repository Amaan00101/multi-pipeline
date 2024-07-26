pipeline {
    agent any

    tools {
        maven 'Maven-3.9.0'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Amaan00101/jenkins-trainig-task.git', branch: 'development',
            }
        }

        stage ('maven build') {
            steps {
                    sh "mvn clean install"                        
                }
            }

        stage('Archive Artifacts') {
            steps {
                
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
