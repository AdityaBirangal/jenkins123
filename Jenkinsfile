pipeline {
    agent any
    options {
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
        timeout(time: 12, unit: 'HOURS')
        timestamps()
    }
    stages {
        stage('Requirements') {
            steps {
                // this step is required to make sure the script
                // can be executed directly in a shell
                sh('pwd')
                sh('cd Ch03')
                sh('pwd')
                sh('cd 03_05-challenge-connect-jenkins-to-github')
                                sh('pwd')
                sh('ls')
                sh('chmod +x ./algorithm.sh')
            }
        }
        stage('Build') {
            steps {
                // the algorithm script creates a file named report.txt
                sh('pwd')
                sh('./Ch03/03_05-challenge-connect-jenkins-to-github/algorithm.sh')

                // this step archives the report
                archiveArtifacts allowEmptyArchive: true,
                    artifacts: '*.txt',
                    fingerprint: true,
                    onlyIfSuccessful: true
            }
        }
    }
}
