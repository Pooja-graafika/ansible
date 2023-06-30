pipeline {
    agent any

    stages {
         stage('Git Checkout'){
                when{expression{params.action == "create"}}    
            steps{
            gitCheckout(
                branch: "main",
                url: "https://github.com/Pooja-graafika/ansible.git"
            )
            }
        }
        
        stage('Execute SSH command') {
            steps {
                
                // sh 'ssh <SSH_OPTIONS> <SSH_USER>@<SSH_HOST> "<COMMAND>"'
                 sh  'ssh -i /root/.ssh/id_rsa2 root@3.110.101.233'
            }
        }

       // stage('Install Ansible') {
           // steps {
              //  sh 'apt install ansible'
          //  }
      //  }

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
