
---
# Lab

[HOME](../../README.md)

---
## VLANS
### Switches (SW)
#### 1. Definir una VLAN
Se deben definir en todos los SW que usen VLANs, aunque no estén asignadas a una interfaz.
```bash
Switch(config)# vlan <NUM>
Switch(config-vlan)# name <NAME>
Switch(config-vlan)# exit
```
#### 2. Asignar VLAN a una interfaz
El trafico entrante por la interfaz es marcado con la VLAN especificada.
Por defecto todas las interfaces usan la VLAN 1.
```bash
Switch(config)# interface <INTERFACE>
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan <NUM>
Switch(config-if)# exit
```
#### 3. Asignar interfaces de trunking
Permite el paso de varias VLANs especificadas. Si no se especifica permite todas.
```bash
Switch(config)# interface <INTERFACE>
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan <NUM>
Switch(config-if)# switchport trunk allowed vlan [add/all/except/remove] <NUM>
Switch(config-if)# exit
```
### Router on-a-stick
Permite configurar varias interfaces virtuales para diferentes VLANs en la misma interfaz física.
```bash
Router(config)# interface <INTERFACE>.<VLAN_NUM>
Router(config-subif)# encapsulation dot1q <VLAN_NUM>
Router(config-subif)# ip address <IP> <MASK>
Router(config-subif)# ipv6 address <IPv6>/<BITS_MASK>
Router(config-subif)# ipv6 address <IPv6> link-local
```
### Switches Capa 3
#### Configuración puerto de acceso de una sola VLAN
```bash
Switch(config)# interface <INTERFACE>
Switch(config-if)# switchport acces vlan <NUM>
```
#### Configuración puerto troncal
```bash
Switch(config)# interface <INTERFACE>
Switch(config-if)# switchport trunk encapsulation dot1q
Switch(config-if)# switchport mode trunk
```
#### Configuración SVI (Switch Virtual Interface)
```bash
Switch(config)# interface vlan <NUM>
Switch(config-if)# ip address <IP> <MASK>
Switch(config-subif)# ipv6 address <IPv6>/<BITS_MASK>
Switch(config-subif)# ipv6 address <IPv6> link-local
Switch(config-if)# no shutdown
```
(La interfaz por la que recibirá los paquetes tiene que ser configurada también)
#### Activación del routing IP para layer 3
```bash
Switch(config)# ip routing
Switch(config)# ipv6 unicast-routing
```
#### Configuración de una interfaz como puerto enrutado
```bash
Switch(config)# interface <INTERFACE>
Switch(config-if)# no switchport
Switch(config-if)# ip address <IP> <MASK>
Switch(config-if)# ipv6 address <IPv6>/<BITS_MASK>
Switch(config-if)# ipv6 address <IPv6> link-local
```
---
## DHCP
### IPv4
```bash
Router(config)# ip dhcp excluded-address <ADDRESS>
Router(config)# ip dhcp excluded-address <ADDRESS_LOW> <ADDRESS_HIGH>

Router(config)# ip dhcp pool <NAME>
Router(dhcp-config)# network <IP_NETWORK> <MASK>
Router(dhcp-config)# default-router <IP_GW>
Router(dhcp-config)# dns-server <IP_DNS>
Router(dhcp-config)# domain-name <DOMAIN>
```
---
## Routing
### Static
```bash
Router(config)#ip route <NET_IPv4> <MASK> <NEXT_HOP_IPv4>
Router(config)#ipv6 route <NET_IPv6>/<MASK> <NEXT_HOPP_IPv6>
```
## OSPFv2 (IPv4)
```bash
Router(config)# router ospf 10 (id proceso, vale cualquiera)
Router(config-router)# router-id 3.3.3.3 (unico para todos los routers)
Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
Router(config-router)# network 192.168.4.252 0.0.0.3 area 0
Router(config-router)#... (redes directamente conectadas que se quieran anunciar)
Router(config-router)# passive-interface G0/0 (Int no conectadas a router OSPF)
```
## OSPFv3 (IPv6)
```bash
Router(config)# ipv6 unicast-routing
Router(config)# ipv6 router ospf 10
Router(config-rtr)# router-id 3.3.3.3

Router(Config)# interface <INTERFACE>
Router(Config-if)# ipv6 ospf 10 area 0
Router(Config)# ... (Hablitar en TODAS las interfaces con IPv6)
```
---
## NAT Dinámico con Sobrecarga (NAT/PAT)
```bash
Router(Config)# access-list <NUM_LIST> permit <RED_INTERNA> <WILDCARD_MASK>
Router(Config)# ip nat pool <NAME_POOL> <IP_ADDR_BAJA> <IP_ADDR_ALTA> netmask <MASK> 
Router(Config)# ip nat inside source list <NUM_LIST> pool <NAME_POOL> overload
Router(Config)# interface <INTERFACE>
Router(Config-if)# ip nat inside
Router(Config)# interface <INTERFACE>
Router(Config-if)# ip nat outside
```
En un L3 switch solo funciona en las subinterfaces (int vlan 1).
Se puede usar la vlan 1 (default)  para la salida a otros routers sin VLANs.

---
## Access Control Lists (ACLS)
Las ACLs por defecto rechazan todas las conexiones.
El orden en el que se introducen es el orden en el que se comprueban.
## ACL estándar
```bash
Router(config)# access-list <ACL_NUM> {permit|deny} host <IP>
Router(config)# access-list <ACL_NUM> {permit|deny} any
Router(config)# access-list <ACL_NUM> {permit|deny} <NETWORK> <WILDCARD>

Router(config)#interface <INTERFACE>
Router(config-if)#ip access-group <ACL_NUM> {in|out}
```
ACL_NUM tiene que ser entre 1 y 99 o entre 1300 y 1999
## ACL extendida
```bash
Router(config)#access-list <ACL_NUM> {permit|deny} <PROTOCOLO> <ORIGEN> <DESTINO> <CONDITION>

Router(config)#interface <INTERFACE>
Router(config-if)#ip access-group <ACL_NUM> {in|out}
```
ACL_NUM tiene que ser entre 100 y 199 o entre 2000 y 2699
Donde:
- `<PROTOCOL>` puede ser: `tcp`, `udp`, `icmp` o `ip` (icmp e ip no admiten la condición)
- `<ORIGEN>` y `<DESTINO>` pueden ser:
	- `<NETWORK> <WILDCARD>`
	- `host <IP>`
	- `any`
- `<CONDITION>` puede ser:
	-  `eq <PORT>` (igual)
	- `gt <PORT>` (greater than)
	- `ly <PORT>` (less than)
	- `neq <PORT>` (no equal)
	- `range <PORT_LOW> <PORT_HIGH>` (Dentro del rango con ambos incluidos)
## Ver y eliminar ACLs
```bash 
Router#show access-lists
Router#show access-lists <ACL_NUM>

Router(config)#no access-list <ACL_NUM> {permit|deny} ...
Router(config)#no access-list <ACL_NUM>
```