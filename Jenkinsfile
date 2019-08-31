pipeline {
    agent any
    tools {
        maven 'Maven-3'
        jdk 'JDK-8'
    }
    stages {
        stage ('Initialize') {
            steps {
                bat(/echo "PATH = ${PATH}"/)
                bat(/echo "M2_HOME = ${M2_HOME}"/)
            }
        }

        stage ('Build') {
            steps {
                bat(/mvn -Dmaven.test.failure.ignore=true install/) 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}
/*      https://jenkins.io/blog/2017/02/07/declarative-maven-project/         */
