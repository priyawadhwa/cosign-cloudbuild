# cosign-cloudbuild

This project is an example of building an image in GCP Cloud Build, pushing it, and then signing it via cosign/GCP KMS.

This should run successfully provided: 

1. Cloud Build service account has these IAM permissions:
- Cloud KMS CryptoKey Signer
- Cloud KMS CryptoKey Public Key Viewer
2. An asymmetric key has been created in GCP KMS for signing

