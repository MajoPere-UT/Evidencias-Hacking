# Evidencias-Hacking

# Inyección SQL #
La primera prueba identificó una vulnerabilidad de inyección SQL en el módulo de autenticación. Desde el menú principal, se accedió al archivo login.php, el cual mostraba dos campos: uno para ingresar el usuario y otro para la contraseña.

En el campo de usuario se introdujo esta cadena maliciosa: ' OR '1'='1. En la contraseña se colocó cualquier valor aleatorio, ya que no influía en la prueba. Al presionar el botón de acceso, el sistema permitió entrar sin validar credenciales reales.

Este resultado confirma la existencia de una inyección SQL, ya que la consulta enviada al servidor fue manipulada para que la condición WHERE siempre resultara verdadera, omitiendo así la verificación de usuario y contraseña.

Esto evidencia una grave falla de seguridad por no emplear consultas preparadas ni sanitizar los datos ingresados por el usuario.
<img width="1347" height="551" alt="image" src="https://github.com/user-attachments/assets/b96deddd-059f-45a4-a13d-95803df9a9e3" />


# XSS reflejado en el módulo de información del navegador #
En la segunda prueba se exploró la existencia de una vulnerabilidad de tipo XSS reflejado. La prueba se llevó a cabo en el archivo browser-info.php, que muestra datos del navegador a partir de los parámetros que se envían en la URL.

Se modificó manualmente la URL para añadir el siguiente fragmento:
&UserAgent=<script>alert('HolaMundo')</script>

Al recargar la página, el navegador ejecutó el script, mostrando una alerta con el texto “HolaMundo”.

Esto confirma que el parámetro UserAgent fue incorporado en la respuesta HTML sin ninguna codificación o escape, permitiendo que código JavaScript se ejecute directamente. Este tipo de vulnerabilidad puede ser aprovechado para engañar a usuarios y ejecutar scripts maliciosos simplemente con que accedan a un enlace manipulado.
<img width="1784" height="530" alt="image" src="https://github.com/user-attachments/assets/1ace31a1-6911-456d-a41b-77cf2748c2de" />

# XSS persistente en publicaciones del blog #
La tercera vulnerabilidad detectada fue de tipo XSS persistente, mediante el uso del archivo add-to-your-blog.php. Esta sección permite a los usuarios crear publicaciones en su blog personal, con campos de título y contenido.
Después de guardar la entrada, al visualizarla desde view-someones-blog.php, el script se ejecutó automáticamente y solicitó acceso a la ubicación del usuario.

Aunque esta prueba usó un ejemplo local (http://localhost/log.php), un atacante real podría utilizar esto para robar información y enviarla a servidores externos. Este tipo de vulnerabilidad es muy peligrosa, ya que el script queda guardado en el servidor y se ejecuta cada vez que alguien visita esa entrada, sin necesidad de interacción adicional.
<img width="1688" height="718" alt="image" src="https://github.com/user-attachments/assets/9d9ec974-4087-4649-a9bf-e1e9a54a08fb" />


