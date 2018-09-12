build_root = "/home/kali/Repos/jenkinsDemo/"
vagrant_root = build_root + "/coreos-vagrant/"
exec_remote_cmd = 'sshpass -p unuzan55 ssh lamersons@localhost cd ' + build_root + '; ';

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
