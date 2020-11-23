pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''#mvn -version 
#mvn install
#mvn compile'''
        dir(path: 'server') {
          git(url: 'https://github.com/benjaminresch/simple-java-maven-app', branch: 'master', credentialsId: 'benjamin_git')
          sh 'mvn -B -DskipTests clean package'
        }

      }
    }

    stage('error') {
      steps {
        sh 'tree'
      }
    }

    stage('Clean up') {
      steps {
        cleanWs(cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, cleanWhenSuccess: true, cleanWhenUnstable: true)
      }
    }

  }
}