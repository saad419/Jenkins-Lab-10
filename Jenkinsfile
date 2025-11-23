pipeline {
    agent any

    // Define environment variables
    environment {
        VERSION = '1.0.0'
    }

    // Define parameters
    parameters {
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run Test Stage?')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building version: ${env.VERSION}"
            }
        }
        stage('Test') {
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo "Testing version: ${env.VERSION} with conditions.."
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying version: ${env.VERSION} ...."
            }
        }
    }

    post { 
        always {
            echo 'Pipeline Completed'
        }
    }
}
