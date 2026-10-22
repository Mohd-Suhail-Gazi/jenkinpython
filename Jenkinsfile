pipeline {
    agent any

    environment {
        PATH = "C:\\Users\\suhai\\AppData\\Local\\Programs\\Python\\Python314;C:\\Users\\suhai\\AppData\\Local\\Programs\\Python\\Python314\\Scripts;${env.PATH}"
    }

    stages {
        stage('Setup & Install Dependencies') {
            steps {
                bat '''
                    python -m venv venv
                    call venv\\Scripts\\activate.bat
                    python -m pip install --upgrade pip
                    pip install -r requirment.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat '''
                    call venv\\Scripts\\activate.bat
                    python app.py
                '''
            }
        }
    }

    post {
        always {
            bat 'if exist venv rmdir /s /q venv'
        }
    }
}
