pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                git 'https://github.com/dadaramjadhav/spring-boot'
            }
        }
        stage('build'){
             steps{
                 withMaven(maven: 'maven3.9.9') {
                 bat 'mvn clean package'
                }      
             }
        }
        stage('static code analsis'){
             steps{
                 withMaven(maven: 'maven3.9.9') {
                 bat 'mvn sonar:sonar  -Dsonar.host.url=http://localhost:9000/ -Dsonar.login=ff9fe11e7bbbf6ac68d0af92e0c0f9a53082a806'
                }      
             }
        }
      stage('test'){
             steps{
                 withMaven(maven: 'maven3.9.9') {
                 bat 'mvn test'
                }      
             }
        }
      stage('public url'){
             steps{
                 withMaven(maven: 'maven3.9.9') {
                 echo 'http://localhost:8081/'
                }      
             }
        }

    }
}
