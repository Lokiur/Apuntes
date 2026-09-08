*Cadena de Ciberataques (Cyber Kill Chain)*
	![[Pasted image 20260805015340.png]]
	## Recon
		La etapa de `Recon` (Reconocimiento) es la etapa inicial, e implica la parte en la que un atacante elige su objetivo. Además, el atacante realiza una recopilación de información para familiarizarse más con el objetivo y reúne la mayor cantidad de datos útiles posible, que pueden ser utilizados no solo en esta etapa, sino también en otras etapas de esta cadena. Algunos atacantes prefieren realizar una recopilación pasiva de información desde fuentes web como LinkedIn e Instagram, pero también desde la documentación en las páginas web de la organización objetivo. Los anuncios de trabajo y los socios de la empresa a menudo revelan información sobre la tecnología utilizada en la organización objetivo. Pueden proporcionar información extremadamente específica sobre herramientas antivirus, sistemas operativos y tecnologías de red. Otros atacantes van un paso más allá; comienzan a 'sondear' y escanean activamente aplicaciones web externas y direcciones IP que pertenecen a la organización objetivo.
	## Weaponize
		 En la etapa de `Weaponize` (Armamentización), el malware que se utilizará para el acceso inicial se desarrolla e incrusta en algún tipo de exploit o carga útil (payload) entregable. Este malware está diseñado para ser extremadamente ligero e indetectable por las herramientas antivirus y de detección. Es probable que el atacante haya recopilado información para identificar la tecnología antivirus o EDR (Endpoint Detection and Response) presente en la organización objetivo. A gran escala, el único propósito de esta etapa inicial es proporcionar acceso remoto a una máquina comprometida en el entorno objetivo, que también tiene la capacidad de persistir a través de reinicios de la máquina y la habilidad de desplegar herramientas y funcionalidades adicionales bajo demanda.
	## Deliver
		En la etapa de `Delivery` (Entrega), el exploit o la carga útil se entrega a la(s) víctima(s). Los enfoques tradicionales incluyen correos de phishing que contienen un archivo adjunto malicioso o un enlace a una página web. La página web puede tener dos propósitos: contener un exploit o alojar la carga útil maliciosa para evitar enviarla a través de herramientas de escaneo de correo electrónico. En algunos casos, la página web también puede imitar un sitio web legítimo utilizado por la organización objetivo en un intento de engañar a la víctima para que ingrese sus credenciales y así recopilarlas. Algunos atacantes llaman a la víctima por teléfono con un pretexto de ingeniería social en un intento de convencerla de que ejecute la carga útil. En estos casos para ganar confianza, la carga útil se aloja en un sitio web controlado por el atacante que imita un sitio web conocido por la víctima (p. ej., una copia del sitio web de la organización objetivo). Es extremadamente raro entregar una carga útil que requiera que la víctima haga más que un doble clic en un archivo ejecutable o un script (en entornos de Windows, esto puede ser .bat, .cmd, .vbs, .js, .hta y otros formatos). Finalmente, hay casos en los que se utiliza la interacción física para entregar la carga útil a través de tokens USB y herramientas de almacenamiento similares que se dejan abandonadas a propósito.
	## Exploit
		La etapa de `Exploitation` (Explotación) es el momento en que se activa un exploit o una carga útil entregada. Durante la etapa de explotación de la Cyber Kill Chain, el atacante típicamente intenta ejecutar código en el sistema objetivo para obtener acceso o control.
	##install
		En la etapa de `Installation` (Instalación), el stager inicial se ejecuta y está corriendo en la máquina comprometida. Como ya se discutió, la etapa de instalación puede llevarse a cabo de varias maneras, dependiendo de los objetivos del atacante y la naturaleza del compromiso. Algunas técnicas comunes utilizadas en la etapa de instalación incluyen:
		- **Droppers**: Los atacantes pueden usar droppers para entregar malware en el sistema objetivo. Un dropper es una pequeña pieza de código diseñada para instalar malware en el sistema y ejecutarlo. El dropper puede ser entregado a través de varios medios, como archivos adjuntos de correo electrónico, sitios web maliciosos o tácticas de ingeniería social.
		- **Backdoors**: Una puerta trasera (backdoor) es un tipo de malware diseñado para proporcionar al atacante acceso continuo al sistema comprometido. La puerta trasera puede ser instalada por el atacante durante la etapa de explotación o entregada a través de un dropper. Una vez instalada, la puerta trasera puede ser utilizada para ejecutar ataques posteriores o robar datos del sistema comprometido.
		- **Rootkits**: Un rootkit es un tipo de malware diseñado para ocultar su presencia en un sistema comprometido. Los rootkits se utilizan a menudo en la etapa de instalación para evadir la detección por parte del software antivirus y otras herramientas de seguridad. El rootkit puede ser instalado por el atacante durante la etapa de explotación o entregado a través de un dropper.
	##Comand & Control 
		En la etapa de `Command and Control` (Comando y Control), el atacante establece una capacidad de acceso remoto a la máquina comprometida. Como se discutió, no es raro usar un stager inicial modular que carga scripts adicionales 'sobre la marcha'. Sin embargo, los grupos avanzados utilizarán herramientas separadas para asegurar que múltiples variantes de su malware vivan en una red comprometida, y si una de ellas es descubierta y contenida, todavía tienen los medios para regresar al entorno.
	##Action
		La etapa final de la cadena es la `Action` (Acción) u objetivo del ataque. El objetivo de cada ataque puede variar. Algunos adversarios pueden tener como objetivo exfiltrar datos confidenciales, mientras que otros pueden querer obtener el nivel más alto de acceso posible dentro de una red para desplegar ransomware. El ransomware es un tipo de malware que hace que todos los datos almacenados en dispositivos de punto final y servidores sean inutilizables o inaccesibles a menos que se pague un rescate dentro de un plazo limitado (no recomendado).


