#Formato de Auditoría OSINT: Reconocimiento Pasivo de Dominio
Introducción
Objetivo: Realizar un reconocimiento pasivo completo de un dominio utilizando dnsdumpster.com, centrolops.net, FOCA, Shodan, Google Dorks y otras herramientas de OSINT.
Llena cada sección con la información obtenida durante la actividad.
1. Mapeo DNS y Subdominios
Dominio objetivo: salud.qroo.gob.mx
Fecha de análisis: 

1.1 Subdominios encontrados:
Subdominio	IP	TTL	Ubicación geográfica
cloud.salud.qroo.gob.mx	187.216.252.2		México
webmail.salud.qroo.gob.mx	187.216.252.10		México
correo.salud.qroo.gob.mx	187.216.252.2		México
correspondencia.salud.qroo.gob.mx	187.216.252.4		México
covid.salud.qroo.gob.mx	187.216.252.14		México
epi.salud.qroo.gob.mx	187.216.229.131		México
grp.salud.qroo.gob.mx	187.216.229.130		México
sistemas.salud.qroo.gob.mx	187.216.229.132		México
tarjetas.salud.qroo.gob.mx	187.216.252.3		México

1.2 Name Servers (NS):
  <img width="803" height="135" alt="image" src="https://github.com/user-attachments/assets/8065dd14-e0e1-4f38-b37b-6df064387af3" />

1.3 Registros MX (servidores de correo):
 <img width="900" height="268" alt="image" src="https://github.com/user-attachments/assets/54df52fb-85c4-4457-9af3-e5e449b22caa" />

2. WHOIS y Datos de Registro
 <img width="951" height="836" alt="image" src="https://github.com/user-attachments/assets/b567a661-b86c-4ef3-b83b-fc58a4c9fcdf" />

3. Metadatos de Documentos (FOCA)
 <img width="1200" height="923" alt="image" src="https://github.com/user-attachments/assets/a959b5cc-75ee-41a1-b975-d377bfafa7c0" />

4. Servicios Expuestos (Shodan)
 <img width="900" height="485" alt="image" src="https://github.com/user-attachments/assets/ad1f7e02-3fb8-4d87-a58f-ce7b1c5af2d2" />

5. Hallazgos con Google Dorks
5.1 Consultas utilizadas y resultados encontrados:
Consulta Dork	URL/Resultado encontrado
	
	
	
	
	

5.2 Descripción de riesgos de cada hallazgo:
 - Hallazgo 1: ____________________________
 - Hallazgo 2: ____________________________
 - Hallazgo 3: ____________________________

6. Recomendaciones de Hardening Inicial
Basado en los hallazgos anteriores, sugerir medidas para mejorar la seguridad:
1.	Ocultar o restringir el acceso público a subdominios sensibles como webmail, correo, correspondencia, sistemas y tarjetas mediante VPN o filtrado por IP.
2.	Implementar HTTPS en todos los subdominios con certificados válidos y configuración TLS actualizada.
3.	Deshabilitar servicios innecesarios expuestos y cerrar puertos no utilizados detectados por Shodan.
4.	Mantener sistemas y aplicaciones actualizados para evitar explotación de vulnerabilidades conocidas.
5.	Configurar políticas de seguridad DNS (DNSSEC, SPF, DKIM, DMARC) para proteger la integridad del correo y prevenir suplantación.



7. Conclusión
Resumen de los hallazgos más relevantes y lecciones aprendidas:
El reconocimiento pasivo permitió identificar múltiples subdominios y posibles vectores de ataque asociados al dominio salud.qroo.gob.mx. La visibilidad de servicios de correo, sistemas administrativos y aplicaciones web sugiere la necesidad de implementar controles adicionales de seguridad.
Las medidas de hardening recomendadas están orientadas a reducir la superficie de exposición, proteger la comunicación y reforzar la seguridad perimetral. Este ejercicio demuestra que incluso sin interacción activa, es posible obtener información sensible que, en manos maliciosas, podría ser aprovechada, lo que resalta la importancia de un monitoreo continuo y de la defensa en profundidad.


