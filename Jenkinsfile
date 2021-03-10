#!groovy

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
//                sh "pid=\$(lsof -i:3333 -t); kill -TERM \$pid || kill -KILL \$pid"
                sh 'nohup ./mvnw spring-boot:run -Dserver.port=3333 &'
            }
        }
    }
}
