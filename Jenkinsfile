  node{
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Slack Notification'){
       slackSend baseUrl: 'https://nebbb.slack.com/services/',
       channel: '#jenk-ci',
       color: 'good', 
       message: 'welcome to jenkins slack', 
       teamDomain: 'nebbb',
       tokenCredentialId: 'slack'
   }
}


