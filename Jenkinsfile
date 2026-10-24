pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
               git branch: 'main', url: 'https://github.com/Chakrinitesh/EKS-Terraform.git'
            }
        }
        stage('checkov-scan') {
            steps {
                sh ''' 
                     python3 -m venv venv
                    ./venv/bin/pip install --upgrade pip
                    ./venv/bin/pip install checkov
                    ./venv/bin/checkov checkov --version
                    ./venv/bin/checkov -f main.tf --output json  results.json || true 
                   '''
            }
        }
    }
}
