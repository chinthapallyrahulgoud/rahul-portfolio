pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/chinthapallyrahulgoud/rahul-portfolio.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo "Building your portfolio project..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying your portfolio project..."
            }
        }
    }
}
