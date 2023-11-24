





## Integrantes

[Gaabyu](http://github.com/Gaabyu) 

[ZiggPunk](http://github.com/ZiggPunk)

[Martina-Flores](http://github.com/Martina-Flores)

[eolicce](http://github/eolicce)

## Codigo

https://github.com/ZiggPunk/Atari-Breakout-por-comandos-de-voz/blob/main/Código


## Introducción

Este proyecto utiliza el reconocimiento de voz a través de un micrófono para traducir las palabras habladas en comandos precisos; permitiendo a su vez, controlar y dirigir la barra del clásico juego Atari Breakout sin la necesidad de un teclado o mouse. 
El control por voz es posible gracias al uso del software Arduino, el microcontrolador “Arduino 33 nano BLE” y la biblioteca de código Cyberon, los cuales en conjunto convierten la experiencia de juego en algo completamente nuevo, eliminando las barreras físicas y permitiendo que la voz sea su herramienta principal.

## Instrucciones de uso

Iniciar Google Atari Breakout.
Activar el reconocimiento de voz del controlador diciendo “Oye placa”.
Seguidamente decir “Izquierda” o “Derecha” según la dirección que quieras mover la barrita del juego.
También existe la posibilidad de decir “Arriba” o “Abajo” para mover el cursor hacia el ícono de pausa o cerrar el juego diciendo la palabra “Detente”.
Disfrutar de la experiencia.

## Materiales:

- Arduino 33 nano BLE

- Mouse USB

- Monitor

- Voz

- Arduino IDE 2.2.2

- Google Atari Breakout

- Cyberon


## Procedimiento

Primeramente obtuvimos el número de serie de la placa mediante a la descarga de una librería que trae consigo un boceto el cual se sube al arduino, en el monitor serial aparecía nuestro número de serie, esto con el objetivo de obtener una licencia del programa.

En el software completamos con la información de nuestra placa y pulsamos enviar, lo que nos dio una serie de números que posteriormente se colocaron en el ejemplo de Cyberon. Vamos hasta el ejemplo “Voice Recognition” y se reemplazan los valores por los números de la licencia.

El ejemplo estaba listo para usar, sin embargo quisimos personalizar los comandos, para esto nuevamente completamos los datos de nuestra placa en Cyberon y creamos un nuevo proyecto. Para configurar el nuevo registro, colocamos una palabra que coloca al arduino en “trigger state”,  la cual es “Oye placa”, después creamos una lista de comandos que resolverán tareas en el boceto.
Al finalizar este proceso obtuvimos los archivos encabezados que nos servirán en nuestro proyecto, lo copiamos y colocamos en la carpeta de nuestros bocetos.
Reemplazamos los antiguos archivos encabezados por los nuevos.

Al tener funcionando este código indagamos la forma de activar el teclado mediante comandos de voz usando el ejemplo anterior sin embargo nos encontramos con la limitante de que la versión de placa actual no permite emular la presión de una tecla.
Posteriormente concordamos la decisión de adaptarlo a las coordenadas del cursor del mouse (izquierda y derecha), para ello modificamos el código actual de reconocimiento de voz insertando parte del código dispuesto en el ejemplo de mouse que viene incluido en el arduino. Esto con la finalidad de mover el cursor una cierta cantidad de pixeles al reconocer las palabras que ingresamos en el modelo de Cyberon.





## Referentes:
- Silithur, streamer español que logró completar el juego “Dark Souls” con comandos de voz.
https://www.youtube.com/watch?v=JNqf_zTjdNY 
- Bob Hammel (https://github.com/rhammell) , programador que desarrolló un proyecto de un mando para jugar videojuegos mediante comandos de voz para gente con movilidad reducida.






## Conclusiones
- Nos costó instalar las librerías de Cyberon en un principio, principalmente por reemplazar el archivo de la licencia por la id en header.
- En un primer momento no nos funcionaban las librerías de “Keyboard.h” y descubrimos que el arduino Nano 33 BLE es incompatible debido a diferencias en la arquitectura del hardware y en la capacidad de emulación USB. Esta tiene una arquitectura ARM Cortex-M4, mientras que las librerías mencionadas anteriormente están diseñadas para placas basadas en el chip Atmel AVR.

![imageia2](https://github.com/Gaabyu/audiv027-2023-2/assets/128186062/af887bf5-dc33-424f-abd2-03fee3407355)

  
- Lo anterior lo solucionamos con los ejemplos USB HID (Human Interface Device) incluidos en el microcontrolador, que tienen una librería modificada llamada “USBKeyboard.h”
- Los comandos de voz deben ser intuitivos para una persona que lo ocupa por primera vez (“izquierda”, “derecha”).
- Tuvimos un pequeño problema donde las funciones de “keyboard” daban error, pero fue por no especificar las variables al inicio del código.
- Intentamos usar teclado originalmente con la librería “USBKeyboard.h”, pero las funciones que posee no permiten emular la presión de una tecla, sino que escriben los caracteres, intentamos con diversas funciones como: “Keyboard.press”, “keyboard.printf”, keyboard.key_code”, “keyboard.putc”.
- Para resolver lo anterior usamos la librería “USBMouse” para controlar el juego mediante el mouse, ya que esta librería permite mover el mouse libremente hacia las coordenadas ingresadas.

![imageia1](https://github.com/Gaabyu/audiv027-2023-2/assets/128186062/688aafa0-7ec1-405a-9e52-65b558dc465c)
  
- Cabe mencionar que cambiamos nuestro juego “Arkanoid”, por “BreakOut”. Es el mismo juego, pero “BreakOut” es el original lanzado en la Atari en 1976, mientras que el otro es una versión posterior de la NES. Aunque el motivo principal es que este tiene una versión web de Google, lo que resulta mucho más sencillo y cómodo para realizar y demostrar el proyecto.




## Links: 

- Mando para jugar videojuegos con comandos de voz https://www.hackster.io/rhammell/voice-enabled-video-game-controller-c76200
  
- Proyecto joystick con una sola mano
 https://forum.arduino.cc/t/nano-33-ble-as-usb-gaming-keyboard/1054091
 
- Breakout juego
 https://elgoog.im/breakout/

- Voice Recognition
 https://docs.arduino.cc/tutorials/nano-33-ble-sense/speech-recognition-engine

- Licencia
https://tool.cyberon.com.tw/ArduinoDSpotterAuth/FDMain.php

- Funciones 
https://www.arduino.cc/reference/en/ 
