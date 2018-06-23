pipeline {
  agent any
    stages {
      stage('Unit Tests') {
        steps {
            ansiColor('xterm') {
              echo 'something that outputs ansi colored stuff'
              sh 'ant -f test.xml -v'
              junit 'reports/result.xml'
            }
        }
      }
      stage('build') {
        steps {
          ansiColor('xterm') {
            sh 'ant -f build.xml -v'
          }
        }
      }
    }

  post {
    always {
      archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
    }
  }
}
