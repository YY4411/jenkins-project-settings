pipeline {
      agent any
      stages {
            stage('Init') {
                  steps {
                        echo 'We are Starting the Init steps'
                  }
            }
            stage('Build') {
                  steps {
                        echo 'Building Sample Maven Project'
                  }
            }
            stage('Deploy') {
                  steps {
                        echo "Deploying in Staging Area"
                  }
            }
            stage('Deploy Production') {
                  steps {
                        echo "Deploying in Production Area"
                  }
            }
            stage('Deploy to Staging Environment'){
                  steps{
                        build job: 'deploy-application-staging-environment-pipeline'

                  }
            
            }
            stage('Deploy to Production Environment'){
                  steps{
                        timeout(time:5, unit:'DAYS'){
                        input message:'Approve PRODUCTION Deployment?'
                        }
                        build job: 'deploy-application-production-environment-pipeline'
                  }
        }
      }
}
