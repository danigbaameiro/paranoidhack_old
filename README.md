# FASE 0: Ocultación

> This is a repository to provide documentation on anonymity.

## Importancia

Nuestra vida avanza y la sociedad en cierto modo nos presiona para hacer uso de la tecnología. Actualmente resulta dificil conocer a un pariente cercano que no haga uso de un dispositivo móvil o de un ordenador. Dicha tecnología crece de forma exponencial, lo cual provoca que cada vez interactuemos más con ella. Es esta interación la que facilita la identificación y recolección de información sobre nuestros hábitos, gustos, opiniones, … Sobre todo nuestro ser.

La tecnología va adentrandose más y más en nuestras vidas hasta llegar al punto de situarse dentro de lo personal. Hemos permitido que puedan conocer nuestros hábitos, nuestros gustos, nuestros ideales e incluso nuestras opiniones.

Sin darnos cuenta hemos pasado de impedir que desconocidos puedan acceder a nuestros hogares a dejarles abiertas las puertas de par en par... Y todo porque no nos percatamos de su presencia. Internet es un gran amigo, pero un gran amigo insvisible a través del cual pueden controlar toda nuestra vida.

Puede que en tiempos pasados pudieramos refugiarnos en el descontrol y el caos… Los tiempos cambian, y al igual que las grandes corporaciones, las agencias y nuestro gran amigo y vecino el cracker se adapta, debemos hacerlo nosotros también.

Muchos paises ya han considerado el ciberespacio como la quinta dimensión en cuestión de riesgos para la seguridad nacional. Para quien no lo sepa, estan las dimensiones del mar, tierra, aire, espacio y ahora… El ciberespacio.

Si bien es cierto como comentan algunos si seguimos una ética correcta, todo es seguro. Si no tocas es que no tiene ningún fallo…

Dejemonos de ser unos ilusos. Dejemos de estar dormidos. Despertemos. Preocupemonos por nuestra seguridad. Por la seguridad de quienes nos rodean. 

Es el momento de marcar un antes y un después. Es el momento de demostrar que sabemos adaptarnos a esta sociedad sin ser deborados por ella. 


## Dirección MAC

### ¿Qué es?
La  dirección MAC es una identificador único a nivel mundial por cada dispositivo formado por 48 bits (6 bloques de dos caracteres hexadecimales (4 bits)) que permite identificar la totalidad de dispositivos de red tales como las tarjetas de red.

Normalmente los fabricantes una vez tienen montado el hardware, vease una tarjeta de red, graban en formato binario en una memoria ROM del dispositivo la dirección MAC. Dicha memoria es de solo lectura, lo cual imposibilita poder modificarla directamente en la ROM.

Según lo anterior no podemos modificarla. Cabe destacar que lo que no podemos modificar es directamente la MAC que tenemos almacenada en la ROM. Entonces… ¿qué podemos modificar?Al arrancar el sistema se carga una copia de la dirección MAC en nuestra memoria RAM. En este caso, lo que podemos hacer es modificar la dirección MAC que esta almacenada en la RAM. Dicha dirección será la usada en todas las acciones donde se precise su uso. 


### Estructura
Anteriormente habiamos mencionado que la dirección MAC es un identificador único a nivel mundial por cada dispositivo. Estos identificadores tienen una entidad que regula unas normas de marcado. Dicha entidad es el IEEE (Instituto de Ingenierí Eléctrica y Electrónica).

Una dirección MAC tiene el siguiente formato:
*40:AF:E5:F5:FE:50*

Debemos centrarnos principalmente en dos partes:

* Por un lado tenemos la primera parte, el lado izquierdo, el cual consta de 3 bloques. Dicho lado identifica quien es el fabricante del hardware. Esto quiere decir que si en nuestra red vemos una dirección MAC que empieza por *40:AF:E5* esta pertenecerá a Sawyer Technologies.

* La segunda parte, la de la derecha, consta también de 3 bloques. Esta parte del código es el número de serie que identifica el dispositivo fabricado. El fabricante puede usar el número de serie que quiera pero con la condición que únicamente puede usar el mismo número de serie una vez. Es decir, los 3 últimos bloques deben ser únicos para un único dispositivo. Si se fabricase otro no debe poder usar la terminación *F5:FE:50*.


### Usos de la dirección MAC
1.- La dirección Mac de una tarjeta de red la podemos utilizar para que nuestro Router asigne una IP estática a nuestro ordenador.

2.- Poder filtrar por MAC en nuestra red de tal forma que solo puedan acceder a ella las MACs que hayamos especificado.

3.- Como hemos mencionado antes la dirección Mac puede servir para identificar a un equipo o usuario dentro de una red informática. Usando Nmap (`nmap -sP <dirección IP>`) o NACC por ejemplo podemos obtener fácilmente las IP y las Mac Address de los equipos conectados a la red.

4.- Nuestro teléfono móvil con la red Wifi activada tiende a preguntar a los diferentes routers si estan activos. Dicha “pregunta” hace reflejar nuestra dirección MAC. Recordemos que nuestra dirección MAC es una dirección única.

5.- Hay proveedores de Internet que requieren Autenticación MAC para proporcionar internet a sus clientes.

6.- Si estamos en una red y somos los únicos con un dispositivo de la marca Apple, claramente se sabrá a quien pertenece dicho ordenador dentro de un establecimiento o local.


### Modificación de la dirección MAC
Hagamos pie en que la dirección MAC es una dirección única que se le da a nuestro dispositivo y que este dispositivo puede hacer uso de ella siendo visible para otros usuarios.

#### ¿Cómo se modifica una dirección MAC?
Hay varias formas y programas para realizar dicha modificación. El más comunmente usado es (https://github.com/alobbs/macchanger macchanger ), disponible en nuestra distribución Parrot. 

A continuación veremos una forma fácil de cómo se hace dicha modificación sin el uso de herramientas:

> Ejecutando ifconfig podremos ver nuestras diferentes redes. Por ejemplo, un nombre comunmente usado es el de la red ethernet eth0. En el lado izquierdo de la respuesta dada al comando ifconfig podremos ver los nombres.


Lo primero que deberemos hacer es deshabilitar la tarjeta de red a la cual vamos a cambiar la dirección MAC:
`ifconfig <nombre de red> down`

A continuación modificamos la MAC de dicha tarjeta por la que queramos:
`ifconfig <nombre de red> hw ether 00:00:00:00:00:00`

> Normalmente en lugar de *00:00:00:00:00:00* se suele hacer uso de direcciones MAC existentes provenientes de bases de datos que circulan por la red. No es muy dificil acceder a dichas bases de datos.

Finalmente volvemos a arrancar de nuevo la tarjeta de red que habiamos deshabilitado:
`ifconfig eth0 up`


Con estos sencillos pasos se habrá modificado la dirección MAC. Podremos comprobar el cambio ejecutando ifconfig. Si nos fijamos en la interfaz de red que se deseó cambiar, esta deberá tener una dirección MAC diferente a la original.

> En algunos lugares se puede considerar ilegal la modificación de la dirección MAC.

