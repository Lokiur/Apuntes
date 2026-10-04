![[Pasted image 20260912175250.png]]

|**Ruta**|**Descripción**|
|---|---|
|`/`|El directorio de nivel superior es el sistema de archivos raíz (root filesystem) y contiene todos los archivos necesarios para arrancar el sistema operativo antes de que se monten otros sistemas de archivos, así como los archivos necesarios para arrancar los otros sistemas de archivos. Tras el arranque, todos los demás sistemas de archivos se montan en puntos de montaje estándar como subdirectorios de la raíz.|
|`/bin`|Contiene binarios de comandos esenciales.|
|`/boot`|Consta del gestor de arranque estático, el ejecutable del kernel y los archivos necesarios para arrancar el SO Linux.|
|`/dev`|Contiene archivos de dispositivo para facilitar el acceso a cada dispositivo de hardware conectado al sistema.|
|`/etc`|Archivos de configuración del sistema local. Los archivos de configuración de las aplicaciones instaladas también pueden guardarse aquí.|
|`/home`|Cada usuario del sistema tiene un subdirectorio aquí para su almacenamiento.|
|`/lib`|Archivos de bibliotecas compartidas que son necesarios para el arranque del sistema.|
|`/media`|Aquí se montan los dispositivos de medios extraíbles externos, como las unidades USB.|
|`/mnt`|Punto de montaje temporal para sistemas de archivos regulares.|
|`/opt`|Aquí se pueden guardar archivos opcionales, como herramientas de terceros.|
|`/root`|El directorio de inicio del usuario root.|
|`/sbin`|Este directorio contiene ejecutables utilizados para la administración del sistema (archivos binarios del sistema).|
|`/tmp`|El sistema operativo y muchos programas utilizan este directorio para almacenar archivos temporales. Este directorio generalmente se vacía al arrancar el sistema y puede ser eliminado en otros momentos sin previo aviso.|
|`/usr`|Contiene ejecutables, bibliotecas, archivos man, etc.|
|`/var`|Este directorio contiene archivos de datos variables como archivos de registro (log files), buzones de correo electrónico, archivos relacionados con aplicaciones web, archivos cron y más.|
