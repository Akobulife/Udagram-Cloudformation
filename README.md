Project 2 submission for Godson Akobundu
========================================

****CORRECTIONS******

1) I have rewritten the launch configuration to include t3 (medium) instance type.

2) The output of the stack or the Load Balancer DNS Name is:

http://Udagr-Udagr-WZHSZ7TU2J7O-1811282767.us-east-1.elb.amazonaws.com
 

CONTENTS:
========

1) project2.yml: This is the YAML file for the Udagram Application

2) project2-param.json: This is the parameters (JSON) file for the Udagram Application

3) Udagram Diagram.PNG: This is the LucidChart diagram for the Udagram AWS stack

4) Snapshots Folder: This Folder contains snapshots of the Udagram Built stack on AWS Cloudformation including; the stack
page, Outputs Page, Resources Page.


TO CREATE UDAGRAM STACK:
=======================

$aws cloudformation create-stack --stack-name Udagram --template-body file://project2.yml  --parameters file://project2-param.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1

**NB: Please the files should be on the same folder and the CLI Program run from the same folder.**


TO DELETE UDAGRAM STACK:
=======================

$aws cloudformation delete-stack --stack-name Udagram --region us-east-1


EXTRA INFORMATION:
==================

1) "http://" was attached to the DNS name of the Udagram Load Balancer.

2) A Bastion Host was deployed in PublicSubnet1 and have the following attached to it:

a) RoleForSSMAccess: Which is a role attached to the Bastion instance profile that allows for AWS Session Managers access.
This eliminated the need for Key based login into the instance and thus a security boost.

3) CloudWatch metrics was integrated into the Udagram AutoScaling Group and the following metrics are being monitored:

a) GroupMinSize
b) GroupMaxSize
c) GroupInServiceInstances
d) GroupTotalInstances