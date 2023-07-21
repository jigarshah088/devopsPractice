pipeline {
    agent any
    
    stages {
        
       
        
        stage('SonarQube analysis') {
            steps{
                    
                    withSonarQubeEnv('sonarqube') { // If you have configured more than one global server connection, you can specify its name
                    sh "mvn clean package sonarqube:sonarqube"
                      }
                 }
        }
        stage('Deploy') {
            steps {
            sh "sudo apt-get install apache2 -y"
            sh 'sudo systemctl restart apache2'
            sh 'sudo systemctl status apache2'
            }
        }
        
    }
}

