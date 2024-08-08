pipeline {
    agent any

    environment {
        TERRAFORM_DIR = '/home/devops_learning/employment_cert'
        ANSIBLE_DIR = '/home/devops_learning/employment_cert'
    }

    stages {
        stage('Provision Yandex Cloud Instances') {
            steps {
                script {
                    dir("${TERRAFORM_DIR}") {
                        sh 'terraform plan'
                        sh 'terraform apply -auto-approve'
                    }
                }
            }
        }

        stage('Deploy Application Using Ansible') {
            steps {
                script {
                    dir("${ANSIBLE_DIR}") {
                        sh "ansible-playbook deploy.yml --private-key /var/lib/jenkins/.ssh/id_ed25519"
                    }
                }
            }
        }
    }
}