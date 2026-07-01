# VPN Client-To-Site FortiGate con Windows Server

**Estudiante:** Michael Robles  
**Matrícula:** 20250845 / 2025-0845  
**Asignatura:** Seguridad de Redes  
**Tipo de VPN:** IPsec IKEv2 Client-To-Site con FortiGate y FortiClient VPN  

## Enlaces

- Repositorio: https://github.com/iClexi/VPN-Fortigate-WindowsClient-To-Site
- Video demostrativo: https://youtu.be/2H8e8zFij4A?si=V2V2YgyBpe7cFVhp

## Resumen del laboratorio

Este laboratorio implementa una VPN Client-To-Site usando un FortiGate como concentrador VPN y un Windows Server como cliente remoto mediante FortiClient VPN. El cliente remoto se encuentra del lado de la LAN A y se conecta hacia la IP WAN del FortiGate. Al conectarse, recibe una IP virtual del pool `10.25.84.10-10.25.84.100` y puede acceder a la LAN interna protegida `192.168.45.0/24`, donde se encuentra PC-B.

## Topología lógica

```text
Cliente Windows Server -> SW-A -> ISP -> FortiGate port1 -> FortiGate port3 -> SW-B -> PC-B
```

## Direccionamiento principal

| Elemento | Dirección | Descripción |
|---|---:|---|
| Cliente Windows Server físico | 20.25.45.10/24 | Cliente remoto antes de conectar VPN |
| ISP hacia LAN A | 20.25.45.1/24 | Gateway del lado del cliente |
| ISP hacia FortiGate | 20.25.8.45/30 | Enlace de tránsito hacia FortiGate |
| FortiGate port1 | 20.25.8.46/30 | WAN que recibe la VPN |
| FortiGate port3 | 192.168.45.1/24 | Gateway de la LAN B interna |
| PC-B | 192.168.45.10/24 | Equipo interno protegido |
| Pool VPN | 10.25.84.10-10.25.84.100 | Rango virtual para clientes VPN |

## Elementos incluidos

- `docs/`: documentación técnica profesional en Word y archivo de enlaces.
- `images/`: evidencias tomadas del laboratorio.
- `scripts/`: configuraciones de SW-A, SW-B e ISP.
- `1.txt`: enlaces del repositorio y video.

## Pruebas realizadas

- Conexión de FortiClient hacia el túnel `C2S_IKE`.
- Asignación de IP VPN `10.25.84.10` al Windows Server.
- Ping desde Windows Server hacia PC-B `192.168.45.10`.
- Traceroute desde Windows Server hacia PC-B.
- Ping inverso desde PC-B hacia el cliente VPN `10.25.84.10`.
- Trace desde PC-B hacia el cliente VPN.

## Nota de seguridad

En el laboratorio se usaron parámetros compatibles con el entorno probado. Para ambientes productivos se recomienda usar algoritmos más fuertes, como AES con SHA-256 o superior, grupos Diffie-Hellman más robustos y políticas restrictivas por servicio.
