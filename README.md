# k8s-cluster-ansible-aw
k8s cluster deployed on aws ec2 instances with ansible
```
ansible-playbook -i hosts ec2.yml 
ansible-playbook -i dynamic_hosts/aws_ec2.yml kubernetes.yml
```
