# Teraform

```bash
A simple workflow for deployment adheres closely to the following steps:

Scope - Confirm what resources need to be created for a given project.
Author - Create the configuration file in HCL based on the scoped parameters.
Initialize - Run terraform init in the project directory with the configuration files. This downloads the correct provider plug-ins for the project.
Plan & Apply - Run terraform plan to verify creation process and then terraform apply to create real resources as well as the state file that compares future changes in your configuration files to what actually exists in your deployment environment.

Exemplo de arquivo (main.tf)
terraform {
  required_providers {
    google = {
      source = "hashicorp/google"
      version = "3.5.0"
    }
  }
}

provider "google" {

  project = "qwiklabs-gcp-00-3d6408e225a5"
  region  = "us-east1"
  zone    = "us-east1-b"
}

resource "google_compute_network" "vpc_network" {
  name = "terraform-network"
}



terraform init

terraform apply

terraform show


# É possível alterar o arquivo de configuração e aplicar as alterações novamente

resource "google_compute_instance" "vm_instance" {
  name         = "terraform-instance"
  machine_type = "e2-micro"

  boot_disk {
    initialize_params {
      image = "debian-cloud/debian-12"
    }
  }

  network_interface {
    network = google_compute_network.vpc_network.name
    access_config {
    }
  }
}

terraform apply

# Para destruir os componentes criados
terraform destroy

# Para visualizar as alterações que serão aplicadas
terraform plan
```
