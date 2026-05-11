pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/leniVithu/devops-158-LeniMoras-tp-v2.git'
            }
        }

        stage('Install dependencies') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    . venv/bin/activate
                    python -m pytest test_app.py -v --tb=short
                '''
            }
        }

        stage('Restart Flask app') {
            steps {
                sh '''
                    pkill -f "python app.py" || true
                    sleep 2
                    . venv/bin/activate
                    nohup python app.py > flask.log 2>&1 &
                    sleep 3
                    echo "Flask redemarre sur le port 5000"
                '''
            }
        }
    }

    post {
        success {
            echo 'Deploiement automatique reussi ! BRAVO DAMN'
        }
        failure {
            echo 'Echec du pipeline. - AIE AIE AIE CA PUE'
        }
    }
}
