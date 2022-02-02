# install-rke-rancher-on-aws-ec2

## prepare the ubuntu vm

### install docker
```shell
curl https://releases.rancher.com/install-docker/20.10.sh | sh
```

### install rke
```shell
wget https://github.com/rancher/rke/releases/download/v1.3.6/rke_linux-amd64
mv rke_linux-amd64 rke
chmod +x rke
sudo mv rke /usr/local/bin/
```

### install helm
```shell
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```

### insstall kubectl
```shell
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```
