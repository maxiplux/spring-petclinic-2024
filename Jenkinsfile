pipeline {
  agent any
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
  environment {
    JAVA_HOME = '/opt/java/openjdk/bin/java'
  }
  post {
    always {
      cleanWs()
    }

  }
}