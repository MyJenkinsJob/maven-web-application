node {
  properties([parameters([choice(choices: 'master\ndevelopment\nstaging\nproduction', description: 'Select Branch To Build', name: 'myBranch')])])
  def mvnHome = tool name: 'Maven04', type: 'maven'

  stage ('CodeCheckout'){
   echo "pulling changes from the branch ${params.myBranch}"
   git url: 'git@github.com:MyJenkinsJob/maven-web-application', branch" "${params.myBranch}"
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
