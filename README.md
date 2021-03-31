# cosign-cloudbuild

This project is an example of building an image in GCP Cloud Build, pushing it, and then signing it via cosign/GCP KMS.

This should run successfully provided: 

1. Cloud Build service account has these IAM permissions:
- Cloud KMS CryptoKey Signer
- Cloud KMS CryptoKey Public Key Viewer
2. An asymmetric key `cosign` has been created, along with a key ring called `cosign`, in GCP KMS for signing

The image can be verified via:

```
cosign public-key -kms gcpkms://projects/$PROJECT_ID/locations/global/keyRings/cosign/cryptoKeys/cosign > cosign.pub
cosign verify -key cosign.pub gcr.io/$PROJECT_ID/cosign-cloudbuild

```