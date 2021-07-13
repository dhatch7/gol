pipeline {
    agent { label 'myp1' }
    parameters {
        string(name: 'BUILD_TYPE', defaultValue: 'clean package', description: 'mvn build type')
    }
    triggers { upstream(upstreamProjects: 'gol-daybuild', threshold: hudson.model.Result.SUCCESS) }
    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage('Build') {
            steps {
                sh script: "mvn ${BUILD_TYPE}"
            }
        }
    }
}
