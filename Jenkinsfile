  node{
   stage('SCM Checkout'){
     git 'https://github.com/nebula1234/my-app.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   /*stage('Slack Notification'){
       slackSend baseUrl: 'https://nebbb.slack.com/services/',
       channel: 'jenkinsci',
       color: 'good', 
       message: 'welcome to jenkins slack', 
       teamDomain: 'nebbb',
       tokenCredentialId: 'slacknotify'
   } */
    def notifyBuild(String buildStatus = 'STARTED') {
  // build status of null means successful
  buildStatus =  buildStatus ?: 'SUCCESSFUL'

  // Default values
  def colorName = 'RED'
  def colorCode = '#FF0000'
  def subject = "${buildStatus}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'"
  def summary = "${subject} (${env.BUILD_URL})"
  def details = """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
    <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>"""

  // Override default values based on build status
  if (buildStatus == 'STARTED') {
    color = 'YELLOW'
    colorCode = '#FFFF00'
  } else if (buildStatus == 'SUCCESSFUL') {
    color = 'GREEN'
    colorCode = '#00FF00'
  } else {
    color = 'RED'
    colorCode = '#FF0000'
  }

  // Send notifications
  slackSend (color: colorCode, message: summary)
    
    
}

  }
