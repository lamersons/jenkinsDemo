mavenAppHome = "simple-java-maven-app";

// def jen = Jenkins.getInstance();
// def job = jen.getItem("${JOB_NAME}");
// def builds = job.getBuilds();
//
// def printClosure = {
//   println("${it.getArtifactManager()?.root().exists()}")
// }
// builds.each(printClosure)

pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    parameters {
      string(name: 'PERSON', defaultValue: "Jack Dawn", description: 'Who should I say hello to?')
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo ">>>>> building.."'
                sh 'cd simple-java-maven-app; mvn -B -DskipTests clean package'
                echo "${params.PERSON}"
            }
        }
        stage('Test') {
            steps {
                sh 'cd simple-java-maven-app; mvn test'
            }
            post {
                always {
                    archiveArtifacts artifacts: 'simple-java-maven-app/target/*.jar', fingerprint: true
                    junit 'simple-java-maven-app/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            agent {
                dockerfile {
                    filename 'Dockerfile.build'
                    dir '.'
                }
            }
            steps {
                sh 'echo ${NAME}-${VERSION}.jar'
                // sh './' + mavenAppHome + '/jenkins/scripts/deliver.sh'
            }
        }
    }
}
