**Contexto**: Un equipo ha sido comprometido. Te entregamos un volcado de memoria. Encuentra el proceso malicioso y extrae la flag.

En este reto se nos da un volcado de memoria y un análisis del equipo comprometido 

![[Pasted image 20260401164129.png]]
Vemos que nos dan una lista de pasos unas pistas de donde esta la flag,
vamos por pasos 
1. Si leemos el análisis dado vemos que tenemos el nombre del proceso malicioso junto con su **PID 3156** *svc_update.exe*
2. Vamos ver el volcado de memoria...
   ![[Pasted image 20260401165124.png]]
   revisamos y vemos una cadena muy larga y algo rara y siguiendo los pasos buscamos una llave para este tipo de ofuscación conocida como `XOR` la cual requiere una key para desofuscar dicha cadena y si miramos el propio volcado nos esta dando la llave `xor_key: 0x5a`
3. 
   En este ultimo paso tomamos la cadena y la pegamos en esta pagina llamada [[https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://gchq.github.io/CyberChef/&ved=2ahUKEwie6evD0s2TAxWzQjABHbKuMEsQFnoECA0QAQ&usg=AOvVaw3cJhXGWs_4gKkmjmhQLSNC|CyberChef]], junto con la clave de `XOR` 
 ![[Pasted image 20260401165949.png]]
 