pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr:'10'))
        timeout(time: 5, unit: 'MINUTES')
        ansiColor('xterm')
    }
    stages {
        stage('Checkout'){
            steps {
              step([$class: 'WsCleanup'])
              git(
                  url: 'https://dso-user@github.com/dso-user/java-spring-boot-demo-template.git',
                  credentialsId: 'jenkins',
                  branch: "master"
                 )
            }
        }
        stage('Compile & Unit Test'){   
            steps {
               sh "echo Compiling application..."
               sh "mvn compile"
            }
        }
    }
}
