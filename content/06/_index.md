---
title: "Terraform Destroy"
weight: 6
---

This section will walk you through three processes:
* Removing all the route table changes we made in Task 7. We must remove these route table changes before we can destroy the VPC, because the route table changes create dependencies within the VPC. Terraform cannot destroy the VPC until these dependencies are removed.
* Use Terraform to destroy all the resources we created when we deployed the autoscale group.
* Use Terraform to destroy all the resources we created when we deployed the distributed ingress workload VPC from AWS Cloudshell.
