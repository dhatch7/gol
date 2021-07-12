pipeline {
    agent { label 'myp1' }
    triggers { cron('H * * * 1-5') }
    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
