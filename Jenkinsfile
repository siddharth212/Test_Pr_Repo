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
            if(PR_ID != "null") {
                echo "Received a PR with following Details"
                echo "PR_ID: $PR_ID ; PR_TYPE: $PR_TYPE ; PR_TITLE: $PR_TITLE ; PR_STATE: $PR_STATE"
                // If the PR state is either MERGED or DECLINED we have to do some cleanup or else call Multibrach Pipeline
                // After the clean up we will again call the Multibranch pipeline to make sure Orphaned Jobs are removed/disabled.

                if(PR_STATE == "DECLINED" || PR_STATE == "MERGED") {
                  // Do your cleanup here, You should have all the PR Details to figure out what to clean
                  echo "Cleaning UP!!!!!!"
                }
                
            } else if(PUSH_DETAILS != "null") {
              // This check is not really required in your case. But in case you want to do something if this is a push I added this. 
              echo "This is a commit. Let's trigger the MultiBranch Pipeline"
            }
            // Always we will call the Multibranch pipeline
            echo "Triggering the Multibranch Pipeline"
            build job: "MultiYCRPipeline", wait: false
          }
      }
    }
}
