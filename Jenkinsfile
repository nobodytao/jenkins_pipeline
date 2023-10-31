pipeline {
    agent any
    stages {
        stage('Username+Password Jenkins credentials + credentials() + sh') {
            environment {
                LOGIN = credentials('AnsibleCred')
            }
            steps {       
                sh 'ansible-playbook all_roles_small.yml -u "$LOGIN_USR" -e "ansible_ssh_pass=$LOGIN_PSW"'
            }
        }
	
	stage('Username+Password Jenkins credentials + withCredentials() + sh') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'AnsibleCred', passwordVariable: 'ANSPWD', usernameVariable: 'ANSUSER')]) {                  
                	sh 'ansible-playbook all_roles_small.yml -u "$ANSUSER" -e "ansible_ssh_pass=$ANSPWD"'
		}
            }
        }

	stage('Username+Password Jenkins credentials + credentials() + Ansible plugin') {
            environment {
                LOGIN = credentials('AnsibleCred')
            }
            steps {
		ansiblePlaybook(
                	inventory:'',
                	installation: 'ansible',
                	limit:'',
                	playbook:'all_roles_small.yml',
                	extras:'-u $LOGIN_USR',
                	extraVars:[ansible_ssh_pass: "$LOGIN_PSW"]
                	)
            }
        }

	stage('Secret_File Jenkins credentials + withCredentials() + Ansible plugin') {
            steps {
		withCredentials([file(credentialsId: 'ansible_ini', variable: 'ansible_ini')]) {
			ansiblePlaybook(
                		inventory:'$ansible_ini',
                		installation: 'ansible',
                		limit:'',
                		playbook:'all_roles_small.yml',
                		extras:'-v'
                		)
		}
            }
        }

	stage('Secret_File Jenkins credentials + withCredentials() + sh') {
            steps {
		withCredentials([file(credentialsId: 'ansible_ini', variable: 'ansible_ini')]) {
                	sh 'ansible-playbook all_roles_small.yml -i $ansible_ini'
		}
            }
        }  
    }
}