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
      
  
        stage('Build') {
            when {
                expression { (env.BRANCH_NAME == 'dev') || (env.BRANCH_NAME == 'test') || (env.BRANCH_NAME == 'master') }
            }
            steps {
                script {
                    // Build each microservice using Maven
                    for (def service in microservices) {
                        dir(service) {
                            sh 'mvn clean install'
                        }
                    }
                }
            }
        }

}

  }
}
