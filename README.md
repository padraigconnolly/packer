# Packer Proxmox Template

Packer Template for Proxmox based off tutorial from https://www.youtube.com/c/TheDigitalLifeTech

More details on the setup and Packer in general can be found in this video: https://www.youtube.com/watch?v=1nf3WOEFq1Y&t=1257s

### Quick Start Guide

#### Install Packer

Add Hashicorp private repo:
```bash
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update && sudo apt-get install packer
```

#### Add Credentials

Edit `credentials.pkr.hcl` to match your Proxmox instance

#### Run Packer

First validate your packer files:
```bash
packer validate --var-file='../credentials.pkr.hcl' ./ubuntu-server-jammy.pkr.hcl
```

If all is `OK` then proceed to run the packer installation:
```bash
packer build --var-file='../credentials.pkr.hcl' ./ubuntu-server-jammy.pkr.hcl
```

Packer should then proceed to build the Ubuntu 22.04 template on your Proxmox Instance
