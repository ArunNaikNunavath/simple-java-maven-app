// This is a Declarative Pipeline
pipeline {
    // 1. Specify the agent (server) to run on
    agent any

    // 2. Define the tools to use (from Manage Jenkins > Tools)
    tools {
        jdk 'JDK-17'
        maven 'Maven-3.9' // Use the exact name you gave it in Jenkins
    }

    // 3. Define the stages of the pipeline
    stages {
        
        // --- BUILD STAGE ---
        stage('Build') {
            steps {
                // Use 'bat' for Windows batch commands
                bat 'mvn clean package -DskipTests'
            }
        }

        // --- TEST STAGE ---
        stage('Test') {
            steps {
                // This command runs the tests
                bat 'mvn test'
            }
            post {
                // This archives the test results to see in the Jenkins UI
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        // --- DEPLOY STAGE ---
      stage('Deploy') {
    steps {
        echo 'Deploying the application...'
        // Use 'START' for Windows to run this in a new window
        // This prevents the Jenkins build from hanging
        bat 'START java -jar target/simple-java-maven-app-1.0-SNAPSHOT.jar'
        echo 'Application deployed.'
    }
}
    }
}