node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
   withAnt(installation: 'Ant') {
// some block
   sh "ant build"
   
    }
  }
}
