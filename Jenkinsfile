pipeline {
    agent any
    
  

    stages {
        stage('ch1') {
            steps {
                agent{
                label 'DemoNode'
                }
                echo 'i am in node 1'
               
            
            }
        }
        
        
        stage('ch2') {
            steps {
                agent{
                label 'DemoNode2'
                }
                echo 'i am in node 2'
               
            
            }
        }
}
