pipeline {
    agent { label 'myp1' }
    options {
        timeout(time: 2, unit: 'MINUTES') 
    }
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
         stage('Post Build') {
            steps {
                junit 'gameoflife-web/target/surefire-reports/*.xml'
                archiveArtifacts 'gameoflife-web/target/*.war'
                stash name: 'warfile', includes: 'gameoflife-web/target/*.war'
            }
        }
        stage ('copy to other node') {
            agent { label 'myp2' }
            steps {
                unstash name: 'warfile'
            }
        }
    }
}
