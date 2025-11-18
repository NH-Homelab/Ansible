# Ansible Playbooks
A collection of ansible playbooks that I use to manage VM's on my proxmox host. 


# Example Usage:

### minikube/setup_k8s.yaml
Installs minikube, kubectl, and helm on the target machine.

```
ansible-playbook setup_k8s.yaml \
  -e "target=k8s"
```


### vm_manage/docker_configure.yaml
Ensures that the user is added to the docker group, necessary before running `start_minikube.yaml` playbook.

```
ansible-playbook docker_configure.yaml \
  -e "target=k8s" \
  -e "user=John"
```

### minikube/start_minikube.yaml
Starts minikube on the target and sets kubectl context.

```
ansible-playbook start_minikube.yaml \
  -e "target=k8s"
```

### vm_manage/setup_github_runner.yaml
Creates a self-hosted github runner with the given configuration.

```
ansible-playbook setup_github_runner.yaml \
  -e "target=k8s" \
  -e "github_repo=youruser/yourrepo" \
  -e "runner_name=project-runner" \
  -e "runner_token=YOUR_TOKEN" \
  -e "user=John" \
  -e "runner_labels=self-hosted"
```

### vm_manage/update_hostname.yaml
Updates the hostname for the target. Typically used after cloning from a template VM.

```
ansible-playbook update_hostname.yaml \
  -e "target=k8s" \
  -e "hostname=node1"
```

### vm_manage/update_packages.yaml
Effectively runs `apt-get update && apt-get upgrade -y` on the target machine.

```
ansible-playbook update_packages.yaml \
  -e "target=k8s"
```
