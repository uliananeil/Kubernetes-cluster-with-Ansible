# k8s-cluster-ansible-aws
k8s cluster deployed on aws ec2 instances with ansible

1. Create in AWS key-pair with name "k8s"
2. In file "ansible.cfg" add path to private key "k8s.pem"
3. Create ec2 instances:
```
ansible-playbook -i hosts ec2.yml 
```
4. get information about instances
```
ansible-inventory -i dynamic_hosts/aws_ec2.yml --list
```
5. create cluster
```
ansible-playbook -i dynamic_hosts/aws_ec2.yml kubernetes.yml
```

Roles:

ec-2 - create security group, one instance for master node and two for worker nodes

master - create master node

workers - create worker nodes

dynamic_hosts/aws_ec2.yml - group instances by tag "tag_Name_master" and "tag_Name_worker"
