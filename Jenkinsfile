node {
  properties([parameters([choice(choices: 'master\ndevelopment\nstaging\nproduction', description: 'Select Branch To Build', name: 'myBranch')])])
  def mvnHome = tool name: 'Maven04', type: 'maven'

  stage ('CodeCheckout'){
    checkout([$class: 'GitSCM', branches: [[name: '*/development']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/agunuworld4/maven-web-application']]])
  }

  stage ('packageApplication'){
    sh "${mvnHome}/bin/mvn clean install package"
  }
  stage ('AlertEmail'){
  mail bcc: '', body: 'Jenkins checkout and App packaging was succuful', cc: '', from: '', replyTo: '', subject: 'myPipiline Jenkins Notifications', to: 'myckaexam@gmail.com'
  }

  stage('slackAlert'){
  slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'slackjenkins', color: 'good', message: 'myPipeline deployments', teamDomain: 'EghosaTech', tokenCredentialId: 'slackjenkins05072021'
  }
}
