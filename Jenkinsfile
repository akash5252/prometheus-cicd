pipeline {
    agent any

    environment {
        KUBECONFIG = credentials('kubeconfig-id')
    }

    stages {

        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/akash5252/prometheus-cicd.git', branch: 'main'
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

        stage('Deploy Prometheus Stack') {
            steps {
                sh '''
                helm upgrade --install prometheus prometheus-community/kube-prometheus-stack \
                -n monitoring --create-namespace \
                -f values.yaml
                '''
            }
        }

    }
}
