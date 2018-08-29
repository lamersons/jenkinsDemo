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
              sh 'echo "building application"'
              sh 'cd simple-java-maven-app; ls -la'
              sh 'cd simple-java-maven-app; mvn -B-DskipTests clean package'
            }
        }
    }
}
