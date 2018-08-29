mavenAppHome = "simple-java-maven-app"

pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo ">>>>> building.."'
                sh 'cd simple-java-maven-app; mvn -B -DskipTests clean package'
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
            steps {
                sh 'echo ${NAME}-${VERSION}.jar'
                // sh './' + mavenAppHome + '/jenkins/scripts/deliver.sh'
            }
        }
    }
}
