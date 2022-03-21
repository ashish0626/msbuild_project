pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sq2') {
          
          sh 'SonarScanner.MSBuild.exe begin /k:"ConsoleApp" /d:sonar.host.url="http://192.168.243.196:31256" /d:sonar.login="eeaf1169f5a1927f71dae0c4721de95d9b4bbcfc"'
          sh 'MsBuild.exe /t:Rebuild'
          sh 'SonarScanner.MSBuild.exe end /d:sonar.login="eeaf1169f5a1927f71dae0c4721de95d9b4bbcfc"'
        }
      }
    }
  }
}
