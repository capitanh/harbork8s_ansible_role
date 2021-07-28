Harbor on Kubernetes Ansible Role
===============================
This role will deploy the official Harbor helm chart onto a k8s cluster (tested only in microk8s, due to specific storage class)

Requirements
------------
A functioning nicrok8s installation. You can use the following role to boot up such a cluster:
https://github.com/capitanh/microk8s_ansible_role

Role Variables
--------------
Tne variables required by this role are:
```yaml
# General
harbor_namespace:         harbor                      # k8s cluster namespace to deploy pods under
harbor_app_name:          harbor                      # Deployed helm app name
harbor_password:          admim                       # Admin password

# Persistent volume
harbor_pv_name:           harbor-server               # Persisten volume name
harbor_pv_storage_size:   30Gi                        # Persistent volume size

# Persistent volume claim
harbor_pvc_name:          harbor-server               # Persistent volume claim name
harbor_pvc_size:          30Gi                        # Persistent volume claim size
harbor_data_dir:          /var/harbor                 # Harbor root dir

```

Dependencies
------------
None

Example Playbook
----------------
Register the role in requirements.yml:
```yaml
    - src: capitanh.harbork8s_ansible_role
      name: harbork8s
```
Include it in your playbooks:
```yaml
    - hosts: servers
      roles:
      - harbork8s
```

License
-------
BSD
