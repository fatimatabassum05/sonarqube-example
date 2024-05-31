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
                sh 'mvn clean install'
            }
         }
        stage('SonarQube Analysis Stage') {
            steps{
                withSonarQubeEnv('sonarqube_1') { 
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=sonarqube_1"
                }
            }
        }
    }
}
