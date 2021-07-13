pipeline {
    agent { label 'myp1' }
    parameters {
        string(name: 'BRANCH_TO_BE_BUILD', defaultValue: 'developer', description: 'add branch details')
    }
    triggers { upstream(upstreamProjects: 'gol-daybuild', threshold: hudson.model.Result.SUCCESS) }
    stages {
        stage('SCM') {
            steps {
                echo "${BRANCH_TO_BE_BUILD}"
        
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
