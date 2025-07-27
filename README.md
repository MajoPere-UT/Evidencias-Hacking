# Evidencias-Hacking
Inyección SQL en el formulario de inicio de sesión
La primera prueba identificó una vulnerabilidad de inyección SQL en el módulo de autenticación. Desde el menú principal, se accedió al archivo login.php, el cual mostraba dos campos: uno para ingresar el usuario y otro para la contraseña.

En el campo de usuario se introdujo esta cadena maliciosa: ' OR '1'='1. En la contraseña se colocó cualquier valor aleatorio, ya que no influía en la prueba. Al presionar el botón de acceso, el sistema permitió entrar sin validar credenciales reales.

Este resultado confirma la existencia de una inyección SQL, ya que la consulta enviada al servidor fue manipulada para que la condición WHERE siempre resultara verdadera, omitiendo así la verificación de usuario y contraseña.

Esto evidencia una grave falla de seguridad por no emplear consultas preparadas ni sanitizar los datos ingresados por el usuario.
