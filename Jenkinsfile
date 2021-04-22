pipeline {
  agent any
  stages {
    stage('clone') {
      git clone "https://github.com/narayana3619/tech_mahindra.git"
    }
    stage('build') {
      sh 'mvn build'
    }
  }
  post {
    always {
      mail to: swamibandaru3@gmail.com, subject: 'The Pipeline failed :('
    }
  }
}
