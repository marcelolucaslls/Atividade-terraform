provider "aws" {
  region = var.aws_region
  access_key = "AKI........"
  secret_key = "ZV......"
}
resource "aws_key_pair" "ssh" {
  key_name   = "ssh_key"
  public_key = file("~/.ssh/id_rsa.pub")
}
resource "aws_instance" "web" {
  ami           = var.ami
  instance_type = var.instance_type
  key_name      = aws_key_pair.ssh.key_name
  tags = {
    Name = "Terraform-Web-Instance"
  }
}
terraform {
  backend "s3" {
    bucket = "bucket-da-atividade"
    key    = "terraform.tfstate"
    region = "us-east-2"
    access_key = "....."
    secret_key = "ZV...."
  }
}
