# 🛡️ Pruebas de Seguridad con Burp Suite  
**⚠️ Nota:** Esta práctica se realiza únicamente con fines educativos.

---

## 🔧 Paso 1: Configuración de Proxy en Burp Suite

Primero, abrimos **Burp Suite** y nos dirigimos a la pestaña **Proxy**, ubicada en la parte superior. Desde ahí, entramos en **opciones de configuración** para asegurarnos de que la conexión esté apuntando a `localhost` (ya que es el entorno que estamos utilizando).

Es importante **activar la casilla “response”** para poder ver las respuestas del servidor. Una vez hecho esto, damos clic en **"Open browser"**.

![alt text](/imgclass1/image.png)

---

## 🌐 Paso 2: Acceso a Mutillidae desde el navegador

Se abrirá automáticamente un navegador basado en Chromium proporcionado por Burp Suite. En este navegador, accedemos a **localhost** para ingresar a **Mutillidae**.

Dentro de Mutillidae, vamos a **OWASP 2017 > SQL Injection > SQL Insert Injection > Register**, donde se encuentra el formulario de registro. Aquí se deben completar los campos solicitados como nombre de usuario y contraseña.

![alt text](/imgclass1/image-1.png)

---

## 🔍 Paso 3: Iniciar sesión y capturar tráfico

Para analizar el inicio de sesión, entramos a **OWASP 2017 > SQL Injection > SQL Extract Data > User Info**. Esta sección muestra un formulario de login.

Para monitorear lo que se transmite entre cliente y servidor, **activamos la opción “Intercept”** en Burp Suite.

![alt text](/imgclass1/image-2.png)  
![alt text](/imgclass1/image-3.png)  
![alt text](/imgclass1/image-4.png)

---

## 📡 Paso 4: Control de solicitudes

Una vez interceptada la solicitud, el navegador quedará esperando respuesta. Esto se debe a que **Burp Suite está controlando el flujo de datos**. En este punto podemos observar con detalle lo que el usuario está enviando al servidor.

![alt text](/imgclass1/image-5.png)  
![alt text](/imgclass1/image-6.png)

---

## 🧪 Paso 5: Modificación de la solicitud (método canario)

Se procede a modificar manualmente la solicitud antes de enviarla. Esto permite hacer pruebas como cambiar los datos del formulario o manipular respuestas del servidor. En este caso, al enviar la contraseña y verificar la respuesta en la pestaña "response", se confirma que el inicio de sesión fue exitoso.

![alt text](/imgclass1/image-7.png)

---

## 🔐 Paso 6: Escalada de privilegios

Para cambiar el rol del usuario (por ejemplo, de usuario común a administrador), primero se activa de nuevo **“Intercept”** al iniciar sesión. En el encabezado de la solicitud (`header`), se edita el parámetro `uid` y se asigna el valor `1`.

Esto simula que el usuario es el administrador. Finalmente, al reenviar la solicitud con **"Forward"**, se comprueba que se obtuvo acceso como admin aunque las credenciales eran de usuario normal.

![alt text](/imgclass1/image-8.png)  
![alt text](/imgclass1/image-9.png)  
![alt text](/imgclass1/image-10.png)