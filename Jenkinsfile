pipeline {
    agent any
    stages {
        stage('Setup') {
            steps {
                sh '''
                    python3 -m venv .venv
                    . .venv/bin/activate
                    pip install pytest
                '''
            }
        }
        stage('Run Tests') {
            steps {
                sh '''
                    . .venv/bin/activate
                    pytest test_validator.py --junitxml=report.xml
                '''
            }
        }
    }
    post {
        always {
            junit 'report.xml'
        }
    }
}
