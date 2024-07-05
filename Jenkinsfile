pipeline {
    agent any

    environment {
        ENV = ""
    }

    stages {

        stage('Setting Up') {
            steps {                
                dir(env.TERRAFORM_DIRECTORY) {
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
                                errorBanner("Aborting the build, branch not configured.")
                                break
                            }
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
}
