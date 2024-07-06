pipeline {
    agent any

    environment {
        ENV = ""
    }

    stages {

        stage('Setting Up') {
            steps {
                script {
                    switch(env.BRANCH_NAME) {
                        case "develop":
                            env.ENV = "dev"
                            break
                        case "qa":
                            env.ENV = "qa"
                            break                           
                        case "prod":
                            env.ENV = "prod"
                            break
                        default:
                            echo "Branch name '${env.BRANCH_NAME}' is not recognized. Setting environment to 'unknown'."
                            error "Unrecognized branch name. Failing the build."
                            break
                        }
                }
            }
        }

        stage('Terraform init') {
            steps {
                script {
                    echo 'Running terraform init'
                }
            }
        }

        stage('Terraform plan') {
            steps {
                script {
                    echo 'Running terraform plan'
                }
            }
        }

        stage('Waiting for approvals') {
            steps {
                script {
                    echo 'Waiting for approvals'
                }
            }
        }

        stage('Terraform apply') {
            steps {
                script {
                    echo 'Running terraform apply'
                }
            }
        }
    }

    post {
        always {
            script {
                echo 'This will always run, even if the build fails.'
            }
        }
        success {
            script {
                echo 'This runs only if the build succeeds.'
            }
        }
        failure {
            script {
                echo 'This runs only if the build fails.'
            }
        }
    }
}