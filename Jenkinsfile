pipeline {
  agent any
  stages {
    stage('build') {
      when {
        changeset "helloworld/**"
      }
      steps {
        dir("${env.WORKSPACE}/helloworld/"){
          sh 'mvn clean install'
          sh 'docker build -t helloworld .'
        }
      }
    }
    stage('CD') {
        when {
          changeset "helloworld/**"
        }
        steps {
          sh 'kubectl rollout restart deploy helloworld'
        }
    }

    stage('k8s update') {
      when {
        changeset "kubernetes/**"
      }
      steps {
        sh 'kubectl apply -k kubernetes/'
      }
    }
  }
}