# Installation of AWX

## Step 1: Install microk8s on ubuntu

    - update the hostname in the inventory
    - ansible-playbook -i inventory.ini install_microk8s.yml

## Step 2: Deploy the AWX on ubuntu

    - update the storage value in deploy_awx.yml
    - update the nodeAffinity value in deploy_awx.yml
    - microk8s kubectl apply -f deploy_awx.yml

## Step 3: Login AWX console

Console location is http://server-ip-address:30765

    - microk8s kubectl get svc -n awx | grep NodePort

Default username is "admin"

Default password is

    - microk8s kubectl get secret ansible-awx-admin-password --template={{.data.password}} -n awx | base64 -d
