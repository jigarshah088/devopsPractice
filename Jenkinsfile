pipeline {
    agent any
    triggers {
        pollSCM('') //Empty quotes tells it to build on a push
    }

    stages {
        
        stage('Checkout SCM') {
            
            
    
            steps {
                checkout([
        $class: 'GitSCM', 
        branches: [[name: '*/master']], 
        doGenerateSubmoduleConfigurations: false, 
        extensions: [[$class: 'CleanCheckout']], 
        submoduleCfg: [], 
        userRemoteConfigs: [[credentialsId: 'git_id', url: 'git@github.com:jigarshah088/devopsPractice.git']]
    ])
                
                script{
            checkout
        }
                
                
            }
        }
        
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

