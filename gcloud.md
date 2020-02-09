#### Install gcloud (ubuntu | wsl on windows)

```bash
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" `
| sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list

sudo apt-get install apt-transport-https ca-certificates gnupg

curl https://packages.cloud.google.com/apt/doc/apt-key.gpg `
| sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -

sudo apt-get update && sudo apt-get install google-cloud-sdk
```

#### Login and Verify

```bash
# Login (a URL will be given to grab the oAuth token from a browser)
gcloud auth login

# Set the project with project ID i.e. letsplay-265908
gcloud config set project letsplay-265908

# Get the current config
gcloud config list
```

#### Interactive shell Beta ( tab completion and intellisense)

```bash
gcloud beta interactive
```

#### Create VPC and subnet

```bash
gcloud compute networks create viki-demo-net --subnet-mode custom --bgp-routing-mode global

gcloud compute networks subnets create frontend-sn --network viki-demo-net --range 10.10.1.0/24
```

#### Verify

```bash
gcloud compute networks list

gcloud compute networks subnets list

```

#### Create Instance attached to the network created

```bash
gcloud compute instances create vm-ubuntu18-02 \
  --image-family ubuntu-minimal-1804-lts \
  --image-project ubuntu-os-cloud \
  --network viki-demo-net \
  --subnet frontend-sn \
  --zone=us-central1-a
```
