***Contexto:*** El equipo de seguridad interceptó un email de phishing. Analiza las cabeceras, decodifica los adjuntos y extrae el payload malicioso.

Se nos comparte el comprimido del reto y dentro vemos un `README` veamos que dice.
![[Pasted image 20260401171702.png]]
Vemos que nos dice que se sospecha de que contiene un **payload malicioso** veamos.
![[Pasted image 20260401171836.png]]
Vemos que tiene un archivo vamos a traérnoslo para mirarlo mas de cerca.
`munpack suspicious_email.eml`

Dejándonos el archivo `Security_report.xls`donde vemos algo curioso.
![[Pasted image 20260401172253.png]]

Vemos que el archivo inyecta código pero no lo vemos bien dado a que esta encriptado en `Base64` vamos a descodificarlo.
`echo content.txt | base64 -d`
![[Pasted image 20260401173040.png]]

Vemos y observando vemos que la cadena `$enc = "7f03624c475...."` esta ofuscada con `XORG` y en la quinta linea vemos que se nos muestra la clave para desofuscar en `$k = 0x37`
usamos la pagina  [[https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://gchq.github.io/CyberChef/&ved=2ahUKEwie6evD0s2TAxWzQjABHbKuMEsQFnoECA0QAQ&usg=AOvVaw3cJhXGWs_4gKkmjmhQLSNC|CyberChef]] desofuscar la cadena `XORG`.
![[Pasted image 20260401175735.png]]
Y consiguiendo así la flag de este reto.