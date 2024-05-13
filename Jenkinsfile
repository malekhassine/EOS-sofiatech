def microservices = ['ecomm-order']

pipeline {
  agent any
  tools{ maven 'maven'}
  

  environment {
    DOCKERHUB_USERNAME = "malekhassine"
    // Ensure Docker credentials are stored securely in Jenkins
  }

  stages {
    stage('Checkout') {
      steps {
        // Checkout the repository from GitHub
        checkout([
          $class: 'GitSCM',
          branches: [[name: env.BRANCH_NAME]], // Checkout the current branch
          userRemoteConfigs: [[url: 'https://github.com/malekhassine/EOS-sofiatech.git']]
        ])
      }
    }
      
  
        stages {
        stage('Build product microservice') {
            steps {
                sh "mvn -v"
                sh "mvn clean install"
            }

}

  }

