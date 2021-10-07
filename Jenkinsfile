pipeline {
     agent {
          docker {
               image 'maven:3-jdk-8'  
               args '-p 33333:8080' 
          }
     }
     environment {
          HOME = '.'
     }
     stages {
          stage('Source') {
               steps {
                    git branch: 'main',
                        url: 'https://github.com/ThitiratL/wisdom-book'
               }
          }
          stage('Build') {
               steps {
                    bat 'mvn package -DskipTests'
               }
          }
          stage('Test') {
               steps {
                    echo 'testing...'
               }
          }
          stage('Deploy') {
               steps {
                    bat 'java -jar ./target/book-0.0.1-SNAPSHOT.jar'
               }
          }
     }
}
