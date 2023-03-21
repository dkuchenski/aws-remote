# AWS Remote
AWS Remote is a command line tool to view and interact with AWS instances via SSM

### Depends On:
- AWS CLI (https://docs.aws.amazon.com/cli/latest/userguide/install-macos.html)
- AWS CLI Session Manager Plugin (https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-working-with-install-plugin.html)

### What Can It Do?
aws-remote will list all your EC2 instances in the specified account/region, and display helpful information like state and SSM management status. aws-remote is also a wrapper for the AWS CLI that makes starting remote sessions and port-forwarding easier. Remote sessions and port-forwarding can be started using the EC2 Instance ID or the friendly name or Private IP address.

Examples:

```
$ aws-remote --help
Usage: aws-remote [OPTIONS] COMMAND [ARGS]...

  AWS Remote is a simple, command line tool to view and interact with AWS
  instances via SSM. Requires the AWS CLI and Session Manager Plugin to be
  installed locally.

Options:
  --profile TEXT  Specify AWS profile
  --region TEXT   Specify AWS region
  --help          Show this message and exit.

Commands:
  list          List EC2 instances and SSM management status
  port-forward  Start SSM port forward to instance id/name/private ip
  session       Start SSM session with instance id/name/private ip

$ aws-remote list
ID                     AZ            Type         State      SSM     IP                Name      
i-01234567890987654    us-east-1a    r4.xlarge    running    true    192.168.1.1       instance1-example.domain.com
i-02345678909876543    us-east-1b    t3.micro     running    false   192.168.1.2       instance2-example.domain.com       
i-03456789098765432    us-east-1c    t3.medium    running    true    192.168.1.3       instance3-example.domain.com

$ aws-remote --profile my_profile session i-02345678909876543

$ aws-remote --profile my_profile session instance2-example.domain.com

$ aws-remote --profile my_profile session 192.168.1.2

$ aws-remote --profile my_profile --region us-west-2 port-forward 8080 80 instance2-example.domain.com
```

### Installation Steps:
1. Verify Python3.6 or later is installed:
`python --version` or `python3 --version`

3. Verify AWS CLI version 1.16.12 or later is installed:
`aws --version `

4. Verify Session Manager plugin is installed:
`session-manager-plugin`

4. Clone repo to your computer: `git clone https://github.com/dkuchenski/aws-remote.git`

2. Install script packages:
`pip install -r aws-remote/requirements.txt`

5. Verify script works: 
`python3 aws-remote/aws-remote --help`

6. If desired, add alias to bash_profile and then restart terminal:
```
vi ~/.bash_profile
alias aws-remote='python3 ~/your-script-directory/aws-remote/aws-remote'
```
