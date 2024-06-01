Ansible Playbook Explanation

---: This marks the beginning of the YAML file, indicating the start of the playbook.
- name: Provision and setup Jenkins on EC2: This defines a play with a descriptive name to set up Jenkins on an EC2 instance.
hosts: all: This specifies that the play will run on all hosts defined in the inventory.
remote_user: ubuntu: This sets the remote user to ubuntu for SSH connections to the EC2 instances.
become: yes: This ensures that the tasks will be executed with elevated privileges (i.e., using sudo).
- hosts: all: This defines another play that will run on all hosts specified in the inventory.
roles:: This indicates that roles will be used to organize and run multiple tasks.
- role: geerlingguy.java: This uses the geerlingguy.java role from Ansible Galaxy to handle the installation of Java.
vars:: This section defines variables for the role.
java_packages:: This specifies the Java packages to be installed.
- openjdk-11-jdk: This indicates that the openjdk-11-jdk package will be installed.
become: yes: This ensures that the tasks within the geerlingguy.java role will be executed with elevated privileges.
- role: geerlingguy.jenkins: This uses the geerlingguy.jenkins role from Ansible Galaxy to handle the installation and configuration of Jenkins.
become: yes: This ensures that the tasks within the geerlingguy.jenkins role will be executed with elevated privileges.
Summary
This playbook is designed to automate the provisioning and setup of Jenkins on EC2 instances. It uses roles from Ansible Galaxy to install Java and Jenkins, ensuring all tasks are performed with the necessary privileges for successful installation and configuration.


How to run:
1. copy your key-pair file to replace existing .pem in the project root directory
2. replace the ip's in the inventory.ini file with your ec2 public ips
3. your terminal, switch to the project directory and run "ansible-playbook lamp-setup.yaml" 
