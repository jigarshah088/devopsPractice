pipeline {
    agent any
    
    stages {
        
       
        
        
        stage('Deploy') {
            steps {
            sh "sudo apt-get install apache2 -y"
            sh 'sudo systemctl restart apache2'
            sh 'sudo systemctl status apache2'
            }
        }
        
    }
}

