Contexto: Hemos capturado tráfico de red sospechoso. Analiza el `archivo.pcap` y encuentra las credenciales filtradas.

`archivo.pcap` registros de logs de red

Estos archivos se pueden abrir con "WhireShark" [`wireshark archivo.pcap &`] [Linux]

O también podemos listar las cadenas imprimibles del archivo usando `strings`

![[Pasted image 20260401114937.png|697]]

Vemos el trafico que se hizo y reconstruimos la comunicación que se hizo y mirando a detalle vemos que una filtración de credenciales en el paquete N.º 4
![[Pasted image 20260401115335.png]]
Vemos un `user=admin&pass=H4U%7Bpcap_cr3d3nt14ls_in_cl34r%7D`
y pues solamente cambiamos las partes URL Encodeadas que son  
[%7B =] { 
[%7D =] }

Dando así la flag de este reto `H4U{pcap_cr3d3nt14ls_in_cl34r}`


