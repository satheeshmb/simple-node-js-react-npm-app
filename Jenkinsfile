pipeline {
  agent any
    
  tools {nodejs "NodeJS 21.1.0"}
    
  stages {
        
    stage('Git') {
      steps {
       git credentialsId: 'ede05712-7bf2-4720-bfab-ad4ca9163cbc', url: 'https://github.com/satheeshmb/simple-node-js-react-npm-app.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }  
            
    stage('Test') {
      steps {
         sh './jenkins/scripts/test.sh'
      }
    }

     stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
      }
  }
}
