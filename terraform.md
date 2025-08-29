```bash
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
