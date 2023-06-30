pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Pooja-graafika/CI-CD-Project.git'
            }
        }
        
        stage('Execute SSH command') {
            steps {
                script {
                    sshagent(credentials: ['8e295089-1193-4339-b920-63cabbd2c0f8']) {
                        sh 'ssh -i /root/.ssh/id_rsa2 root@3.110.101.233 "<COMMAND>"'
                    }
                }
            }
        }

        stage('Run Ansible playbook') {
            environment {
                ANSIBLE_HOST_KEY_CHECKING = "False"
            }
            steps {
                sh 'ansible-playbook -i inventory.ini terraform.yml'
            }
        }
    }
}
