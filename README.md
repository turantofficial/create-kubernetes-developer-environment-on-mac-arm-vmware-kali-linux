# create-kubernetes-developer-environment-on-mac-arm-vmware-kali-linux


1. Complete VMWare & Kali Linux  

2. Install kubectl and validate  
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm64/kubectl"
```

Validate:  
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm64/kubectl.sha256"
```

Checksum:
```
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
```
Install kubectl  
```
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

3. Install the latest minikube stable release on ARM64 Linux using binary download:
```
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

kubectl version --client


4. Install Docker  
```
sudo -i && apt update & apt install docker.io
```

5. Start minikube e.g.  
```
minikube start --driver=docker --memory=1536mb --disk-size=6g
```

```
sudo usermod -aG docker $USER && newgrp docker
```

https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/  
https://www.kali.org/docs/virtualization/install-vmware-silicon-host/  
https://www.kali.org/get-kali/#kali-installer-images  
