# RETRIEVAL-AUGMENTED GENERATION (RAG) AND VECTOR DATABASES

## 1. Program for send prompts to Chatgpt

### Descripción

La estructura de este codigo se basa en obtener la respuesta a una pregunta que se le envia a chatGPT a través de un promp en python.

### Arquitectura

El codigo trabaja a traves de la libreria openAI(API client) que genera la consulta que se va a realizar y el acceso a chatGPT, despues haciendo uso de la libreria LLMchain que invoca la pregunta y la conexión que genera openAI() y posteriormente la ejecuta y obtiene el resultado.

### Test

![](/img/1.PNG)

## 2. RAG using an in-memory vector database

### Descripción

La estructura de este codigo se basa en obtener la respuesta a una pregunta que se le envia a chatGPT a través de un promp en python que se envia como un vector de memoria generado.

### Arquitectura

El codigo trabaja a traves de la libreria openAI(API client) que genera la consulta que se va a realizar y el acceso a chatGPT, despues genera un loader para la  respuesta que se va a obtener y se carga con la libreria WebBaseLoader, posteriormente  se cargan los parametros de la respuesta con la libreria RecursiveCharacterTextSplitter, luego se define el vector que recibira la información con la libreria Chroma y finalmente se genera el coontexto de la consulta generada con el formato que recibe la respuesta y la preguna que se envia.

### Test

![](/img/2.PNG)

## 3. RAG using Pinecone.

### Descripción

La estructura de este codigo se basa en obtener la respuesta a una pregunta que se le envia a chatGPT y consulta en un index generado en Pinecone para obtener la respuesta, el Pinecone es alimentado por nuestro codigo a la vez.

### Arquitectura

El codigo se divide en dos metodos

>##### loadText()
> Al igual que el codigo anterior generea un vector el cual almacena la información que adquiere de un documento llamado "awedfirstpaper.txt", se ajustan los settings de chunk_size, chunk_overlap, length_function y is_separator_regex, se separa el tecto obtenido por caracteres y se abre la conexión con el cliente con la libreria OpenAIEmbeddings() y se inicializa la conexión del pinecone, finalmente se envia la información para que se registre en pinecone.
>#### Nota: se debe descomentar la ltima linea del metodo.

>#### search()
> En este segundo metodo solamente se inicia el cliente con la libreria OpenAIEmbeddings(), se inicializa la conexión de pinecone y se envia a consultar una pregunta pre-definida, sí la pregunta esta relacionada a algún tema que se haya guardado en el pinecone retornara esta información, en caso contrario nos informara que no encontro información relacionada a la pregunta.

### Test

Pinecone vacio previo a ejecutar el metodo loadText()

![](/img/3.PNG)

Siempre debemos compilar el codigo primero, en este caso falla debido a que noesta encontrando nada en el pinecone

![](/img/4.PNG)

Ahora ejecutamos directamente el metodo loadText()

![](/img/5.PNG)

Ahora podemos ver que en Pincone se carga la información que teniamos en nuestro archivo de texto

![](/img/6.PNG)

Ahora al ejecutar el metodo search() obtenemos la respuesta a nuestra pregunta

![](/img/7.PNG)

## Autor
[Richard Santiago Urrea Garcia](https://github.com/RichardUG)
## Licencia & Derechos de Autor
**©** Richard Santiago Urrea Garcia, Ingeniero de Sistemas

Licencia bajo la [GNU General Public License](https://github.com/RichardUG/RETRIEVAL-AUGMENTED-GENERATION-RAG-AND-VECTOR-DATABASES/blob/master/LICENSE).