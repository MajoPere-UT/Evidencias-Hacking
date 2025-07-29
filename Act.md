# Informe de Evidencia – Escaneo con Nmap y Captura con Wireshark**

# Actividad realizada

Se ejecutó un escaneo de red sobre el rango `192.168.56.0/24` utilizando **Nmap**, aplicando diferentes técnicas de descubrimiento y escaneo de puertos. Paralelamente, se utilizó **Wireshark** para capturar y analizar el tráfico generado por dichas pruebas.

# Comandos ejecutados

En la terminal se ejecutaron los siguientes comandos:

   sudo nmap -sP 192.168.1.0/24
   

Parámetro `-sP`: Realiza un “Ping Scan” para detectar qué hosts responden en la subred.


   sudo nmap -sS -Pn --source-port 53 --scan-delay 15 192.168.56.1
  
    `-sS`: Escaneo SYN Stealth (envía SYN sin completar handshake).
    `-Pn`: Omite la detección de host, asumiendo que está activo.
    `--source-port 53`: Usa el puerto 53 (DNS) para intentar evadir filtrado.
    `--scan-delay 15`: Retraso entre sondas para reducir detección.


   sudo nmap -sS -Pn --source-port 53 --scan-delay 15 192.168.56.0/24
 
 Escanea todos los hosts en el rango para identificar puertos abiertos.


# Resultados observados*

Nmap detectó hosts activos dentro de la red y realizó escaneos SYN sobre ellos.
Wireshark capturó paquetes TCP con banderas SYN enviados a múltiples direcciones y puertos.
Se confirmo tráfico característico de escaneos de reconocimiento, sin intercambio de datos posteriores.

La combinación de Nmap y Wireshark confirma un proceso de auditoría orientado a **reconocimiento pasivo/activo**.
Los paquetes SYN confirman la ejecución de un **escaneo stealth**, evitando completar el handshake TCP para reducir el riesgo de detección.
El uso del puerto de origen 53 es una técnica clásica para evadir sistemas de detección, aprovechando que el tráfico DNS suele ser permitido.

Captura de Nmap y Wireshark:
<img width="1365" height="733" alt="image" src="https://github.com/user-attachments/assets/77d8124c-c2d6-4c35-9ffd-654d1126584c" />

