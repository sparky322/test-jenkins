pipeline {
  agent docker
  stages {
    stage("verify tooling") {
      steps {
        sh '''
          docker version
          docker info
          docker compose version 
          curl --version
          jq --version
        '''
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
