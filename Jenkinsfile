node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
   withAnt(installation: 'LocalAnt') {
// some block
   sh "ant build"
   
    }
  }
}
