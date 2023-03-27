# Ejercicios

En cada ejercicio se da un ejemplo y el resultado a obtener a partir de un prompt. El objetivo es diseñar el prompt de la forma correcta para obtener el resultado esperado.
___

## :question: 1 - Diseño de prompt simple

Frase de ejemplo:
```
Vamos a comer a mi restaurante favorito, y ya se lo que voy a pedir
```

Ahora define tres prompts para generar las siguientes respuestas:

```
We are going to eat at my favorite restaurant, and I know what I will order.
```

```
No vamos a comer a mi restaurante favorito, y no se que voy a pedir.
```

```
Ella va a comer a su restaurante favorito, y ya sabe lo que va a pedir.
```

Resumir un email:
```
Incluye un email 
```
Ahora crea un prompt que incluya en su respuesta la siguiente información basada en contenido del email:
```
Summary: XYZ
Open Questions: XYZ
Action Items: XYZ
```


<details>
  <summary>:white_check_mark: Ver solución:</summary>

* Traducción a inglés:
  ```
  Traduce la siguiente frase a inglés.
  
  Frase: Vamos a comer a mi restaurante favorito, y ya se lo que voy a pedir.
  
  Traducción a inglés:
  ```

* Niega la frase:
  ```
  Niega la siguiente frase.

  Frase: Vamos a comer a mi restaurante favorito, y ya se lo que voy a pedir.

  Frase Negada:
  ```

* Convierte a tercera persona
  ```
  Convierte la siguiente frase a tercera persona del singular, asumiendo que la persona es femenina.
  
  Frase: Vamos a comer a mi restaurante favorito, y ya se lo que voy a pedir.

  Frase convertida:
  ```

* Resumen de un email
  ```
  Quiero que resumas el siguiente email:
  [Resumen:]
  [Preguntas formuladas:]
  [Acciones propuestas:]
  
  Email: Incluye aquí un email.

  Email resumido:
  ```

</details>

___

## :question: 2 - Varias tareas en un mismo prompt

Utiliza la misma frase de ejemplo:
```
Vamos a comer a mi restaurante favorito, y ya se lo que voy a pedir.
```

Crea un prompt que genere la siguiente respuesta:
```
{
    "traducción": "We are going to eat at my favorite restaurant, and I know what I will order..",
    "frase negada": "No vamos a comer a mi restaurante favorito, y no se que voy a pedir.",
    "tercera persona": "Ella va a comer a su restaurante favorito, y ya sabe lo que va a pedir."
}
```
<details>
  <summary>:white_check_mark: Ver solución</summary>

```
A partir de la siguiente frase haz las siguientes tareas:
 
1. Traduce al inglés
2. Niega la frase
3. Convierte a tercera persona, asumiendo que la persona es femenina.
La respuesta debe ser un documento JSON. Una las claves "traducción", "frase negada" and "tercera persona" en el JSON. No hace falta incluir el texto original.

Sentence: Vamos a comer a mi restaurante favorito, y ya se lo que voy a pedir.
 
JSON:
```

</details>

___

## :question: 3 - Analizar un email de atención al cliente

Aquí tienes un email de ejemplo:

```
Hola, me llamo Mateo Gómez. Perdí mi tarjeta de crédito el 17 de Agosto, y me gustaría solicitar su cancelación. La última compra realizada fueron unos zapatos en Contoso Fashion, cerca del Museo Hollywood, por $40. Añado a continuación mi información personal para que puedan validar mi identidad:

Profesión: Contable
DNI: 12345678A
Fecha de nacimiento: 1-1-1989
Teléfono: 949-555-0110
Dirección: 1234 Hollywood Boulevard Los Angeles CA
Email: mateo@contosorestaurant.com
Código Swift: CHASUS33XXX
```

Diseña un prompt que genere la siguiente salida:
```
{
    "motivo": "Pérdida de tarjeta",
    "motivo_clasificado": "perdida_tarjeta",
    "nombre": "Mateo Gomez",
    "dni": "123-45-6789",
    "fdn": "09/09/1989"
}
```

<details>
  <summary>:white_check_mark: Ver solución</summary>

```
Este es un email de un cliente. Extrae la siguiente información:
  
- Razón de contacto:
- Razón de contacto clasificada (puede ser una de las siguientes "perdida_tarjeta","cierre_cuenta","cambio_direccion"):
- Nombre del cliente:
- DNI: 
- Fecha de nacimiento:
Extrae la información en un JSON con claves motivo, motivo_clasificado, nombre, dni, fdn. Para fdn utiliza formato DD/MM/AAAA

Email:
Hola, me llamo Mateo Gómez. Perdí mi tarjeta de crédito el 17 de Agosto, y me gustaría solicitar su cancelación. La última compra realizada fueron unos zapatos en Contoso Fashion, cerca del Museo Hollywood, por $40. Añado a continuación mi información personal para que puedan validar mi identidad:
Profesión: Contable
DNI: 12345678A
Fecha de nacimiento: 1-1-1989
Teléfono: 949-555-0110
Dirección: 1234 Hollywood Boulevard Los Angeles CA
Email: mateo@contosorestaurant.com
Código Swift: CHASUS33XXX

Resultado:
```

</details>

___

## :question: 4 - Escribe la descripción de un producto

Define un prompt que genere una descripción corta de dos frases de artículos de ropa basado en metadatos

Come up with a prompt that generates a short, two sentence description for clothing articles based on metadata.

Metadatos:
```
Temporada: Invierno
Estilo: Jersey
Género: Mujer
Público objetivo: Adolescentes
Material: Algodón
```

<details>
  <summary>:white_check_mark: Ver solución!</summary>

```
Escribe una descripción de dos lineas para este artículo de ropa. Hazla elocuente y llamativa.

Temporada: Invierno
Estilo: Jersey
Género: Mujer
Público objetivo: Adolescentes
Material: Algodón

Descripción:
```

</details>

___

## :question: 4 - Escribe un blog post

Escribe un blog post de un tema que te interese.

Utiliza el siguiente prompt reemplazando <Tema 1> con el tema sobre el que quieres escribir y añadiendo las ideas principales en <Idea 1> e <Idea 2>. 
```
Paso 1: Quiero que actúes como un social media manager. Tienes que ayudarme a pensar ideas para un post de mi blog sobre el tema <Tema 1>:
Paso 2: Escribe tres párrafos cautivadores e informativos sobre <Idea 1 relacionada con el Tema 1>
Paso 3: Escribe tres párrafos cautivadores e informativos sobre <Idea 2 relacionada con el Tema 1>
Paso 4: Tags <Lista de #hashtags relevantes>
```
___

## :question: 5 - Crear una query SQL con lenguaje natural

El siguiente prompt enviado a un modelo de codex devuelve una query de tipo select sobre las tablas que le pasamos al prompt.

```
### Postgres SQL tables, with their properties:
#
# Employee(id, name, department_id)
# Department(id, name, address)
# Salary_Payments(id, employee_id, amount, date)
#
### A query to list the names of the departments which employed more than 10 employees in the last 3 months

SELECT
```
Escribe un prompt que genere la query SQL que contenga la información de todos los clientes de Zaragoza de nombre Juan, teniendo el cuenta que la información se encuentra en la tabla Clientes, que contiene las columnas: CustomerId, Nombre, Apellido, Empresa, Direccion, Ciudad, Provincia, CP. 
___

<details>
  <summary>:white_check_mark: Ver solución!</summary>

```
Table Clientes, columns = [CustomerId, Nombre, Apellido, Empresa, Direccion, Ciudad, Provincia, CP]
Create a SQL query for all customers in Zaragoza named Juan 
query =

```

</details>
