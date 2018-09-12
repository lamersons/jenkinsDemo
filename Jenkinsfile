pipeline {
  agent any
  stages {
    stage('get_init_scripts') {
      steps {
        sh exec_remote_cmd+"git clone https://github.com/coreos/coreos-vagrant.git"
        sh 'ls -la '
      }
    }
  }
}