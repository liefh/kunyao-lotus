pipeline {
  agent any
  stages {
    stage('pushCode') {
      steps {
        retry(count: 3) {
          sh 'echo \'git push -u origin master\''
        }

      }
    }

    stage('getCode') {
      steps {
        sh 'echo \'git clone https://github.com/liefh/kunyao-lotus.git\''
      }
    }

    stage('test') {
      steps {
        sh './lotus daemon'
      }
    }

    stage('testResultGood') {
      parallel {
        stage('testResultGood') {
          steps {
            echo 'good'
          }
        }

        stage('testResultBug') {
          steps {
            echo 'bug'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        sh './lotus daemon'
      }
    }

    stage('deployGood') {
      parallel {
        stage('deployGood') {
          steps {
            echo 'good'
          }
        }

        stage('deployFailed') {
          steps {
            echo 'failed'
          }
        }

      }
    }

    stage('result') {
      steps {
        echo 'balbala'
      }
    }

  }
}