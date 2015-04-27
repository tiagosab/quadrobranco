# notas preparatõrias

## rotas sem o strongvpn
default via 192.168.1.1 dev wlan0  proto static  metric 1024 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.115 
## rotas com o strongvpn

default dev ppp0  proto static  scope link  metric 1024 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
173.255.176.27 via 192.168.1.1 dev wlan0  src 192.168.1.115 
173.255.187.129 dev ppp0  proto kernel  scope link  src 173.255.187.250 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.115 

# passos

. remover rota padrão strongvpn

sudo ip route del default dev ppp0 proto static scope link metric 1024

. acrescentar rota padrão normal

sudo ip route add default via 192.168.1.1 dev wlan0  proto static
metric 1024

. acrescentar regra de roteamento

sudo ip rule add fwmark 2 table 3

. acrescentar rota na tabela 3

sudo ip route add default dev ppp0 via proto static scope link metric 1024

. configurar o programa para rodar com o usuário determinado

sudo adduser --system --no-create-home tinyproxy
alterar /etc/tinyproxy.conf para indicar o usuário

. marcar os pacotes gerados pelo usuário

iptables -t mangle -A OUTPUT -m owner --uid-owner 125 -j MARK --set-mark 2

. masquerade porque?

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

. Para garantir que a conexão com o vpn já não indique rotas
