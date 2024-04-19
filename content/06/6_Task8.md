---
title: "Task 8: Cleanup"
weight: 1
---

* Start by removing all routes in the Workload VPC that point to the autoscale endpoints that we created in Task5. The Terraform destroy will fail if you try to remove the endpoints with existing routes pointing to the endpoints. 
* Log into your AWS account and navigate to the [**Console Home**](https://us-west-2.console.aws.amazon.com/console/home?region=us-west-2#).
* Click on the VPC icon

![](image-t8-1.png)

* Click on "Route tables" in the left pane

![](image-t8-2.png)

* Highlight the IGW Ingress Route table named "cnf-dist-rec-igw-rt". 
* Click on the "Routes" tab at the bottom. 
* Click on "Edit routes".

![](image-t8-3.png)

* Remove the four routes that have a "Target" that points to a "vpce"
* Click "Save Changes"

![](image-t8-4.png)
![](image-t8-5.png)

* Highlight the private route table for AZ1.
* Click the "Routes" tab at the bottom
* Click "Edit routes"

![](image-t8-6.png)

* Change the default route target to the IGW in the VPC.
* Click "Save changes"

![](image-t8-7.png)
![](image-t8-8.png)

* Navigate back to the "Route tables" screen and change the default route for the private subnet in AZ2. 
* Click the "Routes" tab at the bottom
* Click "Edit routes"
* Change the default route target to the IGW in the VPC.
* Click "Save changes"

![](image-t8-9.png)
![](image-t8-10.png)
![](image-t8-11.png)

* Cleanup the terraform autoscale deployment. 
** ssh into the ec2 linux instance in AZ1

    ``` ssh -i <keypair> ubuntu@<public ip> ```

** cd to the deployment directory

    ``` cd terraform-aws-cloud-modules/examples/spk_gwlb_asg_fgt_gwlb_igw/ ```

** destroy the autoscale group using terraform destroy. (20-25 minutes)
** Wait for "destroy complete"

    ``` terraform destroy --auto-approve ```

![](image-t8-12.png)

* Now lets destroy the distributed egress workload vpc we created from AWS Cloudshell
* Log into your AWS account and navigate to the [**Console Home**](https://us-west-2.console.aws.amazon.com/console/home?region=us-west-2#).
* Click on the "AWS Cloudshell" icon
* cd tec-recipe-distributed-ingress-nlb/
* terraform destroy --auto-approve

![](image-t8-13.png)
![](image-t8-14.png)

* Wait for "destroy complete"

![](image-t8-15.png)

* This concludes this section and the workshop is complete.
