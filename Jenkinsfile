pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Shylo-Ivan-MIT/Lab3forDocker.git'
                sh './mvnw clean compile'
                // bat '.\\mvnw clean compile'
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test'
                // bat '.\\mvnw test'
            }

            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
		    
                }
		success {
		    echo "App testing is completed"
		    sh "docker push progtech_lab3"
		}
		failure {
		echo "Something went horribly wrong"
		}
            }
        }
    }
}