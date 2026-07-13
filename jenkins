pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/DeekshithSN/sample-web-application.git'
    }

    stages {
        stage('List Branches') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'github-creds',
                    usernameVariable: 'GIT_USER',
                    passwordVariable: 'GIT_TOKEN'
                )]) {
                    sh '''
                        git ls-remote --heads https://${GIT_USER}:${GIT_TOKEN}@github.com/DeekshithSN/sample-web-application.git
                    '''
                }
            }
        }
    }
}
