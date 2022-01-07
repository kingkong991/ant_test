node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
   withAnt(installation: 'Ant') {
// some block
   sh "ant sonar -Dsonar.login=47efbd52d4848bc2a0d8f44f164ac1509be2d0a0"
   
    }
  }
}


  stage("Quality Gate") {
               withSonarQubeEnv('Sonarqube Server') {
                script {
                    def sonarScanner = tool name: 'SonarQube Scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    sh "${sonarScanner}/bin/sonar-scanner " +
                    "-Dsonar.projectKey=Javabuild2 " +
                    "-Dsonar.projectName=Javabuild2 "
                         }
    timeout(time: 1, unit: 'HOURS') { 
     def qg = waitForQualityGate() 
      if (qg.status != 'OK') {
       error "Pipeline aborted due to quality gate failure: ${qg.status}"
    }
  }
}
}
