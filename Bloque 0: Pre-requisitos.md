# Bloque 0: Pre-requisitos

Para poder realizar los bloques de ejercicio, será necesario que realices estos pasos correctamente. 

1. **Azure Form Recognizer**:
    * Navega al [portal de Azure](https://portal.azure.com/)
    * Pincha en "Crear recurso" y busca "Form Recognizer" 
    * Rellena los campos como un grupo de recurso, nombre de tu recurso FR y una región.
    * Al terminar, pincha "Create", y espera unos segundos 
    * Para acceder al servicio, utilizaremos el Studio: [Form Recognizer Studio](https://formrecognizer.appliedai.azure.com/)


2. **Azure Speech Service**:

    * Navega al [portal de Azure](https://portal.azure.com/)
    * Pincha en "Crear recurso" y busca "Speech"
    * Rellena los campos, seleccionando el RG previamente creado para FR, nombre de tu recurso Speech y una región.
    * Al terminar, pincha "Create", y espera unos segundos 
    * Para acceder al servicio, utilizaremos el Studio: [Speech Studio](https://speech.microsoft.com/portal)


3. **OpenAI**: 

    * Opcion 1: Azure OpenAI
         
      Si tu empresa ya tiene acceso a Azure OpenAI, tendrás que tener el rol "Cognitive Services OpenAI User" o "Cognitive Services OpenAI Contributor" para poder lanzar peticiones a los modelos
      
       Para utilizar el servicio, lo haremos mediante el playground del OpenAI Studio:  [Azure OpenAI Studio](https://oai.azure.com/)

    * Opcion 2: OpenAI (público)
      
      Si no cuentas con acceso a OpenAI en Azure, siempre podrás acceder via la API pública. 
      
      Date de alta aqui: https://platform.openai.com/login
      
      Para utilizar el servicio, lo haremos mediante el playground: [Playground (public)](https://platform.openai.com/docs/models/playground)
      
      **Cuidado:** ten cuidado con los datos que envias a la API publica, y asegura que no envias ninguna informacion confidencial de tu empresa. 
