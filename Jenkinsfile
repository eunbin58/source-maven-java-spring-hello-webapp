pipeline {
        agent any

        triggers {
                pollSCM('* * * * *')
        }

        stages {
                stage('Checkout') {
                        steps {
                                git branch: 'master',
                                url: 'https://github.com/eunbin58/source-maven-java-spring-hello-webapp.git'
                        }
                }
                stage('Build') {
                        steps {
                                sh 'mvn clean package'
                        }
                }
                stage('Deploy') {
                        steps {
                                deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', url: 'http://192.168.56.12:8080')], contextPath: null, war: 'target/hello-world.war'
                        }
                }
        }
}

