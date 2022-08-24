## Deploy pi-hole on K8s/K3s/etc...

Some housekeeping:
1. pi-hole documentation is [here](https://github.com/pi-hole/docker-pi-hole)
2. This deployment is based off of [this](https://subtlepseudonym.medium.com/pi-hole-on-kubernetes-87fc8cdeeb2e) blog post

Steps:
1. Create a dedicated namespace for pi-hole with pihole-namespace.yml. If you change the name, be sure to update it in the rest of the yaml files
2. Create a storage class with pihole-sc.yml. In my case, I am running a single-node K3s cluster and will be mounting a local directory
3. Create a persistent volume for /etc/pihole and /etc/dnsmasq.d with pihole-pvs.yml
4. Create a persistent volume claim for the above with pihole-pvcs.yml
5. Create a secret for the pi-hole web password with pihole-admin-secret.yml. Please insert a base64 encoded secret in this file
6. Create a service with pihole-services.yml. Be sure to add the DHCP ports if you use that functionality (I don't)
7. Create the deployment with pihole-deploy.yml. Adjust the env variables and resources as needed


