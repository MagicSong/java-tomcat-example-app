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
                sh 'mvn -B -DskipTests clean package'
                echo "正在构建项目，mvn -B -DskipTests clean package"
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
                echo '正在执行测试，mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                    echo '执行后续测试，target/surefire-reports/*.xml'
                }
            }
        }
    }
}
