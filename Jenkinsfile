def projectName = 'flask-calculator-app'
def version = "0.0.${currentBuild.number}"
def dockerImageTag = "${projectName}:${version}"

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
        sh "docker build -t ${dockerImageTag} --build-arg PYTHON_MAIN_FILE=app.py ."
      }
    }
    stage('Run Docker Container') {
      steps {
        sh "docker run -it --name amanjenkins -p 5000:5000 ${dockerImageTag}"
      }
    }
  }
}
