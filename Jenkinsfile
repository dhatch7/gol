pipeline {
    agent { label 'myp1' }
    triggers { upstream(upstreamProjects: 'gol-daybuild', threshold: hudson.model.Result.SUCCESS) }
    stages {
        stage('SCM') {
            steps {
                echo $BRANCH_TO_BE_BUILD
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
