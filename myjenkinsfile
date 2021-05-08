node {

  stage ('checkoutCode'){
  checkout([$class: 'GitSCM', branches: [[name: '*/development']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/agunuworld4/maven-web-application']]])
  }
stage ('PackageApp'){
 sh 'mvn clean install'
}


}
