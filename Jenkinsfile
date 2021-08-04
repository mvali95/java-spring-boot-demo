pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr:'10'))
        timeout(time: 5, unit: 'MINUTES')
        ansiColor('xterm')
    }
    stages {
        stage('Compile & Unit Test'){   
            steps {
               sh "echo Compiling application..."
               sh "mvn compile"
            }
            
        }
        
        stage('install trufflehog') {
           sh 'pip install truffleHog'
    }
        
       stage('Run trufflehog') {
           sh 'truffleHog --regex --entropy=False . --json'
    }
        
        
    }
}
