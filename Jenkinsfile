pipeline {
      agent { node { label 'Agent-1' } }
      options{
            timeout(time: 1, unit: 'HOURS')
      }
      environment {
            USER = 'sivakumar'
      }

      stages {
            stage('Build') {
                  steps {
                        echo 'Building..'
                        sh '''
                         ls -ltr
                         pwd
                         echo "Hello from Github push webhook event"
                         printenv

                         '''
                  }
            }
            stage('Test') {
                  steps {
                        echo 'Testing..'
                  }
            }
            stage('Deploy') {
                  steps {
                        echo 'Deploying....'
                  }
            }

            stage('Example') {
            environment { 
               AUTH = credentials('ssh-auth') 
            }
            steps {
                sh 'printenv'
            }
        }
      }

      post {
            always {
                  echo 'I will always run whether job is success or not!'
            }
            success {
                  echo 'I will run only when job is success'
            }
            failure {
                  echo 'I will run only when job is fail'
            }
      }
}

