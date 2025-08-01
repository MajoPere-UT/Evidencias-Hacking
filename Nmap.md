# Actividad: Escaneo con Nmap y Análisis de Tráfico con Wireshark
Descripción de la actividad
En esta práctica se realizó un escaneo de red utilizando la herramienta Nmap con el objetivo de identificar hosts activos y servicios expuestos. Se ejecutó un barrido sobre la red 152.168.56.0/24 para obtener información sobre puertos abiertos y servicios detectados.

# Resultados obtenidos
Durante el escaneo se identificó un host activo en la dirección IP 152.168.56.1.
Este host presenta únicamente dos puertos TCP abiertos, asociados a servicios PacketCable utilizados en entornos de telecomunicaciones y VoIP.
Además, se observó que la mayoría de los puertos se encuentran filtrados o cerrados, lo que indica la presencia de un firewall o política de seguridad restrictiva.

# Puertos detectados:

2126/tcp open pktcable-cops
Servicio relacionado con PacketCable COPS, empleado para control de dispositivos en redes de cable.

3918/tcp open pktcablemmcops
Servicio PacketCable Multimedia COPS, orientado a control de señalización multimedia.

La presencia de estos puertos confirma que el dispositivo pertenece a una infraestructura de telecomunicaciones (como un cablemodem, servidor VoIP o equipo de red controlado). Aunque existe filtrado de la mayoría de puertos, la exposición de servicios administrativos requiere verificación de autenticación segura para evitar accesos indebidos.

#Evidencia
A continuación se presenta la captura del escaneo realizado con Nmap, donde se aprecian los resultados mencionados:
<img width="918" height="697" alt="image" src="https://github.com/user-attachments/assets/a9936478-6344-490c-8e04-6682114e7adb" />
