#!groovy

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                echo 'pid=$(lsof -i:3333 -t) fails build if there are no process listening on port 3333'
                sh "pid=\$(lsof -i:3333 -t); kill -TERM \$pid || kill -KILL \$pid"
                script {
                    withEnv(['JENKINS_NODE_COOKIE=dontkill']) {
                        sh 'nohup ./mvnw spring-boot:run -Dserver.port=3333 &'
                    }
                }

            }
        }
    }
}
