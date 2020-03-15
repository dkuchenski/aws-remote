# AWS Remote
AWS Remote is a command line tool to view and interact with AWS instances via SSM

### Depends On:
- AWS CLI (https://docs.aws.amazon.com/cli/latest/userguide/install-macos.html)
- AWS CLI Session Manager Plugin (https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-working-with-install-plugin.html)

### What Can It Do?
aws-remote will list all your EC2 instances in the specified account/region, and display helpful information like state and SSM management status. aws-remote is also a wrapper for the AWS CLI that makes starting remote sessions and port-forwarding easier. Remote sessions and port-forwarding can be started using the EC2 Instance ID or the friendly name.

Examples:

```
$ aws-remote list
ID                      Name                             AZ            Type          State       SSM          
i-01234567890987654     instance1-example.domain.com     us-east-1a    r4.xlarge     running     true        
i-02345678909876543     instance2-example.domain.com     us-east-1b    t3.micro      running     false        
i-03456789098765432     instance3-example.domain.com     us-east-1c    t3.medium     running     true 

$ aws-remote --profile my_profile session i-02345678909876543

$ aws-remote --profile my_profile session instance2-example.domain.com

$ aws-remote --profile my_profile --region us-west-2 port-forward 8080 80 instance2-example.domain.com
```

### Installation Steps:
1. Verify Python3.6 or above is installed:
`python --version` or `python3 --version`

3. Verify AWS CLI is installed:
`aws --version `

4. Verify Session Manager plugin is installed:
`session-manager-plugin`

4. Clone repo and make aws-remote executable: `git clone https://github.com/dkuchenski/aws-remote.git && chmod +x aws-remote/aws-remote`

2. Install script packages:
`pip install -r aws-remote/requirements.txt`

5. Verify script works: 
`./aws-remote/aws-remote --help`

6. If desired, add alias to bash_profile and then restart terminal:
```
vi ~/.bash_profile
alias aws-remote='python3 ~/your-script-directory/aws-remote/aws-remote'
```
