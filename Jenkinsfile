pipeline {
    agent any

    // Define tools
    tools {
        maven 'Maven' // Name of the Maven installation in Jenkins Global Tool Configuration
    }

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
                // Run Maven on Windows
                bat 'mvn -version'
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo "Testing with conditions .."
                echo "Testing version: ${env.VERSION} with conditions.."
                // Example Maven test command (Windows)
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version: ${env.VERSION} ...."
                // Example Maven deploy command (Windows)
                bat 'mvn deploy'
            }
        }
    }

    post { 
        always {
            echo 'Pipeline Completed'
        }
    }
}
