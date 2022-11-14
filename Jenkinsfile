pipeline {
    agent any
    
    triggers {
    GenericTrigger(
     genericVariables: [  
      [key: 'PR_STATE', value: '$.pullrequest.state', defaultValue: 'null']
     ],
     causeString: 'Triggered By Bitbucket',
     token: '',
     tokenCredentialId: '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',
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
            echo "Triggering the  Pipeline"
          }
      }
    }
}
