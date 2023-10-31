<b>Project Overview: Running Ansible Playbooks in Multi-Pipeline Jenkins with GitHub Integration</b>
<br><br>
This project showcases the capability of running an Ansible playbook with roles in a Jenkins project that supports multiple pipelines while seamlessly connecting with GitHub. The objective is to interact with Linux Debian-based workstations and execute a series of commands listed in the file <b>/debian_workstations_small/tasks/main.yml</b>.
<br><br>
<b>Jenkinsfile Features:</b><br>
The Jenkinsfile in this project offers 5 different methods for utilizing Jenkins credentials in the ansible-playbook:
<br><br>
<b>Method 1</b>: User credentials (username and password) from Jenkins credentials, using the credentials() function along with "sh 'ansible-playbook ...'".
<br><br>
<b>Method 2</b>: User credentials from Jenkins credentials, using withCredentials() along with "sh 'ansible-playbook ...'".
<br><br>
<b>Method 3</b>: User credentials from Jenkins credentials, employing the Ansible plugin within Jenkins.
<br><br>
<b>Method 4</b>: Using a secret file from Jenkins credentials in conjunction with withCredentials() and the Ansible plugin. The secret file contains the 'myhosts.ini' file, including the username and password.
<br><br>
<b>Method 5</b>: Utilizing a secret file from Jenkins credentials along with withCredentials() and "sh 'ansible-playbook ...'".
<br><br>
<b>Preparation Steps:</b><br>
Before you begin, ensure you've set up two specific Jenkins credentials:
<br><br>
<b>Username with Password:</b> Create an environment variable with the ID "AnsibleCred." This will store the username and password required for the ansible playbook.
<br><br>
<b>Secret File:</b> Create another environment variable with the ID "ansible_ini." This variable will hold the 'myhosts.ini' file, which is essential for the ansible playbook to operate smoothly.
