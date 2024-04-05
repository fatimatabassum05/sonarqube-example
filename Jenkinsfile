pipeline{
    agent {label 'sonar_node'}
    stages{
       stage('Git Checkout Stage'){
            steps{
                git branch: 'main', url: 'https://github.com/fatimatabassum05/sonarqube-example.git'
            }
         }        
       stage('Build Stage'){
            steps{
                sh '/opt/apache-maven-3.9.6/bin/mvn clean install'
            }
         }
        stage('SonarQube Analysis Stage') {
            steps{
                withSonarQubeEnv('sonar_node') { 
                    sh "opt/apache-maven-3.9.6/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=sonarqube_1"
                }
            }
        }
    }
}
