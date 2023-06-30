pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout(
                    scmGit([
                        branches: [[name: '*/main']],
                        userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/Pooja-graafika/ansible.git']]
                    ])
                )
            }
        }
        
         stage('Execute SSH command') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: '8e295089-1193-4339-b920-63cabbd2c0f8', keyFileVariable: 'SSH_KEY')]) {
                    sh 'ssh -i $SSH_KEY root@3.110.101.233'
                }
            }
        }
         

      //  stage('Run Ansible playbook') {
       //     environment {
         //       ANSIBLE_HOST_KEY_CHECKING = "False"
           // }
            //steps {
              //  sh 'ansible-playbook -i inventory.ini terraform.yml'
            //}
        //}
    }
}
