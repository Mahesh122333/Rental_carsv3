

node(){
stage("git checkout"){
checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git', url: 'https://github.com/Mahesh122333/Rental_carsv3.git']]])
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

