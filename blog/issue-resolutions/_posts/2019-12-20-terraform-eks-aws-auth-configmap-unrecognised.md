---
layout: post
title:  "AWS_AUTH_CONFIGMAP Unrecognised When Creating EKS Cluster Using Terraform"
date:   2019-12-20 00:00:00 +0000   
categories: issue-resolutions
tags: issue-resolutions
teaser: This happened because of the way terraform was accessing aws credential profiles in my setup
---  

## Issue
Creating an EKS Cluster using terraform (v0.12) consistently failing with the following error
```
': exit status 1. Output: error: unable to recognize "aws_auth_configmap.yaml": Get https://8F2094C9F05CB7AD32816EFA57F5FD3D.sk1.eu-west-1.eks.amazonaws.com/api?timeout=32s: dial tcp 52.16.7.117:443: i/o timeout
error: unable to recognize "aws_auth_configmap.yaml": Unauthorized
```

## Resolution
This happens when a non-default aws credentials profile is used to run terraform code.
Example, my .aws/credentials file looked something like below
```
1 # default = aws account 1
2 [default]
3 aws_access_key_id = ...
4 aws_secret_access_key = ...
5
6 [beancrunch]
7 aws_access_key_id = ...
8 aws_secret_access_key = ...
```
My terraform code was configured to use the `beancrunch` profile which isn't the default.    
Solution was to explicitly call out the profile name in the EKS terraform code as below:
```hcl-terraform
module "eks-cluster" {
  source             = "terraform-aws-modules/eks/aws"
  cluster_name       = "${var.eks_cluster_name}"
  subnets            = concat(module.vpc.public_subnets, module.vpc.private_subnets)
  vpc_id             = "${module.vpc.vpc_id}"
  kubeconfig_aws_authenticator_env_variables = {
    AWS_PROFILE = "beancrunch"
  }
// More code here
}
```

![Webstorm debug configuration](/assets/blog/issue-resolutions/nodejs-debugger-error-babel-fix.png)




