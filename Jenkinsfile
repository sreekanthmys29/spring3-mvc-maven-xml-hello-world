pipeline {
    agent any

    tools {
        maven 'mavenLocal'   // Name of your Maven installation in Jenkins
       
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout  branch'
                git 'https://github.com/sreekanthmys29/spring3-mvc-maven-xml-hello-world.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
