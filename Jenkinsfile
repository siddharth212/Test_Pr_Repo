pipeline {
    agent any
    
  

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            
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
