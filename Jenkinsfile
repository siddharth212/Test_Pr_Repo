pipeline {
    agent any
    
   triggers {
        githubPullRequest {
            admin('siddharth212')
            admins('siddharth212')
            userWhitelist('siddharth212')
            userWhitelist(siddharth212)
            orgWhitelist('my_github_org')
            orgWhitelist(siddharth212)
            cron('H/5 * * * *')
            triggerPhrase('approved')
            onlyTriggerPhrase()
            useGitHubHooks()
            permitAll()
            autoCloseFailedPullRequests()
            allowMembersOfWhitelistedOrgsAsAdmin()
            extensions {
                commitStatus {
                    context('deploy to staging site')
                    triggeredStatus('starting deployment to staging site...')
                    startedStatus('deploying to staging site...')
                    statusUrl('http://mystatussite.com/prs')
                    completedStatus('SUCCESS', 'All is well')
                    completedStatus('FAILURE', 'Something went wrong. Investigate!')
                    completedStatus('PENDING', 'still in progress...')
                    completedStatus('ERROR', 'Something went really wrong. Investigate!')
                }
            }
        }
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
