**Contexto**: El servidor web fue atacado. Analiza los logs de acceso de Apache para identificar al atacante y el tipo de ataque utilizado.

En este reto se nos comparte un `.zip` 
![[Pasted image 20260401121820.png]]
dejándonos 2 archivos `.log` y un `README.txt`, leemos el `README` 
![[Pasted image 20260401122758.png]]

Viendo que la flag y lo que buscamos esta en entre `H4U{...}`
usando simplemente `Grep` y algunas expresiones regulares pues podemos encontrar esta flag [... , * ? ] %% algunas expresiones regulares  %%
![[Pasted image 20260401123050.png]]
Cambiamos los caracteres URL Encodeados dando así  `H4U{Bsql_inj3c10n_1n_l0gs}`

Fin :)