pipeline {
  /*
   * TODO: Implement pipeline stages/steps
   *   See documentation: https://www.jenkins.io/doc/book/pipeline/syntax/#stages
   */

   pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Compiling the application
                sh './gradlew assemble'
            }
        }

        stage('Test') {
            steps {
                // Running the tests
                sh './gradlew test'
            }
        }
    }

    post {
        always {
            // Archive build results
            archiveArtifacts artifacts: '**/build/libs/*.jar', fingerprint: true
        }
        success {
            echo 'Build and tests were successful!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}

}
