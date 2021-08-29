pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "mymaven"
        jdk "myjava"
    }
    stages {
        stage('Compile') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/snithin1978/Devops_Adressbook.git'
                sh "mvn compile"
            }
        }
        stage('codereview') {
            steps {
                sh "mvn pmd:pmd"
            }
        }
        stage('unittest') {
            steps {
                sh "mvn test"
            }
        }
        stage('metriccheck') {
            steps {
                sh "mvn cobertura:cobertura -Dcobertura.report.format=xml"
            }
        }
        stage('package') {
            steps {
                sh "mvn package"
            }
        }
    }
}
