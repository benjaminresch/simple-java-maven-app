pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn -version'
        dir(path: 'server') {
          git(url: 'https://github.com/benjaminresch/simple-java-maven-app', branch: 'master', credentialsId: 'benjamin_git')
          sh '#mvn -B -DskipTests clean package'
        }

      }
    }

    stage('error') {
      steps {
        cleanWs(cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, cleanWhenSuccess: true, cleanWhenUnstable: true, cleanupMatrixParent: true, deleteDirs: true, disableDeferredWipeout: true)
      }
    }

  }
}