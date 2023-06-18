pipeline {
    agent any
    tools {nodejs "NodeJS16"}
    environment {
        NODE_ENV='production'
    }

    stages {
        stage('Source') {
            steps {
                echo NODE_ENV
                git 'https://github.com/MORG151/node-js-sample'
            }
        }

        stage('Build') {
            environment {
               NODE_ENV='staging'
                   }
            steps {
                echo NODE_ENV
                sh 'npm install'
            }
        }

        stage('saveArtifacts') {
            steps {
                withCredentials([string(credentialsId: 'f0af62f0-a77a-4493-adf0-a9dbf268ff82', variable: 'secretvar')]) {
    // some block
                    echo secretvar
                    
                }
                archiveArtifacts artifacts: '**', followSymlinks: false
            }
        }
        
        
        
    }
}