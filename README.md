Kubernetes cluster are deployed on AWS EC2 instances with Ansible
-
There are three roles:
- **ec-2** creates SecurityGroup and EC2 instances with tags Name: Worker and Name: Master
- **master** installs on instance(s) with tag "Name: Master" containerd, Kubernetes cluster package and Flanell
- **workers** installs on instance(s) with tag "Name: Worker" containerd, Kubernetescluster package and join worker with master.

To create cluster:
-
1. Create pair of keys with name "k8s" in AWS KMS.
2. In file "ansible.cfg" add path to private key "k8s.pem"
3. Create ec2 instances:
```
ansible-playbook -i hosts ec2.yml 
```
4. Get information about instances
```
ansible-inventory -i dynamic_hosts/aws_ec2.yml --list
```
5. Install Kubernetes cluster
```
ansible-playbook -i dynamic_hosts/aws_ec2.yml kubernetes.yml
```
