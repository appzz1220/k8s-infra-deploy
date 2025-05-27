pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Validate') {
      steps {
        sh 'yamllint *.yaml'
        sh 'kubeconform -strict -summary .'
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
