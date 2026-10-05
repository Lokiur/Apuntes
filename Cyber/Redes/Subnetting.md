
## *Conversión de binario a decimal*

| $2^7$ | $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 128   | 64    | 32    | 16    | 8     | 4     | 2     | 1     |
| x     | x     | 1     | 0     | 1     | 1     | 0     | 1     |
Se suman los valores para el obtener el resultado decimal donde haya un **1** dando como resultado:
$32+8+4+1 = 45$  Como numero decimal donde $101101binario = 45decimal$


Ahora intentemos pasar $78=decimal$

| $2^7$ | $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 128   | 64    | 32    | 16    | 8     | 4     | 2     | 1     |
| 0     | 1     | 0     | 0     | 1     | 1     | 1     | 0     |
Como resultado tenemos que $78 decimal = 01001110 binario$


### Subredes
Formula:
Se elevara el $2^x$ hasta que la potencia se **mayor o igual** a la cantidad de subredes requeridas.

*ejemplo* 
	$2^x=>c$     c = 5 subredes  $2^3=8 > 5$


Después de tener la formula resuelta procedemos a aplicarla en la Subnetmask 

%%Nota: Se usara una subnetmask de clase B, las subnetsmask ya subnettiadas no podrán ser nuevamente ser configuradas%%

Subnetmask(B)

| Bits        | 11111111 | 11111111 | 00000000 | 00000000 |
| ----------- | -------- | -------- | -------- | -------- |
| **Decimal** | $255$    | $255$    | 0        | 0        |
En el ejemplo anteriormente resuelto nos da que $2^3$ es el numero que ocupamos para hacer el Subnetting, aplicamos en la mascar de subred prendió 3 bits de la mascara obteniendo las mascara subnettiada   


| $2^7$ | $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 128   | 64    | 32    | 16    | 8     | 4     | 2     | 1     |
| 1     | 1     | 1     | 0     | 0     | 0     | 0     | 0     |


$11111111.11111111.11100000.00000000$
255.255.224.0


El prefijo de esta subnetmask %%sin subnneting%% es de prefijo **/16** pero como ahora esta modificada el prefijo cambiara sumándole los 3 bits encendidos de mas dando así un prefijo **/19**

#### Host

La formula para calcular el numero de ***Hosts*** disponibles es: 

$2^m-2=h$ 
donde $m$ es el numero de $0$ que quedaron adelante de los últimos bits encendidos del Subnetting

$11111111.11111111.11100000.00000000$
$255.255.224.0$

En este caso el numero de 0 despues del subnneting fueron 13 ceros 

$2^13-2$ = 8.190

En la formula se restan dos por echo de que se debe dejar un campo para broadcast y de red 

#### Salto de red

$256-224=32$ 
Cada 32  hay un red 