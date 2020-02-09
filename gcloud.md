### Login

```bash
gcloud auth login
gcloud account list
```

### Create VPC and subnet

```bash
gcloud compute networks create viki-demo-net --subnet-mode custom --bgp-routing-mode global

gcloud compute networks subnets create frontend-sn --network viki-demo-net --range 10.10.1.0/24
```

```bash
gcloud compute networks list

gcloud compute networks subnets list

```

```bash
gcloud compute instances create vm-ubuntu18-02 \
  --image-family ubuntu-minimal-1804-lts \
  --image-project ubuntu-os-cloud \
  --network viki-demo-net \
  --subnet frontend-sn \
  --zone=us-central1-a
```
