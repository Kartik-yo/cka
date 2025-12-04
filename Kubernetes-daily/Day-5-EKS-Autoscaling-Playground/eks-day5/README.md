# Day 5 – EKS Autoscaling Playground

Fully working EKS cluster with:
- Custom VPC + bastion
- Managed nodegroup (t3.medium × 2)
- Working HPA (php-apache)
- Cluster Autoscaler with IRSA (fixed!)
- Test workload to trigger node scale-out

To recreate:
1. Deploy VPC + bastion (your CFN)
2. eksctl create cluster --name eks-learning --without-nodegroup
3. eksctl create nodegroup -f nodegroup.yaml
4. Apply hpa-demo/
5. Apply cluster-autoscaler/serviceaccount.yaml + deployment.yaml
6. Run ca-test.yaml → watch nodes scale!
