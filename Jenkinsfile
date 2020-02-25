pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage ('build docker image'){
            when {
               branch 'master'
            }
            steps{
                script{
                    app=docker.build("tanmayi789/train-schedule")
                    app.inside{
                        sh 'echo $(curl localhost 8080)'
                    }
                }
            }
        }
            
    
    }
    
    
    
}
