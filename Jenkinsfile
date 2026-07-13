pipeline {
    agent any

    environment {
        SECRET_NAME = "github-credentials"
        AWS_REGION = "ap-south-1"
        GIT_REPO = "https://github.com/DeekshithSN/sample-web-application.git"
    }

    stages {

        stage('Fetch Secret') {
            steps {
                script {

                    def secret = sh(
                        script: """
                            aws secretsmanager get-secret-value \
                            --secret-id ${SECRET_NAME} \
                            --region ${AWS_REGION} \
                            --query SecretString \
                            --output text
                        """,
                        returnStdout: true
                    ).trim()

                    def json = readJSON text: secret

                    env.GIT_USERNAME = json.username
                    env.GIT_PASSWORD = json.password
                }
            }
        }

        stage('List Branches') {
            steps {
                sh '''
                    git ls-remote --heads https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/DeekshithSN/sample-web-application.git \
                    | awk '{print $2}' \
                    | sed 's#refs/heads/##'
                '''
            }
        }
    }
}
