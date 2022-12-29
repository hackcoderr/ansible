## Adhoc Command

Where

-m = Module name

-a = allow parameters

-u = usernam

```
ansible hostname -m <module> -a "name=<packagename> state=<state>"
# e.g: ansible 127.0.0.1 - yum -a "name=httpd state="present"
```
for more information
1. [Ansible Adhoc Commands in Linux](https://www.devopsschool.com/tutorial/ansible/ansible-linux-adhoc-commands.html)
2. [Ansible Ad Hoc Commands Cheat Sheet](https://www.decodingdevops.com/ansible-ad-hoc-commands-cheat-sheet/#:~:text=or%20inventory%20file.-,Ansible%20ad%20hoc%20command%20to%20install%20any%20package,module%20to%20install%20any%20packages.&text=Here%20it%20will%20install%20httpd%20in%20all%20host%20systems.&text=It%20will%20install%20httpd%20in%20all%20host%20systems.,-Ansible%20adhoc%20commands)
