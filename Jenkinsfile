pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Greatlearningaman/flask-calculator-app.git']]])
            }
        }
    stage('Build Container') {
      steps {
        sh "docker build -t amanimage ."
      }
    }
    stage('Run Docker Container') {
      steps {
        sh "docker run -it --name amanjenkins -p 5000:5000 amanimage"
      }
    }
  }
}
