pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/DeekshithSN/sample-web-application.git'   
}

    stages {
        stage('List Git Branches') {
            steps {
                script {
                    sh """
                        echo "Available branches in ${GIT_REPO}:"
                        git ls-remote --heads ${GIT_REPO} | awk '{print \$2}' | sed 's#refs/heads/##'
                    """
                }
            }
        }
    }
}
