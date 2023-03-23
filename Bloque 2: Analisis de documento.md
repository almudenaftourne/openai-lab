# Bloque 2: Analisis de un contrato

Como ejemplo, puedes utilizar el pdf del contrato de ejemplo de este repositorio. Pero verás que podríamos aplicar estos dos pasos a cualquier otro documento que tengas y quieras analizar con OpenAI.

Antes de empezar, recuerda que:

* Tienes que descargarte el pdf de ejemplo (u otro) a tu PC local y tenlo a mano porque vamos a extraer el texto plano usando Azure Form Recognizer. 
* Necesitarás un recurso Azure Form Recognizer creado, y deberás tener acceso a él
* Necesitarás también acceso a OpenAI, sea Azure OpenAI (en una subscripcion de Azure) o OpenAI en abierto 
___

## Parte 1 - Diseño de prompt simple

En este apartado deberás ir al servicio de Forms Recognizer y extraer texto del contrato de alquiler:

Para ir a Forms Recognizer, la url es [https://formrecognizer.appliedai.azure.com/studio](https://formrecognizer.appliedai.azure.com/studio)
* Haz login con tus credenciales de Azure
* Selecciona el recurso sobre el que vamos a hacer las peticiones
* Usando el modelo Layout o Read, sube el pdf del contrato que te has descargado a local, y pincha en "Analyze". Copia el texto que aparezca en la derecha. 
* Verás que tenemos el JSON y más opciones de consumo de los modelos, pero para este caso lo vamos a mantener tan sencillo como copiar el texto directamente.  

Usaremos ese texto en la Parte 2


<details>
  <summary>:white_check_mark: Ver solución:</summary>

* Texto que extraemos con Forms Recognizer
  ```
    
  CONTRATO DE ARRENDAMIENTO DE VIVIENDA

  En Bilbao a 31 de marzo de 2023

  REUNIDOS

  De una parte,

  Don/Doña Gregorio Marañon, mayor de edad, de nacionalidad española, con domicilio en Calle de Bernarda 25 y DNI/ PASAPORTE/ NIE número 123456K y cuya fotocopia del mismo queda incorporado como Anexo al final de este contrato. Actúa en su propio nombre y representación,

  (en adelante, el/los "Propietario/s").

  De otra parte,

  Don/Doña Manuela Malasaña, mayor de edad, de nacionalidad española, con domicilio en Calle del Agua 123 y DNI/ PASAPORTE/ NIE número 9876543N y cuya fotocopia del mismo queda incorporado como Anexo al final de este contrato. Actua en su propio nombre y representación,

  (en adelante, el/los "Inquilino/s").

  El Propietario y el Inquilino serán denominadas conjuntamente como las "Partes".

  Ambas partes en la calidad con la que actúan, se reconocen reciprocamente capacidad jurídica para contratar y obligarse y en especial para el otorgamiento del presente CONTRATO DE ARRENDAMIENTO DE VIVIENDA, y


  EXPONEN

  1º .- Que el Propietario, es propietaria de la vivienda sita en Bilbao, calle San Mamés 23, 15ºJ. Vivienda en zona ajardinada con piscina comunitaria y garaje en el edificio.

  REF. CATASTRAL: AABBCC1234.

  Comunidad de propietarios: [x]

  Nº Cédula de habitabilidad [x] se adjunta fotocopia de la misma como anexo al final del presente contrato.

  Certificado de eficiencia energética [x]. Se adjunta fotocopia del certificado como anexo al final del presente contrato.

  El Propietario manifiesta expresamente que el Inmueble cumple con todos los requisitos y condiciones necesarias para ser destinado a satisfacer las necesidades permanentes de vivienda del Inquilino.

  (En adelante, la vivienda y sus dependencias descritas, conjuntamente, el "Inmueble").

  2º .- Que el Inquilino, manifiesta su interés en tomar en arrendamiento el citado Inmueble descrito en el Expositivo 1º, para su uso propio (y, en su caso, el de su familia) como vivienda habitual y permanente.

  3º .- Ambas partes libremente reconocen entender y aceptar el presente CONTRATO DE ARRENDAMIENTO DE VIVIENDA (el "Contrato"), conforme a las disposiciones de la Ley 29/1994 de 24 de noviembre de Arrendamientos Urbanos (la "LAU"), reconociendose mutuamente capacidad jurídica para suscribirlo, con sujeción a las siguientes:


  CLÁUSULAS


  PRIMERA: OBJETO

  1.1. El Propietario arrienda al Inquilino, que acepta en este acto, el Inmueble descrito en el Expositivo 1º, que el Inquilino acepta en este acto.

  1.2. El Inquilino se compromete a usar dicho Inmueble exclusivamente como vivienda del Inquilino y de su familia directa, en su caso.

  1.3 En relación con el uso del Inmueble, queda estrictamente prohibido:

  a) Cualquier otro tipo de uso distinto al descrito en el apartado anterior.

  b) El subarrendamiento, total o parcial.

  C) La cesión del contrato sin el consentimiento previo y por escrito del Arrendador.

  d) El uso del Inmueble para comercio, industria ni oficina o despacho profesional.

  e) Destinarla al hospedaje de carácter vacacional.

  El incumplimiento por el Inquilino de esta obligación esencial facultará al Propietario a resolver el presente Contrato.

  1.4 Por las dimensiones del Inmueble, el número máximo de personas que podrán ocuparlo es de 4, incluyendo al Inquilino.

  1.5 El Inquilino se obliga a cumplir y respetar en todo momento los estatutos y normas internas de la comunidad de propietarios a la que pertenece el Inmueble, que declara conocer y aceptar. Además, se compromete a no molestar ni perjudicar la pacífica convivencia del resto de vecinos de la comunidad.

  1.6 Se prohíbe expresamente al Inquilino tener en el Inmueble cualquier tipo de animal doméstico, salvo consentimiento expreso por escrito del Propietario. El incumplimiento de la presente obligación será considerado causa suficiente para la resolución del Contrato, de conformidad con lo establecido en el artículo 27.1 de la vigente LAU.

  SEGUNDO: PLAZO DE VIGENCIA

  2.1 El Contrato entrará en vigor en la fecha 1 de abril de 2023 con una duración inicial obligatoria de un (1) año a partir de la fecha de entrada en vigor del Contrato.

  2.2 El Contrato se prorrogará tácitamente (sin necesidad de aviso previo) en cada anualidad hasta un máximo legal de cinco (5) años, salvo que el Inquilino manifieste al Propietario, con treinta días de antelación a la fecha de terminación del Contrato o de cualquiera de sus prórrogas, su voluntad de no renovar el Contrato.

  2.3 Una vez transcurridos como minimo cinco (5) años de duración del Contrato, si ninguna de las Partes hubiese notificado a la otra, con al menos cuatro meses de antelación en el caso del Propietario, o con al menos con dos meses de antelación en el caso del Inquilino, a la fecha de finalización su voluntad de no renovar el Contrato,

  el Contrato se prorrogará obligatoriamente por anualidades hasta un máximo de tres (3) años, salvo que el Inquilino manifieste al arrendador con un mes de antelación a la fecha de terminación de cualquiera de las anualidades, su voluntad de no renovar el Contrato.

  2.4 El Inquilino podrá desistir del Contrato una vez que hayan transcurrido al menos seis (6) meses a contar desde la fecha de entrada en vigor del Contrato, siempre que notifique por escrito con treinta (30) días de antelación al Propietario. El desistimiento dará lugar a una indemnización equivalente a la parte proporcional de la renta arrendaticia de una mensualidad con relación a los meses que falten por cumplir de un año.


  TERCERA: ENTREGA DEL INMUEBLE

  3.1 El Propietario entrega al Inquilino el Inmueble en perfectas condiciones de habitabilidad, buen estado de conservación y funcionamiento de sus servicios y a la entera satisfacción de éste.

  3.2 Ambas Partes confirman que el Inmueble se entrega con cocina equipada y vivienda amueblada.

  En este acto el Propietario hace entrega al Inquilino de [número de llaves] juegos de llaves completos de acceso al Inmueble.


  CUARTA: RENTA

  Renta arrendaticia

  4.1 Ambas Partes acuerdan fijar una renta anual de 12.000 EUROS (€), que será pagada por el Inquilino en doce (12) mensualidades iguales de 1.000 EUROS (€) cada una de ellas.

  4.2 La falta de pago de una (1) mensualidad de renta será causa suficiente para que el Propietario pueda dar por resuelto este Contrato y ejercite la acción de desahucio.


  Inicio del devengo de la renta

  4.3 Se establece que la renta se devengará a partir de la fecha de entrada en vigor del presente Contrato. El Inquilino paga al Propietario el importe de la renta correspondiente a los días que quedan para finalizar el mes en curso, que el Propietario declara haber recibido a su entera satisfacción, sirviendo el presente Contrato como recibo de pago.


  Pago de la renta

  4.4 El Inquilino abonará la renta por mensualidades anticipadas, dentro de los cinco (5) primeros días laborables de cada mes, mediante transferencia bancaria a la siguiente cuenta titularidad del Propietario:

  Titular: Gregorio marañon Entidad: Banco Español. Nº de Cuenta/IBAN: 120211121002222.


  QUINTA: GARANTÍA DEL CONTRATO


  Fianza arrendaticia

  El Inquilino entrega en la entrega de llaves al Propietario, quien declara recibirla, la cantidad de 1000 EUROS (€ ), equivalente a 1 mensualidad de renta, por concepto de fianza legal, según lo establecido en el apartado primero del Artículo 36 de la LAU para garantizar el cumplimiento de las obligaciones que asume en virtud del presente Contrato.

  5.2 Para aquellas comunidades autónomas en las que sea necesario depositar la fianza: El Propietario se compromete a depositar la fianza en el organismo u oficina pública correspondiente a la Comunidad Autónoma en la que se encuentra el Inmueble.

  5.3 El importe de la fianza servirá para cubrir cualquier desperfecto o daño tanto en el Inmueble como en su mobiliario (según corresponda) así como garantizar el cumplimiento de las obligaciones que asume el Inquilino en virtud de este Contrato.

  5.4 Durante los primeros cinco (5) años de duración del Contrato, la fianza no estará sujeta a actualización, transcurrido dicho plazo, se actualizará en la cuantía que corresponda hasta que aquella sea igual a una mensualidad de la renta vigente en cada momento.

  SEXTA: FIRMA DEL CONTRATO

  Las partes aceptan el presente contrato, así como sus correspondientes anexos y sus efectos jurídicos y se comprometen a su cumplimiento de buena fe.

  ```

</details>

___

## Parte 2 - Diseño de prompt de analisis de la transcripcion

En esta parte, una vez hayamos extraido el texto del documento, vamos a utilizar Azure OpenAI para 3 tareas. Intenta crear un prompt para cada una de ellas, y experimenta con diferentes variantes. En la parte de "Ver Solucion" tienes algunos ejemplos. 

```
Prompt 1: Extraer información simple (por ejemplo, alquier mensual, política de mascotas, partes involucradas, dirección, etc. 
```

```
Prompt 2: Extraer información en JSON (pídele los mismos datos del Prompt 1, pero en formato muy concreto en JSON)
```

```
Prompt 3: Preguntar algo concreto para ver si sabe responder sobre el contrato.
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
