# docs
For test how to share docs 
##This is test page##
__**OPA**__


# AWS Terraform vault with MFA 
```
wget https://github.com/99designs/aws-vault/archive/v4.2.1.tar.gz
aws-vault add epam
aws-vault list
aws-vault exec knab -- env | grep AWS | grep -v 'AWS_VAULT'
aws sts get-session-token --serial-number arn:aws:iam::<ID>:mfa/<user> --token-code <TOCKEN> --profile <PROFILENAME>
aws iam list-access-keys --user-name stefanov --profile personal
terraform  plan -out personal
terraform apply "personal"
```
AWS CLI config
aws configure
```
[astor@ECSB00100A08 .aws]$ cat config
[default]
output=json
region=eu-west-1
mfa_serial=arn:aws:iam::id:mfa/usr

[profile opa]
output=json
region=eu-west-1
mfa_serial=arn:aws:iam::<id>:mfa/<user>

[profile plamen]

[profile personal]

[astor@ECSB00100A08 .aws]$ cat credentials
[default]
aws_access_key_id = AFSAFKNAHSFQRRQW
aws_secret_access_key = wOASGGSIGNJIWEQGQL
```


AWS check
```
AWS  CLI - No there is no way to set multiple regions in one setting. You could do something like this

for region in `aws ec2 describe-regions --output text | cut -f3`
do
     echo -e "\nListing Instances in region:'$region'..."
     aws ec2 describe-instances --region $region
done
```

AWS CLI install
```
pip install awscli --upgrade --user
```
