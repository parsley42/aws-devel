This repository contains configuration and data for creating developer workstations in AWS using Cloud9.

Requirements:
* aws-linuxjedi - repository used for configuring the VPC and other CloudFormation resources
* linuxjed-private - repository with non-public variable definitions
* Base AMIs built with linuxjedi-amis
* Base AMI IDs stored in SSM Parameter Store:
  * /ami/amzn2base
  * /ami/f28base
  * /ami/u16base
* A permissive .ssh/config that doesn't sweat changing host keys, e.g.:
```
CanonicalizeHostname yes
CanonicalDomains linuxjedi.org
Host *.linuxjedi.org
        StrictHostKeyChecking false
        UserKnownHostsFile /dev/null
        CheckHostIP false
```

## Creating a Cloud9 Developer Workstation Manually

1. Create the instance from one of the templates; the instance name need not match the template name:
```bash
$ ec2 create -w f28devel c9-native f28devel
```
2. Run the `c9devel` playbook:
```bash
$ ansible-playbook c9devel.yaml -e target=f28devel
```