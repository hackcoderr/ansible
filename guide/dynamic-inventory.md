### How to configure dynamic Inventory
#
 * Step-1: Make a folder which will contains all the informations of inventory.
 ```
 mkdir hosts
 ```
 * Step-2: Go inside **/etc/ansible/ansible.cfg** directory and set the path of your inventory folder which you made earlier.
 
 ```
 [defaults]
 inventory=/hosts
 ```
 * Step-3: After saving inventoty path, download precreted python [ec2.py](https://github.com/ansible/ansible/blob/stable-2.9/contrib/inventory/ec2.py) and [ec2.ini](https://github.com/ansible/ansible/blob/stable-2.9/contrib/inventory/ec2.ini) files. So follow the  below syntex to download them.
 ```
 wget https://github.com/ansible/ansible/blob/stable-2.9/contrib/inventory/ec2.py
 
 wget https://github.com/ansible/ansible/blob/stable-2.9/contrib/inventory/ec2.ini
```

* Step-4: Convert both files into executable mode.
```
chmod +x ec2.py

chmod +x ec2.init
```
* Step-5: Open your **ec2.py** with help of any editor like *vim* and *vi* and comment **from ansible.module_utils import ec2 as ec2_utils** line which is existing at **172** in your **ec2.yml** file.
```
from ansible.module_utils import six
#from ansible.module_utils import ec2 as ec2_utils
from ansible.module_utils.six.moves import configparser

```
**Note**: If your controller node has **Python3** then replace the location of **shebang**(#!) from **#!/usr/bin/env python** to **#!/usr/bin/python3**.eg:
```
#!/usr/bin/python3

'''
EC2 external inventory script
=================================
Generates inventory that Ansible can understand by making API request to
AWS EC2 using the Boto library.

```
* Step-6: Now open **ec2.ini** file and give your access and secret key which will mentioned at the bottom of **ec2.ini** file.
```
[credentials]

# The AWS credentials can optionally be specified here. Credentials specified
# here are ignored if the environment variable AWS_ACCESS_KEY_ID or
# AWS_PROFILE is set, or if the boto_profile property above is set.
#
# Supplying AWS credentials here is not recommended, as it introduces
# non-trivial security concerns. When going down this route, please make sure
# to set access permissions for this file correctly, e.g. handle it the same
# way as you would a private SSH key.
#
# Unlike the boto and AWS configure files, this section does not support
# profiles.
#
aws_access_key_id = AXXXXXXXXXXXXXX
aws_secret_access_key = XXXXXXXXXXXXXXXXXXX
```

* Step-7: Install **boto and boto3** python library.

**Note**: Python should be installed to to download and install python libraries.

* *If your controller node has python 1 or 2 version then use.*
```
sudo pip install boto

sudo pip install boto3
```
 * *Or your controller node has python 3 then use.*
 ```
 sudo pip3 install boto
 
 sudo pip3 install boto3
 ```
 * Now your dynamic inventory configuration is done.If your AWS Account has any launched instance the check with below command.
 ```
[root@controller_node~]$ ansible all --list-hosts
[WARNING]: Invalid characters were found in group names but not replaced, use -vvvv to see details
  hosts (1):
    15.206.148.130
```
* if you want to ping your instance or run the playbook on your instance then give the **tagname** of your instance. eg:
```
[root@controller_node ~]$ ansible tag_Name_testing_os -m ping
[WARNING]: Invalid characters were found in group names but not replaced, use
-vvvv to see details
13.233.92.62 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "ping": "pong"
}
```
 #
 **<𝚌𝚘𝚍𝚎𝚛𝚜/>! <img src="https://github.com/TheDudeThatCode/TheDudeThatCode/blob/master/Assets/Hi.gif" width="29px">, If this repo is useful to you then you can follow me on Github and visit my Github profile**

 [![GitHub followers](https://img.shields.io/github/followers/hackcoderr?label=Follow&style=social)](https://github.com/hackcoderr/?tab=follow)


 
 
 
 
 
 
