# Bloque 3: Analisis de llamadas de un call center

Como ejemplo, puedes utilizar el audio (mp3) de este repositorio. Pero verás que podríamos aplicar estos dos pasos a cualquier otro audio que tengas y quieras analizar, o que puedes grabar el audio en el Speech Studio directamente con tu micrófono. 

![Diagrama de Solucion con Speech to text y OpenAI](Bloque3.png)

Antes de empezar, recuerda que:

* Tienes que descargarte el audio de ejemplo (u otro) a tu PC local y tenlo a mano porque vamos a transcribirlo a texto con Azure Speech-to-text. 
* Necesitarás un recurso Azure Speech creado, y deberás tener acceso a él
* Necesitarás también acceso a OpenAI, sea Azure OpenAI (en una subscripcion de Azure) o OpenAI en abierto 
___

## Parte 1 - Transcribir audio (Speech-to-text)

En este apartado deberás ir al servicio de Azure Speech Studio y transcribir el audio a texto:

Para ir al Speech Studio, la url es [https://speech.microsoft.com/](https://speech.microsoft.com/)
* Haz login con tus credenciales de Azure
* Selecciona el recurso sobre el que vamos a hacer las peticiones
* Usando la funcionalidad "Real-time Speech-to-text", selecciona como idioma el Español, sube el audio que tienes en tu PC, y verás que se empieza a transcribir a texto. Puedes ir oyendo el audio mientras se va transcribiendo a texto. 
* Una vez haya terminado la transcripción, copia el texto que aparezca como resultado. 
* Verás que tenemos el JSON y más opciones de consumo de los modelos, pero para este caso lo vamos a mantener tan sencillo como copiar el texto directamente.  

Usaremos ese texto en la Parte 2


<details>
  <summary>:white_check_mark: Ver solución:</summary>

* Texto que extraemos con Speech-to-text del audio de ejemplo:

  ```    
  ¿Hola Santiago, cómo estás? Te habla Andrés, asesor comercial y encargado de tu servicio telefónico. ¿Cómo estás bien? Gracias. No, no. Estoy interesado, muchísimas gracias. Mira Santiago, el motivo de mi llamado es breve y es para darte un beneficio hasta el 7% en tu factura del móvil en los que solo te tomará 3 minutos. Santiago Mira, el beneficio consiste en hacer una portabilidad o cambio de tu servicio. En el cual debes estar pagando 60 y casi 70000 pesos. ¿Vas a pagar solamente 65500 mensuales, que te parece interesante, verdad? ¿Pues es que yo ya estoy bien, sin embargo, podrías estar mejor? Santiago mira, el ahorro es casi de 5000 pesos al mes en el año son 60000 pesos que puedes invertir en otras necesidades y no solo el beneficio económico, sino que vas a tener una cobertura mejor, más datos para navegar es una oferta, gana gana, solo solo es solo para algunos clientes como tú. ¿Los beneficiados son pocos y tienes que aprovecharlo, pues por el día de hoy qué te parece? Pues tal vez sí, tal vez sí me interesa la oferta, pero es que no tengo tiempo, pues de ir a oficina o hacer el trámite, no te preocupes por el por el trabajo, me quedaba poco tiempo libre. Entonces no sé, muchísimas gracias. Igualmente entiendo Santiago, no te preocupes, mira todo, es muy sencillo, yo me encargo por acá de hacerlo todo telefónicamente, lo único que necesito es que me digas que estás interesado en ahorrar, en mejorar tu servicio y yo lo transmito todo por acá en 4 minutos. Sí, no es que lo que pasa es que en ese momentico estoy en el bus y pues no me gusta dar datos así por teléfono. ¿Además que además que no sé si es una estafa, ya entiende, no? ¿Sí, sí entiendo Santiago tu posición, mira para tu tranquilidad, te voy a dar mi extensión, sí como asesor Ejecutivo de me llamas es la línea de Atención al Cliente oficial que tenemos aquí en el cuál Center me vas a llamar y pides hablar conmigo sí, EH? Son solo 5 minutos y con esos 5 minutos vas a mejorar tu servicio durante todo el año. Chévere, no. ¿Eh? ¿Ok una pregunta, cuántas megas voy a tener mi gigas? Vas a tener más de cuatro gigas que tienen, ajá, claro, vas a tener más de 40 gigas para redes sociales, chat de navegación ilimitado para todo lo que desees. Ah, y minutos ilimitados nacionales y 20 minutos mensuales para Venezuela. Ah, bueno, listo. Sí, sí, sí, me interesa la oferta. Ah, bueno le llamo listo, bueno, Santiago mira, son las 4:55 h kg máximo de las 5:20 h, espero tu llamada, OK, si no es molestia y si no me puedes llamar, pues te estaré devolviendo la llamada para poderlo confirmar y para que puedas tomar el beneficio. ¿Te parece listo? ¿Una cosa es que yo me tengo que bajar ya, casi voy a llegar a pues a mi destino, Eh? ¿Una pregunta, Eh? La oferta es limitada, o sea, corre el riesgo de perderlas y me demoro mucho en llamarle, si bueno, no, sí a las 5:20 H, Podemos establecer esa comunicación máximo 5 y 30, yo te aseguro que te la puedo mantener. Y esta bueno, bueno ya ya, gracias por tu tiempo, hablamos más tarde de Santiago Chao, OK, muy bien Andrés, hasta luego. 

  ```

</details>

___

## Parte 2 - Diseño de prompt de analisis de la transcripcion

En esta parte, una vez hayamos extraido el texto del documento, vamos a utilizar Azure OpenAI para 3 tareas. Intenta crear un prompt para cada una de ellas, y experimenta con diferentes variantes. En la parte de "Ver Solucion" tienes algunos ejemplos. 

```
Prompt 1: Extraer información simple (por ejemplo, intención de la llamada, partes involcradas, oferta realizada, plazo de respuesta de aceptacion de la oferta etc. 
```

```
Prompt 2: Extraer información en JSON (pídele los mismos datos del Prompt 1, pero en formato muy concreto en JSON)
```

```
Prompt 3: Preguntar algo concreto para ver si sabe responder sobre la conversacion.
```

<details>
  <summary>:white_check_mark: Ver solución:</summary>

* Extraer información
  ```
  Extrae el importe mensual a pagar de este contrato, dime si se aceptan mascotas, y el numero de clausulas que incluye. 
  
  Contrato a analizar: <texto extraido con forms recognizer>
  ```
  
* Extraer información en JSON
  ```
  Extrae la siguiente información del contrato que te voy a pasar: 
  
  1. el importe mensual a pagar de este contrato (clave: mensualidad)
  2. si se aceptan mascotas (clave: mascotas)
  3. el numero de claúsulas que incluye el contrato (clave: clausulas)
  
  Devuelveme un JSON con los campos dentro de un objeto "contrato". 
  
  Contrato a analizar: <texto extraido con forms recognizer>:
  ```
  
  Completion esperado:
  ```
  {
  "contrato": {
    "mensualidad": 1000,
    "mascotas": "prohibido",
    "clausulas": 6
  }
  }
  ```
 

</details>

___
