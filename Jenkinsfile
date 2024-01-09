pipeline {
    agent any

    environment {
        // Define your environment variables here
        JAVA_HOME = "/opt/java/openjdk/bin/java"
    }

    stages {

        stage('Build') {
            steps {
                // Use your build tool (e.g., Maven) to compile the project
                sh 'echo $JAVA_HOME'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                // Run tests
                sh 'mvn test'
            }
            post {
                always {
                    // Archive test results, JUnit format assumed
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deployment steps, customize as per your deployment process
                echo 'Deploying application'
                // e.g., sh './deploy.sh'
            }
            post {
                success {
                    echo 'Deployment successful!'
                }
                failure {
                    echo 'Deployment failed.'
                }
            }
        }
    }

    post {
        always {
            // Post-build actions like cleaning up
            cleanWs()
        }
    }
}
