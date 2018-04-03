pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
                sh 'rm -rf test5'
                sh 'git clone https://github.com/awesomemayank007/test5.git'
				sh 'cp -rvf test5/* /ansible_playbook/'
            }
        }
		stage('TEST') {
			agent {
				docker { image 'docker.io/ansible/centos7-ansible'
				args '-v "/ansible_playbook":"/ansible_playbook"' }
				}
			steps {
			    sh 'cd ~;pwd;yum install sshpass -y'
			    sh 'cp -rvf /ansible_playbook/ansible.cfg /etc/ansible/'
			    sh 'ansible-playbook -i /ansible_playbook/hosts /ansible_playbook/nginx-install.yml'
            }
        }
	}
}
