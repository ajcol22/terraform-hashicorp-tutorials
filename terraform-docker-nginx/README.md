# Deploy NGINX Server in a Docker Container using Terraform

### Pre-requisites
- Terraform
- Docker
  
### Steps
1. Open Terminal
2. Start Docker Desktop
   `open -a Docker`
4. Create a directory for your project and navigate to it.
5. Create a file in the directory called main.tf and paste the following code into it:
```
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.1"
    }
  }
}
 
provider "docker" {}
 
resource "docker_image" "nginx" {
  name         = "nginx"
  keep_locally = false
}
 
resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "tutorial"
 
  ports {
    internal = 80
    external = 8000
  }
}
```

### Referenced >
https://developer.hashicorp.com/terraform/tutorials/azure-get-started/install-cli
