# google-cloud-learning


Manually create VM SSH keys:
```
ssh-keygen -t rsa -f filepath -C username (choose one) -b 2048
```

To add it to a VM,
```
gcloud compute instances add-metadata VM_NAME --metadata-from-file ssh-keys=KEY_FILE
```
