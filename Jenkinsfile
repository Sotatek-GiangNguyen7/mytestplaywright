pipeline {
  agent any
  tools {
    nodejs "20.8.0"
  }
  stages {
    stage('install playwright') {
      steps {
        sh '''
          npm i 
          npx playwright install
          npx playwright install-deps
        '''
      }
    }
    stage('help') {
      steps {
        sh 'npx playwright test --help'
      }
    }
    stage('test') {
      steps {
        sh '''
        npx playwright test
        '''
      }
      post {
        success {
          archiveArtifacts(artifacts: 'homepage-*.png', followSymlinks: false)
          sh 'rm -rf *.png'
        }
      }
    }
  }
}