  node{
   stage('SCM Checkout'){
     git 'https://github.com/nebula1234/my-app.git'
   }
   stage('Compile-Package'){
    
     slackSend "Build Started - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)" 
     def mvnHome =  tool name: 'maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
  
    stage('Slack Notification'){
       slackSend baseUrl: 'https://hooks.slack.com/services/',
       channel: '#jenkinsci',
       color: 'good', 
       message: 'welcome to jenkins slack', 
       teamDomain: 'nebbb',
       tokenCredentialId: 'slacknotify'
   } 
    

  
  }
