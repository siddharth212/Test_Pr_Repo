pipeline {
    agent any
    
    triggers {
    GenericTrigger(
     genericVariables: [  
      [key: 'PR_STATE', value: '$.pullrequest.state', defaultValue: 'null']
     ],
     causeString: 'Triggered By Bitbucket',
     token: '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',
     tokenCredentialId: '',
     printContributedVariables: true,
     printPostContent: true,
     silentResponse: false
    )
  }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                echo 'PR_STATE:$PR_STATE'
            }
        }
        
        stage('ProcessWebHook') {
      steps {
          script {
            echo "Received a Webhook Request from github."
            // Always we will call the Multibranch pipeline
            echo "Triggering the Multibranch Pipeline"
            build job: "MultiYCRPipeline", wait: false
          }
      }
    }
}
