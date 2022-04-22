pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/ingi-h/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t rudclthe/testweb:newnewmain .
        sudo docker push rudclthe/testweb:newnewmain
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth
	sudo kubectl set image deployment deploy-main ctn-main=rudclthe/testweb:newnewmain
        '''
      }
    }
  }
}
