# STS Assume Role
This repository contains a script for assuming a role in AWS.

### Features
- Exports temporary credentials into current session before running AWS CLI commands

### Pre-requsites
Software:

| Package | Download / Install Instructions |
| ------ | ------ |
| awscli | http://docs.aws.amazon.com/cli/latest/userguide/installing.html |
| jq | https://stedolan.github.io/jq/download/ |
| ansible | http://docs.ansible.com/ansible/latest/intro_installation.html |

Credentials:

Ensure you have the following in a credentials file in ~/.aws/credentials:

```bash
[iam]
aws_access_key_id = XXXXXXXXXXXXX
aws_secret_access_key = XXXXXXXXXXXXXXXXXXXXXXX
```

#### Accounts, Numbers and Roles:

Before running, you will need to add the information applicable to your AWS accounts. In the awstoken script replace the following:

1. aws_account_name with a name you define for each
2. aws_permitted_role with the role/s you will be assuming

Next, update the sts-config.json file as below:

1. Replace the accounts key with the associated account number value
2. Add the IAM account number

Once this sensitive information has been added, you may wish to encrypt the sts-config.json file using ansible vault. The setup script will then be able to decrypt the file, add your username to it and copy it to the correct location.

Operating System Recommendations:
  - Linux
  - macOS

### Version Dependencies
None.

### How to Use
To setup the sts credentials file run the following script:

```bash
./setup.sh
```

When prompted ensure you provide your IAM AWS account name. This is a one time task only needs to be run on on first use.

To generate temporary STS Assume Role credentials ensure you 'source' the script as below:

```sh
cd sts-assume-role/
source awstoken {acc1 | acc2 | acc3 | acc4 | acc5 | acc6}
```

### Build/Release Process
Branch off develop and raise a pull request before merging back to the develop branch. Only merge to the master branch from develop.

### Known Issues
No known issues.

### Author
Daniel Campailla
