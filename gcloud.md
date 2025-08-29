# Google Cloud Shell commands

```

gcloud storage buckets create gs://[BUCKET_NAME] --location=us-central1

gcloud compute zones list | grep $MY_REGION

gcloud config set compute/zone $MY_ZONE

gcloud compute instances create $MY_VMNAME \
--machine-type "e2-standard-2" \
--image-project "debian-cloud" \
--image-family "debian-11" \
--subnet "default"

gcloud compute instances list

gcloud iam service-accounts create test-service-account2 --display-name "test-service-account2"

gcloud projects add-iam-policy-binding $GOOGLE_CLOUD_PROJECT --member serviceAccount:test-service-account2@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com --role roles/viewer



# APP Deploy

# Criar o arquivo app.yaml com as configurações do app

# Criar um novo app
gcloud app create --region=us-west1

# Fazer o deploy
gcloud app deploy --version=one --quiet

# Segunda versão não publicada (no-promote)
gcloud app deploy --version=two --no-promote --quiet


# GKE - Criar repositório de imagens docker
gcloud artifacts repositories create devops-demo \
    --repository-format=docker \
    --location=us-west1 

gcloud auth configure-docker us-west1-docker.pkg.dev

cd ~/gcp-course/deploying-apps-to-gcp
gcloud builds submit --tag us-west1-docker.pkg.dev/$DEVSHELL_PROJECT_ID/devops-demo/devops-image:v0.2 .

```
