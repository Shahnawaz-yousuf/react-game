pipeline{
    agent any
    tools{
        
        nodejs 'node16'
    }
    environment {
        SCANNER_HOME=tool 'sonar'
    }
    stages {
        stage('clean workspace'){
            steps{
                cleanWs()
            }
        }
        stage('Checkout from Git'){
            steps{
                git branch: 'main', url: 'https://github.com/tawfeeq421/react-game.git'
            }
        }
      
        stage("quality gate"){
           steps {
                script {
                    waitForQualityGate abortPipeline: false, credentialsId: 'Sonar' 
                }
            } 
        }
        stage('Install Dependencies') {
            steps {
                sh "npm install"
            }
        }
        
    }
}
