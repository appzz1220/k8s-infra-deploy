pipeline {
  agent any

  environment {
    KUBECONFIG = '' // optional if running in-cluster
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: env.BRANCH_NAME, url: 'git@github.com:appzz1220/k8s-infra-deploy.git'
      }
    }

    stage('Validate') {
      steps {
        sh 'yamllint *.yaml || true'
        sh 'kubeconform -strict -summary . || true'
      }
    }

    stage('Deploy to Kubernetes') {
      when {
        branch 'dev'
        branch 'stage'
        branch 'main'
      }
      steps {
        script {
          def namespace = env.BRANCH_NAME
          sh "kubectl apply -n ${namespace} -f ."
        }
      }
    }
  }
}
