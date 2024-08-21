# home-assistant-k3s
home-assistant



## Set static IP
sudo nmcli c mod "Wired connection 1" ipv4.addresses 192.168.x.x/24 ipv4.method manual
sudo nmcli con mod "Wired connection 1" ipv4.gateway 192.168.x.x
sudo nmcli con mod "Wired connection 1" ipv4.dns "192.168.x.x"

## Rotate Certs (365 days valid)
Self signed cert of k3s [Cert](https://docs.k3s.io/cli/certificate#client-and-server-certificates)
#### Stop K3s
systemctl stop k3s

#### Rotate certificates
k3s certificate rotate

#### Start K3s
systemctl start k3s


### Add configuration to container
As long as there is no package created we manually create the helm chart by file

`kubectl create configmap hoa-cfgmap --from-file ../config/configuration.yaml`