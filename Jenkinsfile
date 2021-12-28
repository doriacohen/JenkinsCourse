pipeline { 
agent any
    stages {
        stage('Clone Git Repository') {
            steps {
                git 'https://github.com/gr455/jenkins-demo.git'
            }
        }
        stage('Run Code') {
            steps {
                sh "/usr/bin/python3 hello.py"
            }
        }
     stage('Test Code') {
            steps {
                sh "/usr/bin/python3 test.py"
            }
        }
    } 
}
