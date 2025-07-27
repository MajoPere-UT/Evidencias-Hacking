# 🛡️ Pruebas de Seguridad con Burp Suite  

# Configuración de Proxy en Burp Suite

Primero, abrimos **Burp Suite** y nos dirigimos a la pestaña **Proxy**, ubicada en la parte superior. Desde ahí, entramos en **opciones de configuración** para asegurarnos de que la conexión esté apuntando a `localhost` (ya que es el entorno que estamos utilizando).

Es importante **activar la casilla “response”** para poder ver las respuestas del servidor. Una vez hecho esto, damos clic en **"Open browser"**.

<img width="1894" height="760" alt="image" src="https://github.com/user-attachments/assets/e5dfc8a0-53f1-4910-975c-153f6423fa31" />


---

# Acceso a Mutillidae desde el navegador

Se abrirá automáticamente un navegador basado en Chromium proporcionado por Burp Suite. En este navegador, accedemos a **localhost** para ingresar a **Mutillidae**.

Dentro de Mutillidae, vamos a **OWASP 2017 > SQL Injection > SQL Insert Injection > Register**, donde se encuentra el formulario de registro. Aquí se deben completar los campos solicitados como nombre de usuario y contraseña.

<img width="1913" height="917" alt="image" src="https://github.com/user-attachments/assets/b8e9bb6e-1c96-4e84-bc01-9416b18a9829" />


---

# Iniciar sesión y capturar tráfico

Para analizar el inicio de sesión, entramos a **OWASP 2017 > SQL Injection > SQL Extract Data > User Info**. Esta sección muestra un formulario de login.

Para monitorear lo que se transmite entre cliente y servidor, **activamos la opción “Intercept”** en Burp Suite.

<img width="1202" height="448" alt="image" src="https://github.com/user-attachments/assets/8181da5f-8a53-49b5-a554-131b4d4d2d7d" />


---

# Control de solicitudes

Una vez interceptada la solicitud, el navegador quedará esperando respuesta. Esto se debe a que **Burp Suite está controlando el flujo de datos**. En este punto podemos observar con detalle lo que el usuario está enviando al servidor.


<img width="1516" height="628" alt="image" src="https://github.com/user-attachments/assets/98671b48-8c17-4f27-9f06-31f3f6ddd9bc" />

---

# Modificación de la solicitud (método canario)

Se procede a modificar manualmente la solicitud antes de enviarla. Esto permite hacer pruebas como cambiar los datos del formulario o manipular respuestas del servidor. En este caso, al enviar la contraseña y verificar la respuesta en la pestaña "response", se confirma que el inicio de sesión fue exitoso.

<img width="1784" height="555" alt="image" src="https://github.com/user-attachments/assets/74b5ae5c-9e96-40e0-9fc0-1037870b2e44" />


---

# Escalada de privilegios

Para cambiar el rol del usuario (por ejemplo, de usuario común a administrador), primero se activa de nuevo **“Intercept”** al iniciar sesión. En el encabezado de la solicitud (`header`), se edita el parámetro `uid` y se asigna el valor `1`.

Esto simula que el usuario es el administrador. Finalmente, al reenviar la solicitud con **"Forward"**, se comprueba que se obtuvo acceso como admin aunque las credenciales eran de usuario normal.

<img width="348" height="473" alt="image" src="https://github.com/user-attachments/assets/0b8b8279-9fea-439e-a914-6ab52635bf4e" />
