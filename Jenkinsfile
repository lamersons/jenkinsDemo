build_root = "/home/kali/Repos/jenkinsDemo/"
vagrant_root = build_root + "/coreos-vagrant/"
exec_remote_cmd = 'sshpass -p unuzan55 ssh lamersons@localhost cd ' + build_root + '; ';

// def jen = Jenkins.getInstance();
// def job = jen.getItem("${JOB_NAME}");
// def builds = job.getBuilds();
//
// def printClosure = {
//   println("${it.getArtifactManager()?.root().exists()}")
// }
// builds.each(printClosure)

pipeline {
    agent any
    // parameters {
    //   string(name: 'PERSON', defaultValue: "Jack Dawn", description: 'Who should I say hello to?')
    // }
    stages {
        stage('get_init_scripts') {
            steps {
                sh exec_remote_cmd + "git clone https://github.com/coreos/coreos-vagrant.git"
                sh "ls -la "
                // sh 'echo ">>>>> building.."'
                // sh 'cd simple-java-maven-app; mvn -B -DskipTests clean package'
                // echo "${params.PERSON}"
            }
        }
        // stage('') {
        //     steps {
        //         sh 'cd simple-java-maven-app; mvn test'
        //     }
        //     post {
        //         always {
        //             archiveArtifacts artifacts: 'simple-java-maven-app/target/*.jar', fingerprint: true
        //             junit 'simple-java-maven-app/target/surefire-reports/*.xml'
        //         }
        //     }
        // }
        // stage('BuildDockerImage') {
        //     agent {
        //       dockerfile true
        //         // dockerfile {
        //         //     filename 'Dockerfile.build'
        //         //     dir '.'
        //         // }
        //     }
        //     steps {
        //         sh 'echo ${NAME}-${VERSION}.jar'
        //         // sh './' + mavenAppHome + '/jenkins/scripts/deliver.sh'
        //     }
        // }
    }
}
