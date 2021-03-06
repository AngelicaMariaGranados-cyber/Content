Damas y caballeros, prepárense.  
El tema de esta semana es:  

#Arduino

Arduino es una plataforma de hardware y software de fácil manejo basada en microcontroladores AVR. Esta vez dejaremos la teoría un poco de lado, puesto que estoy casi seguro de que ya quieren empezar.

####Pues entonces, empezemos.

Existen 2 funciones básicas:

***Void loop*** y ***void setup***  

En el *void setup* ponemos aquello que deseamos que solo ocurra una vez cada vez que se resetee al arduino, mientras que en el *void loop* colocamos aquello que deseamos que se repita mientras el arduino esté funcionando.

Si lo queremos asimilar mejor, un ejemplo no cae mal. Si deseas fotocopiar una página 50 veces, ¿cuántas veces prendes la impresora? Correcto, entonces eso iría en el void setup, solo necesitamos que pase una vez. Pero la acción de fotocopiar si necesitamos que se repita hasta cumplir su objetivo. Entonces nuestro programa quedaría más o menos así:

```ino
void setup()  
{  
    encender la impresora  
}  
void loop()  
{  
fotocopiar hasta tener las 50 copias  
}  
```

Entonces ahora veremos algunas otras sentencias usadas frecuentemente:

***Declarando variables***  

Las variables pueden entenderse como contenedores específicos, como los cajones para la ropa y los recipientes para comida. ¿Se te ocurre guardar sal en el recipiente del azúcar? Exactamente. No puedes guardar un dato en una variable que no le corresponda. Por ejemplo, en una variable de tipo **int** solo pueden entrar números enteros, es decir que no podremos guardar valores como **"12,5"** (con coma decimal), pero sí valores como **12** y **13** (números enteros).

Los nombres de las variables no deben de comenzar con un número ni tener espacios, y de preferencia deben de tener un nombre reconocible.  

Ejemplos:  

int promedio;  

float temperatura;  

boolean estado;  

char datoIngresado;  

...

***pinMode(pin, Mode)    -se usa en el void Setup*** 

¿Recuerdas que los pines digitales podían ser configurados como entradas y como salidas? Esta es la sentencia encargada de hacerlo. Si quieres que un pin sea salida, lo declaras como OUTPUT (siempre en mayúsculas), y si quieres que sea entrada, como INPUT. 

**Ejemplo**  

```ino
pinMode(13, OUTPUT) // declaramos el pin 13 como salida  
pinMode(5, INPUT) // declaramos el pin 5 como entrada
```

***digitalWrite(pin, value)***  

Puedes enviar (escribir) 5V o 0V desde un pin declarado como salida. 

**Ejemplo**
  
```ino
digitalWrite(13, HIGH) // escribimos un 1 lógico (5V, led encendido)  
digitalWrite(13, LOW)  // escribimos un 0 lógico (0V, led apagado)
```

***digitalRead(pin)***   

Lee el valor en un pin declarado como entrada. Recibe 2 valores: HIGH y LOW 

Ejemplos:  

```ino
digitalRead(5) //si lee un valor cercano a 5V en el pin, devuelve HIGH, si recibe menos, un valor cercano a los 0V, devuelve LOW
```

***analogRead(pin)***   

Lee un valor en uno de los pines analógicos (A0-A5) y lo devuelve como un entero entre 0 y 1023. 

Ejemplos:  

```ino
int dato;
dato = analogRead(A0) // almacena un valor entre 0 y 1023 según el voltaje en el pin.
```

***analogWrite(pin, value)***  

Escribe un valor de PWM (permite variar intensidad) entre 0 y 255, siendo 255 toda la intensidad y 0 ninguna. (ejemplo, el brillo de un led).  

Ejemplo:  

```ino
analogWrite(9, 250); // el led brilla casi a su 100%  
analogWrite(9, 127); // el led brilla a su 50%  
analogWrite(9, 10);  // el led casi no brilla   
```

***delay(milisegundos)***  

Detiene el Arduino por una cantidad de milisegundos.  

Ejemplo:   

```ino
digitalWrite(13, HIGH); // encender un led
delay(500);             //esperar medio segundo
digitalWrite(13, LOW);  // apagar el led
delay(500)              // esperar medio segundo
```

***map(variable, A, B, C, D)***  

Escala la variable de A a B a un rango de C a D. Por ejemplo, al mover un potenciómetro, tenemos una variación de 0 a 1023, pero PWM necesita variación de 0 a 255. 

Entonces mapeamos:  

```ino
valorPWM = map(valorPotenciometro, 0, 1023, 0, 255) // convierte la variación de 0 a 1023 a una variación de 0 a 255
```

***Estructuras de control***

Aquí tenemos a los clásicos **for**, **while**, **if**, **switch** y similares.
Usamos el if para tomar desiciones en función a un enunciado. Si este es verdadero, se ejecuta lo que se  encuentra dentro del "if". Caso contrario, se ejecuta el código dentro del "else"  

```ino  
if(condición)  
{  
    //acciones A 
}    
else  
{  
    //acciones B
}
```

el for nos permite repetir un conjunto de instrucciones una cantidad determinada de veces

```ino
for (int i=0; i <= valor máximo; i++)    
{  
      //acción a repetir  
}   
```

el switch nos permite seleccionar un caso en función a una variable  

```ino
switch(case)  
{  
    case a: acción A  
    break;  
    case b: acción B  
    break;  
    .  
    .  
    .  
    default: break; // el default es aquel caso que ocurre cuando ninguno anterior es seleccionado  
}  
```

el while es aquel ciclo que se repite mientras una condición es verdadera

```ino
While(condición)  
{  
    //acción a repetirse  
}  
```

...***y esas son las funciones básicas que usaremos. Si desean indagar más, pueden buscar en las referencias de arduino, en su página oficial, <http://arduino.cc/en/Reference/HomePage>***


***ALGO IMPORTANTE:**

Si vas a conectar leds, no olvides ponerles una resistencia entre el led y el pin de salida (de 220 ohm o según colores, rojo rojo marrón; o una de 330, naranja naranja marrón). Conectar el led solo puede causar que se queme, excepto por el pin 13, que tiene una resistencia interna

 pin de salida Arduino]-----(RESISTENCIA)--------[LED]----[GND o tierra del Arduino

## Ejercicios

Pon a prueba tus habilidades de programación con estos ejercicios. Algunos están sencillos, otros no tanto... ¡escoge los 4 que más te gusten y experimenta!

1) Haz parpadear un led

2) Varía la intensidad de brillo de un led mediante un potenciómetro

3) Parpadear un led MIENTRAS se presiona un botón. Al soltarlo, debe dejar de parpadear

4) Variar la intensidad de un led de manera que vaya de menos a más y se reinicie

5) Variar la intensidad de un led de manera que vaya de menos a más, y luego de más a menos.

6) Hacer un juego de luces con 4 leds (la secuencia puede ser como deseen)

7) Hacer un juego de luces con 4 leds (la secuencia debe ser (según posición) "1, 2, 3, 4, 3, 2, 1")

8) Cada vez que se presiona un botón, se incrementa un contador, y un led se prende cada número par.






