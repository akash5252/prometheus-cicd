pipeline {
    agent any

    stages {

        stage('Verify Cluster') {
            steps {
                sh 'kubectl get nodes'
            }
        }

        stage('Add Helm Repo') {
            steps {
                sh '''
                helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
                helm repo update
                '''
            }
        }

        stage('Deploy Prometheus') {
            steps {
                sh '''
                kubectl create namespace monitoring || true

                helm upgrade --install prometheus prometheus-community/kube-prometheus-stack \
                -n monitoring \
                -f values.yaml
                '''
            }
        }
    }
}
