# Tutorial del juego Chain Reaction

Para los que no saben jugar Chain Reaction aquí tienen un tutorial de como jugarlo en Delta Chat.

* El juego tiene lugar en un tablero de 9 filas y 6 columnas.
* Todas las celdas están inicialmente vacías. Los jugadores se turnan para poner "átomos" de su color correspondiente. Cada jugador puede poner un átomo por turno
  en una celda vacía o una celda que ya contenga uno de los átomos de su color. Cuando colocas un átomo en una celda donde ya tenías un átomo ocurre una reacción
  química y ambos átomos se fusionan creando así un nuevo tipo de átomo con otro color y mayor masa. 
* Cada celda en el tablero admite hasta cierta masa crítica igual al número de celdas adyacentes en las 4 direcciones (arriba, abajo, izquierda y derecha). Por
  ejemplo, la masa crítica es 4 para celdas que no toquen un borde del tablero, 3 para celdas en los bordes y 2 para celdas en las esquinas. 
* Cuando un átomo alcanza la masa crítica que soporta la celda donde se encuentra, la alta presión hace que explote, dividiéndose en varios átomos que son
  expulsados hacia las celdas adyacentes. A su vez, la explosión podría sobrecargar otras celdas adyacentes y producir una reacción en cadena de explosiones
  (de ahí viene el nombre del juego). 
* Cuando ocurre una explosión si una celda adyacente contenía un átomo del enemigo, este se fusiona con el nuestro aumentando su masa y pasando a ser nuestro. 
* La masa de cada átomo se sabe por el color del mismo: 
  - Jugador 1: rojo = 1   naranja = 2   amarillo = 3 
  - Jugador 2: verde = 1   púrpura = 2   azul = 3 
* Objetivo del juego:  
    - El jugador 1 representa al calor, cada vez que fusiona átomos estos se vuelven más calientes hasta explotar en una ola de calor calentando a los átomos
      adyacentes. El jugador 2 al contrario representa el frío creando átomos cada vez más gélidos hasta explotar en una nova de escarcha que congela a los átomos
      adyacentes. 
    - El objetivo de cada jugador es absorber todos los átomos de su oponente, si en algún momento un jugador se queda sin átomos en el tablero, su energía se
      extingue y pierde. 
* ¿Cómo jugar?  
    - Para invitar a un amigo a jugar le envías al bot **games@echedeylr.tk** el comando: `/chr_play miAmigo@nauta.cu`  donde en lugar de `miAmigo@nauta.cu`  debes
      poner el correo del amigo que deseas invitar a jugar. 
    - Para colocar un átomo envías un mensaje con las coordenadas de la casilla donde lo quieres colocar, por ejemplo:  `b2` para colocar un átomo en la fila B
      columna 2.
