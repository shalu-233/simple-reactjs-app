pipeline {
   agent { label 'npm' }
   options {
        timeout(time: 1, unit: 'HOURS')
    } 
   triggers {
        pollSCM('* * * * *')
    } 
   stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/aditya-sridhar/simple-reactjs-app.git',
                    branch: 'master'
            }
            
        }
        stage('BUILD') {
            steps {
                    dir('simple-reactjs-app') { 
                    sh 'npm install'
                    sh 'npm run build'
                    }
            }
        }
    
   }
    post {
        success {
            mail subject: 'Build run Update' to: 'admin@gmail.com' body: 'build successfully completed'
    }
   }
}
