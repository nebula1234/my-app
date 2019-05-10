  node{
   stage('SCM Checkout'){
     git 'https://github.com/nebula1234/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Slack Message') {
            steps {
                slackSend channel: '#jenkins',
                    color: 'good',
                    message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
    /*stage('Slack Notification'){
       slackSend baseUrl: 'https://hooks.slack.com/services/',
       channel: '#jenkinsci',
       color: 'good', 
       message: 'welcome to jenkins slack', 
       teamDomain: 'nebbb',
       tokenCredentialId: 'slacknotify'
   } */
    

  }
