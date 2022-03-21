pipeline {
  agent {docker 'docker'}
  stages {
    stage("verify tooling") {
      steps {
        sh '''
          sudo docker version
          sudo docker compose version 
          sudo curl --version
          sudo java --version
        '''
      }
    }  
    stage('Start container') {
      steps {
        sh 'docker compose up'
        sh 'docker compose ps'
      }
    }
    stage('Run tests against the container') {
      steps {
        sh 'curl http://localhost:3000/param?query=demo | jq'
      }
    }
  }

}
