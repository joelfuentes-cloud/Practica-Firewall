🛠️ Proceso paso a paso: 
Creación del Directorio: Se creó la carpeta de trabajo practica_firewall y los subdirectorios workdata y confdir para que la configuración sea persistente y no se pierda al borrar el contenedor.

Configuración con Docker Compose: Se creó un archivo docker-compose.yml para gestionar el servicio, mapeando los puertos clave:

53: Para las peticiones DNS.

3000: Para el asistente de instalación inicial.

80: Para el panel de control web.

Despliegue: Se levantó el servicio con el comando docker-compose up -d.

Configuración del Sistema: Se modificó la configuración de red en Windows, cambiando el servidor DNS por la dirección de bucle local 127.0.0.1.

Activación de Filtros: Se accedió al panel web para verificar que las listas de bloqueo estuvieran activas y procesando el tráfico.

🛡️ ¿Qué función tiene?
La función principal de este despliegue es actuar como un Firewall DNS. Sus beneficios son:

Bloqueo de publicidad: Detecta peticiones a servidores de anuncios y las bloquea antes de que se descarguen.

Privacidad: Evita que los rastreadores (trackers) recopilen datos de navegación.

Seguridad: Puede bloquear dominios conocidos por distribuir malware o realizar phishing.

Control de red: Permite monitorizar qué dispositivos de la red están haciendo más consultas y qué dominios visitan.

🚀 ¿Cómo se usa?
1. Iniciar el servidor
Desde la carpeta del proyecto, ejecuta en la terminal:

DOS
docker-compose up -d
2. Configurar el cliente
Para que el filtrado funcione, el dispositivo debe usar el servidor. En Windows:

Ve a Configuración de red -> Propiedades de IPv4.

Cambia el DNS a: 127.0.0.1.

3. Verificar el funcionamiento
Para comprobar que el firewall está trabajando, abre una terminal (CMD) y escribe:

DOS
nslookup doubleclick.net
Si la respuesta es 0.0.0.0, significa que AdGuard ha interceptado la petición y el bloqueo es exitoso.

4. Consultar estadísticas
Entra en tu navegador a http://localhost para ver el Panel de Control, donde aparecerán los gráficos de consultas totales y elementos bloqueados en tiempo real.



Ejemplo:
<img width="969" height="397" alt="image" src="https://github.com/user-attachments/assets/05c648aa-7e0c-43e4-89b1-ddae5f0d9b58" />
<img width="955" height="727" alt="image" src="https://github.com/user-attachments/assets/8c9fe672-fc90-4588-83a1-7c2ec22ec407" />
