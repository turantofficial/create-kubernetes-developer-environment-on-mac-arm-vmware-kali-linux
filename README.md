# create-kubernetes-developer-environment-on-mac-arm-vmware-kali-linux


1. Complete VMWare & Kali Linux  
https://www.kali.org/docs/virtualization/install-vmware-silicon-host/  
https://www.kali.org/get-kali/#kali-installer-images  

2. Install kubectl and validate (see https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)  
`curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl"`  

Validate:  
`curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl.sha256"`  

Checksum:
`echo "$(cat kubectl.sha256)  kubectl" | shasum -a 256 --check`  

Make the kubectl binary executable    
`chmod +x ./kubectl`  

Move the kubectl binary to a file location on your system PATH  
```
sudo mv ./kubectl /usr/local/bin/kubectl
sudo chown root: /usr/local/bin/kubectl
```

Test:  
`kubectl version --client`


3. Install the latest minikube stable release on ARM64 Linux using binary download:
```
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-arm64
sudo install minikube-linux-arm64 /usr/local/bin/minikube && rm minikube-linux-arm6
```
  

4. Install Docker  
`sudo -i && apt update & apt install docker.io`

5. Start minikube e.g.  
```
minikube start --driver=docker --memory=1536mb --disk-size=6g
sudo usermod -aG docker $USER && newgrp docker`
```

