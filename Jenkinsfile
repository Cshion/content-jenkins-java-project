pipeline {
  agent any
  
  options {
      ansiColor('xterm')
  }

  environment {
    MAVEN_OPTS = '-Djansi.force=true'
  }

  stages {
    stage('Unit Tests') {
      steps {
        echo "Hello \u001B[31mRed\u001B[m"
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
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
