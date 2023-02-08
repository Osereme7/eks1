# eks1
Terraform code to spin up an eks cluster 
provider "aws" {
  region = "us-west-2"
}

module "eks" {
  source = "terraform-aws-modules/eks/aws"

  cluster_name = "my-eks-cluster"
  subnets = [
    "subnet-0123456789abcdef0",
    "subnet-0123456789abcdef1",
    "subnet-0123456789abcdef2"
  ]

  vpc_id = "vpc-0123456789abcdef0"

  tags = {
    Terraform   = "true"
    Environment = "dev"
  }

  enable_alg_port_rules = true

  managed_node_group_count = 2
  managed_node_group_name   = "my-eks-node-group"

  tags = {
    Terraform   = "true"
    Environment = "dev"
  }
}
