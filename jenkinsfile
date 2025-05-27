pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Deploy to Kubernetes') {
      when {
        anyOf {
          branch 'dev'
          branch 'stage'
          branch 'main'
        }
      }
      steps {
        script {
          def ns = env.BRANCH_NAME?.replaceFirst(/^origin\//, '') ?: 'dev'
          sh "kubectl apply -n ${ns} -f ."
        }
      }
    }
  }
}
