pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Jenkins işlem alanına geçmeden önce depoyu kontrol et
                git 'https://github.com/your/helm/chart/repository.git'
            }
        }
        
        stage('Build Helm Chart') {
            steps {
                // Helm Chart'ını oluştur
                script {
                    sh 'helm package ./path/to/your/chart'
                }
            }
        }

        stage('Deploy Helm Chart') {
            steps {
                // Helm Chart'ını Kubernetes kümesine yükle
                script {
                    sh 'helm upgrade --install release-name ./your-chart-name-0.1.0.tgz'
                }
            }
        }
    }
}
