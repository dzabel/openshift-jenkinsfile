pipeline {
    agent none
    options{
        buildDiscarder(logRotator(daysToKeepStr: '30', numToKeepStr: '30'))
    }
    stages {
        stage('init') {
            steps {
                script {
                    echo 'init'
                }
            }
        }
        stage('prepare deployment') {

            options {
                timeout(time:7, unit:'DAYS')
            }
            steps {
                script{
                    input (id: 'update_prod', message: "Update Prod?")
                }
            }
        }

        stage('do deployment') {
            when {
                expression {
                    currentBuild.result == null || currentBuild.result == 'SUCCESS'
                }
            }
            steps {
                script {
                    echo 'doDeployment'
                }
            }

        }
    }
}
