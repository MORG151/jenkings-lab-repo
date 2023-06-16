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
                withCredentials([string(credentialsId: '08a2e219-d455-4d81-9305-5afc286cde2b', variable: 'secvar')]) {
    // some block
                    echo secvar 
                    
                }
                archiveArtifacts artifacts: '**', followSymlinks: false
            }
        }
        
        
        
    }
}