*Identificadores para Elastic `event.code:####`*
	
	
| Event ID | Categoría       | Significado                                         | Utilidad en investigación                                 |
| -------- | --------------- | --------------------------------------------------- | --------------------------------------------------------- |
| 4624     | Autenticación   | Inicio de sesión exitoso                            | Identificar quién, cuándo y cómo inició sesión            |
| 4625     | Autenticación   | Inicio de sesión fallido                            | Fuerza bruta, password spraying, credenciales incorrectas |
| 4634     | Autenticación   | Cierre de sesión                                    | Construir timeline                                        |
| 4647     | Autenticación   | Logoff iniciado por usuario                         | Timeline de actividad del usuario                         |
| 4648     | Autenticación   | Uso de credenciales explícitas                      | Detectar posible abuso de credenciales                    |
| 4672     | Privilegios     | Privilegios especiales asignados a una nueva sesión | Detectar sesiones administrativas                         |
| 4688     | Procesos        | Nuevo proceso creado                                | ⭐ Analizar ejecución de malware y process tree            |
| 4689     | Procesos        | Proceso terminado                                   | Timeline y duración de procesos                           |
| 4697     | Servicios       | Servicio instalado                                  | ⭐ Posible persistencia                                    |
| 4698     | Scheduled Tasks | Tarea programada creada                             | ⭐ Posible persistencia                                    |
| 4699     | Scheduled Tasks | Tarea programada eliminada                          | Investigar posible limpieza de evidencias                 |
| 4700     | Scheduled Tasks | Tarea programada habilitada                         | Persistencia / ejecución                                  |
|          |                 |                                                     |                                                           |
|          |                 |                                                     |                                                           |
|          |                 |                                                     |                                                           |


|**4702**|Scheduled Tasks|Tarea programada modificada|⭐ Persistencia / modificación maliciosa|
|**4720**|Cuentas|Usuario creado|⭐ Persistencia / creación de cuentas|
|**4722**|Cuentas|Usuario habilitado|Actividad sobre cuentas|
|**4724**|Cuentas|Intento de restablecer contraseña|Posible compromiso de cuenta|
|**4728**|Grupos|Usuario agregado a grupo global|⭐ Escalada de privilegios|
|**4732**|Grupos|Usuario agregado a grupo local|⭐ Escalada de privilegios|
|**4740**|Cuentas|Cuenta bloqueada|Fuerza bruta / múltiples intentos|
|**4768**|Kerberos|Solicitud de TGT|Investigar autenticación en Active Directory|
|**4769**|Kerberos|Solicitud de Service Ticket|Kerberos / movimiento lateral|
|**4771**|Kerberos|Fallo de preautenticación Kerberos|Ataques contra credenciales|
|**4776**|Autenticación|Validación de credenciales|Investigar autenticaciones|

*Identificadores "importantes" para Elastic `event.code:####`*
	
	|**4624**|🟢 Login exitoso|
	|**4625**|🔴 Login fallido|
	|**4648**|🔑 Credenciales explícitas|
	|**4672**|👑 Privilegios especiales|
	|**4688**|⚙️ Proceso creado|
	|**4697**|🔧 Servicio instalado|
	|**4698**|⏰ Scheduled Task creada|
	|**4702**|⏰ Scheduled Task modificada|
	|**4720**|👤 Usuario creado|
	|**4728**|👥 Usuario agregado a grupo global|
	|**4732**|👥 Usuario agregado a grupo local|
	