pipeline {
    agent any

    environment {
        DEPLOY_DIR = "/opt/portfolio"
        SERVICE = "portfolio.service"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/chinthapallyrahulgoud/rahul-portfolio.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                echo "Stopping old service..."
                sudo systemctl stop ${SERVICE} || true

                echo "Copying new JAR file..."
                JAR=$(ls target/*.jar | head -n 1)
                sudo cp "$JAR" ${DEPLOY_DIR}/app.jar

                echo "Starting new service..."
                sudo systemctl start ${SERVICE}

                echo "Deployment completed!"
                '''
            }
        }
    }
}
