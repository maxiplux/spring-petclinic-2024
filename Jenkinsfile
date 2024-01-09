pipeline {
  agent any
  environment {
        // Define your environment variables here
        JAVA_HOME = "/opt/java/openjdk/"
    }
  stages {
    stage('Build') {
      steps {
        sh 'echo $JAVA_HOME'
        sh 'gradle clean package'
      }
    }

    stage('Test') {
      post {
        always {
          junit '**/target/surefire-reports/TEST-*.xml'
        }

      }
      steps {
        sh 'mvn test'
      }
    }

    stage('Deploy') {
      post {
        success {
          echo 'Deployment successful!'
        }

        failure {
          echo 'Deployment failed.'
        }

      }
      steps {
        echo 'Deploying application'
      }
    }

  }

  post {
    always {
      cleanWs()
    }

  }
}
