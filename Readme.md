#Created Provider
provider "aws" {
  region     = "eu-central-1"
  access_key = "AKIA3ZJX67JAKOXCGCB2"
  secret_key = "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"
}

resource "aws_instance" "terraform" {
  ami          = "ami-0767046d1677be5a0"
  instance_type = "t2.micro"
  key_name = "sample"
  vpc_security_group_ids = [aws_security_group.main.id]
  }

resource "aws_security_group" "main" {
    egress = [
        {
    cidr_blocks      = ["0.0.0.0/0",]
    description      = ""
    from_port        = 0
    ipv6_cidr_blocks = []
    prefix_list_ids  = []
    protocol         = []
    protocol         = "-1"
    security_groups  = []
    self             = false
    to_port          = 0
   }
  ]
  ingress            = [
    {
    cidr_blocks      = ["0.0.0.0/0",]
    description      = ""
    from_port        = 22
    ipv6_cidr_blocks = []
    prefix_list_ids  = []
    protocol         = []
    protocol         = "tcp"
    security_groups  = []
    self             = false
    to_port          = 22
  }
  ]
}

resource "aws_key_pair" "deployer" {
    key_name = "sample"
    public_key = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC8PbziOuL8GxPhPwXeHJ6aawugHnCHSpWF4Yq5CHu+KFHHjgF4BLbAYRX3nRQrMP0fRsaEKk2vgl5Okh43M1shU8wjnka9JsLaESbnJYJKXCt8W6UEwJD9PwdA1XUJ1Isq/MV5W0h9KO1/xFv9C1OUpBfCUL2bh3ruPcY5ib9VjaKKjmnYfzC5G2j5HMeuN8MAqE2TJMGuhHDOaHYLaQoXz/ykFc0LqC6MW3f/AiraNnfeNBmhkOEBur3BuI3cRkrs54hh92moyvGfUyyAJ8cVTXMHNhVk1qRzs3sIkvdyWgajFO4NyU3m9YXEF1U7Wf8yWeUiKt21oxldC2QWo+Et corp\rashmith@lin83006692"
}

---------------------------------------
To Create PUBLIC_Key
sh-keygen -t rsa -b 2048

---------------------------------------
SSH Key:
ssh -i "sample.pem" ubuntu@ec2-3-75-184-56.eu-central-1.compute.amazonaws.com

----------------------------------------
Server ubuntu Command(Java and Python)
java --version
sudo apt update
sudo apt install java

sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.8
python --version
---------------------------------------
(Jenkins)
sudo apt-get update
sudo apt-get install openjdk-8-jdk

wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -

sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt-get update

--------------------------------------------



