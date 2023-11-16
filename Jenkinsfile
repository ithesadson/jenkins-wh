pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Jenkins işlem alanına geçmeden önce depoyu kontrol et
                git 'https://github.com/ithesadson/jenkins-wh.git'
            }
        }

        stage('Build and Push Helm Chart') {
            steps {
                script {
                    def chartName = "tempchart"

                    sh "helm create $chartName"
                    sh "helm package $chartName"

                    // Send chart to harbor
                    sh "curl --data-binary \"@${chartName}-0.1.0.tgz\" http://localhost:8081/api/charts"
                    echo "Chart Pushed, Listed Charts:"
                    sh "curl -X GET http://localhost:8081/api/charts"
                }
            }
        }
    }
}
