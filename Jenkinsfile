pipeline {
    agent any

    stages {
		stage ('Checkout') {
			steps { 
				checkout scm
			}
		}
        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build the project') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Test the project') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed'
        }
        success {
            echo '✅ Build finished successfully'
        }
        failure {
            echo '❌ Build failed (successfully :?)'
        }
    }
}