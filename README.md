### Scope

- monitor private git project
  - commit hook
  - PR hook
- [x] auto build and run test
- notification accordingly
- auto deploy on staging when it works
- [x] real setup on aws

- test target: https://github.com/hi-ogawa/rails_jwt_zero_downtime
- VM specific trouble:
  - http://stackoverflow.com/questions/28174437/spring-permission-error-ubuntu-14-04

### Setup

- install jenkins via ansible script
- security setup
  - create user from jenkins interface
- project setup
  - setup deploy key on github and register on jenkins


### Plugins

- github: https://wiki.jenkins-ci.org/display/JENKINS/GitHub+Plugin
- slack: https://wiki.jenkins-ci.org/display/JENKINS/Slack+Plugin

### Commands

```
# launch vm
$ vagrant up

# check if ansible can access to vm
$ ANSIBLE_HOST_KEY_CHECKING=False ansible -i ./ansible/hosts vagrant -u ubuntu -m ping

# run ansible script (verbosely)
$ ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -v -i ./ansible/hosts ./ansible/vagrant.yml

# get real on aws
$ ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -v -i ./ansible/hosts ./ansible/aws.yml

# in vm
$ cat /etc/default/jenkins
```

### References

- https://wiki.jenkins-ci.org/display/JENKINS/Use+Jenkins
- https://wiki.jenkins-ci.org/display/JENKINS/Installing+Jenkins+on+Ubuntu
- https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get

- ansible techniques:
  - http://docs.ansible.com/ansible/playbooks_error_handling.html
  - http://docs.ansible.com/ansible/shell_module.html
  - http://docs.ansible.com/ansible/playbooks_conditionals.html#register-variables
  - http://docs.ansible.com/ansible/faq.html#how-can-i-set-the-path-or-any-other-environment-variable-for-a-task-or-entire-playbook

- jenkins on tcp 80:
  - https://wiki.jenkins-ci.org/display/JENKINS/Installing+Jenkins+on+Ubuntu#InstallingJenkinsonUbuntu-SettingupanNginxProxyforport80%5C%3E8080
  - https://wiki.jenkins-ci.org/display/JENKINS/Running+Jenkins+on+Port+80+or+443+using+iptables
