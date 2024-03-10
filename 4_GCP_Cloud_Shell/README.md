# Cloud Shell

- Google Cloud Shell is an interactive terminal to interact with Google Cloud.
- Cloud Shell is Browser Based Terminal.
- Cloud SDK, gcloud CLI and other Utilities are pre-installed in Google Cloud Shell.
- Cloud Shell comes with inbuilt Code Editor.
- It is fully Browser Based Application. No local installation is required to use Google Cloud Shell.
- Cloud Shell has 5GB Persistent Disk attached. The VM it runs on is ephemeral and terminates 20 mins after our session ends.
- Easy Access to pre-install tools such as bq, vim, python etc.
- Write **`gcloud config set project (id-of-your-project)`** to set your project in cloud shell

## Cloud SDK Commands
1. List all the instances
```sh
gcloud compute instances list
```
2. Start a terminated instance
```sh
gcloud compute instances start instance-20240308-045108 --zone=us-central1-a
```
3. List out instances in a particular zone
```sh
gcloud compute instances list --zones=us-central1-a
```
