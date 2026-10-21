pipeline {
    agent any

    options {
        timestamps()
    }

    stages {
        stage('Install dependencies') {
            steps {
                sh '''
                    python3.12 -m venv .venv
                    . .venv/bin/activate
                    pip install -r requirement.txt
                '''
            }
        }

        stage('Build check') {
            steps {
                sh '''
                    . .venv/bin/activate
                    python -m compileall -q hello.py
                '''
            }
        }

        stage('Run automated tests') {
            steps {
                sh '''
                    . .venv/bin/activate
                    pytest -v
                '''
            }
        }
    }
}
