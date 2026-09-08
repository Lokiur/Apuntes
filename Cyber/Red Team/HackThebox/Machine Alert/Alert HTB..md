Notas/Writeup by lokiur 
IP  10.10.11.44
1 ENUMERACION 
![[Pasted image 20250322134926.png]]
	Usamos nmap para empezar la enumeración de puertos y servicios.
	![[Pasted image 20250322135339.png]]
	Este es nuestro segundo escaneo de puertos en los cuales se observa dos
	servicios. 
	 Miramos la web de la maquina pero al entrar somos redireccionados a "Alert.htb"
	 ![[Pasted image 20250322135843.png]]
	 Contemplamos en el /etc/hosts el dominio " ip de la maquina victima Alert.htb" 
	 ![[Pasted image 20250322140030.png]]
	 Así viendo la pagina Web.
	 Vemos un capo de subida en la parte inicial mas tarde miremos esa parte.
	Usamos gobuster en búsqueda de contenido oculto en la pagina.
	
![[Pasted image 20250322153619.png]]
	Miramos los contenidos pero nos arroja error 403 "no estamos autorizados para entrar"
	Haciendo un segundo escaneo con "FUZZ" pudimos dar un con una ruta:
	![[Pasted image 20250322155858.png]]
	La contemplamos en el /etc/hosts/ observando un panel de login en el cual no podemos hacer nada por la falta de credenciales.![[Pasted image 20250322160016.png]]
	


2 . XSS ATTACK 

Mirando mas en detalle el campo de subida de archivos vemos de que es un campo que admite archivos con terminación .md hacemos una prueba simple para ver si tenemos el vector de ataque XSS.
	Creamos un archivo .md con el siguiente contenido:
	![[Pasted image 20250322154029.png]]
Vemos de que al cargar el archivo .md nos arroja un "ALERT"  
	 ![[Pasted image 20250322154334.png]]
 