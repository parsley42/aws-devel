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