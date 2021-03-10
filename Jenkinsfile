pipeline{
    environment{
        JAVA_TOOL_OPTIONS="-Duser.home=/home/jenkins"
    }
    agent{
        dockerfile{
            label 'agent-00'
            args '-v /home/osboxes/maven:/home/jenkins/.m2 -e MAVEN_CONFIG=/home/jenkins/.m2'
        }
    }
    options{
        buildDiscarder(logRotator(numToKeepStr: '2'))
        disableConcurrentBuilds()
        disableResume()
        timestamps()
    }
    stages{
        stage('Check contents'){
            steps{
                sh 'pwd'
                sh 'ls -ltr'
            }
        }
        stage('Build'){
            steps{
                sh 'ssh -V'
                sh 'mvn --version'
                sh 'mvn clean package'
            }
        }
    }
}

