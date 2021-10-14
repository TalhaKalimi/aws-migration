# aws-migration

first step:
make  OVA file of your local vm

second step:
uplod this file on your aws s3 buket

third step:
configer aws cli on your base OS also make IAM user and group with full access rolls

fourth step:
go to aws documanttation and search for vm import/export option
and then go to recuirement and copy trustrolls.json also copy policy rolls.json and finally copy the container.json file.

fifth step:
change path of your all files in your system

sisxth step
open a aws cli and run the following command according to your path 
aws iam create-role --role-name vmimport --assume-role-policy-document "file://C:/Users/admin/Desktop/migration/trust-policy.json"

aws iam put-role-policy --role-name vmimport --policy-name vmimport --policy-document "file://C:/Users/admin/Desktop/migration/role-policy.json"

aws ec2 import-image --description "CentOS 7 64-bit" --disk-containers "file://C:/Users/admin/Desktop/migration/containers.json"

aws ec2 describe-import-image-tasks --import-task-ids import-ami-0d66563c78952be9b

seven step:
check on your aws consol AMI option   

hurray your local vm is migreted to your aws console
