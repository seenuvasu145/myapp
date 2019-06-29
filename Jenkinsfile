node{
    stage('SCM Checkout'){
         git 'https://github.com/seenuvasu145/myapp.git'
}
    stage('Compile-Package'){

         def mvnHome = tool name: 'MAVEN', type: 'maven' 
         sh "${mvnHome}/bin/mvn package"
} 
    
    
 stage('Slack Notification'){
           slackSend baseUrl: 'https://esafeworkspace.slack.com/services/hooks/jenkins-ci/', 
           channel: '#pipeline', color: 'good', 
           message:"${currentBuild.result}: ${BUILD_URL} ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}", 
           teamDomain: 'esafe build notification', 
           tokenCredentialId: 'jenkins-slack-notification',
           body: '${currentBuild.result}: ${BUILD_URL}',
           subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}'

} 

    stage('Attachment Log'){
          emailext attachLog: true, body: '${currentBuild.result}: ${BUILD_URL}', 
          compressLog: true, replyTo: 'mohamed.sadiqh@gmail.com', 
          subject: 'Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}', to: 'vasucena145@gmail.com'
}

}
