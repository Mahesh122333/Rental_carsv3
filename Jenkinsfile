
node(){

stage("git checkout"){
checkout scm
}
stage("maven build"){

sh "mvn package"
}
stage("sonar Analysic"){
     scannerHome = tool 'sonarqubescanner'
    withSonarQubeEnv('sonarqube') {
      sh "${scannerHome}/bin/sonar-scanner"
}
 timeout(time: 10, unit: 'MINUTES') {
     waitForQualityGate abortpipeline: true
}

}


}