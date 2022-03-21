pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sq2') {
          sh '''
          
          dotnet sonarscanner begin /k:"ConsoleApp"
          dotnet build ConsoleApp.sln
          dotnet sonarscanner end
        
        '''
        }
      }
    }
  }
}
