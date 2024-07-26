pipeline {
    agent any
 
    stages {
        stage('Checkout') {
            steps {
                git url: 'git@github.com:Amaan00101/multi-pipeline.git', branch: env.BRANCH_NAME
            }
        }
 
        stage('Build') {
            steps {
                script {
                    echo "Building production branch: ${env.BRANCH_NAME}"
                    withMaven(maven: 'Maven-3.9.0') {
                        sh 'mvn clean package'
                    }
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                script {
                    echo "Deploying to production from branch: ${env.BRANCH_NAME}"
                }
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