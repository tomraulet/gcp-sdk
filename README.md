# Run GCP tools with docker container
## Install
```bash
git clone https://github.com/tomraulet/gcp-sdk.git
cd gcp-sdk
# to build customized image (workdir set)
docker build -t gcp-sdk:latest .
# to create a volume with your credential
docker run -ti --name gcloud-config google/cloud-sdk gcloud auth application-default login

# add alias to use gcloud in your shell. it requies to NOT have a previously installed version of gcloud on your system
echo "alias gcloud='docker run --rm -ti -v \$PWD:/root/workdir -v ~/.config/gcloud:/root/.config/gcloud -v ~/.kube:/root/.kube gcp-sdk gcloud \$@'" >> ~/.bashrc

source ~/.bashrc
```

Adapt `~/.bashrc`  according to the shell you're using.

## Usage
Use `gcloud` as you would use it normally.

e.g `gcloud version`
