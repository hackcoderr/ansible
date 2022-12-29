## Adhoc Command

Where

-m = Module name

-a = allow parameters

-u = usernam

```
ansible hostname -m <module> -a "name=<packagename> state=<state>"
# e.g: ansible 127.0.0.1 - yum -a "name=httpd state="present"
```
[for more information](https://www.devopsschool.com/tutorial/ansible/ansible-linux-adhoc-commands.html)
