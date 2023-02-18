# TALLER 2
## PATTERNS-FACTORY: LA HERRAMIENTA MAVEN

### CREAR UN PROYECTO CON MAVEN
Para crear un nuevo proyecto basado en un arquetipo, en la consola usamos el comando `mvn archetype:generate` con los datos datos en el enunciado del laboratorio como se muestra a continuación:

```
mvn archetype:generate -DgroupId=edu.eci.cvds -DartifactId=Patterns -Dpackage=edu.eci.cvds.patterns -DarchetypeArtifactId=maven-archetype-quickstart
```
Cambiamos al directorio Patterns y ejecutamos el comando tree /f para ver el conjunto de archivos y directorios creados por el comando mvn:

![image](https://user-images.githubusercontent.com/63562181/219901822-c8c2d1d8-3bd5-4669-8dcd-483fd5250f98.png)

### AJUSTAR ALGUNAS CONFIGURACIONES ENEL PROYECTO

Editamos el archivo pom.xml para agregar la sección **properties**:

![image](https://user-images.githubusercontent.com/63562181/219901920-e37db3c9-3591-431f-8353-42b639e5c132.png)

### COMPILAR Y EJECUTAR

Ejecutamos el comando `mvn package`:

![image](https://user-images.githubusercontent.com/63562181/219901987-a2341b6f-d7c8-457d-94dc-9a660d65d95c.png)

Para ejecutar desde la línea de comandos un proyecto Maven usamos el comando `mvn exec:java -Dexec.mainClass="edu.eci.cvds.patterns.App"`
Lo que da como resultado que se imprima "Hello World!"

![image](https://user-images.githubusercontent.com/63562181/219902326-0b663aba-7be3-43f7-af44-a58c6b723054.png)

Para enviar parametros al al plugin "exec" usamos la propiedad `-Dexec.args`. Realizamos los cambios en la clase App.java para crear un saludo personalizado, basado en los parámetros de entrada a la aplicación:

```
public class App 
{
    public static void main( String[] args )
    {
        if(args.length == 0){
            System.out.println( "Hello World!" );
        }else{
            System.out.println( "Hello " + args[0] + "!" );
        }
    }
}
```
Ejecumos la clase desde línea de comandos enviando Andrés como parámetro y verificamos la salida:

![image](https://user-images.githubusercontent.com/63562181/219902574-51d96fa6-8769-4bf8-af26-957af5f55958.png)

Al ejecutar la clase con mí nombre y apellido como parámetro solo muestra el nombre:

![image](https://user-images.githubusercontent.com/63562181/219902642-23f24af7-4632-4b04-851d-0265abd961dc.png)

Para enviar los parametros de forma compuesta usamos comillas simples '' para "encapsular" cada parametro:

![image](https://user-images.githubusercontent.com/63562181/219902686-e454e384-3924-458b-a6c2-a78bb5330417.png)

### HACER EL ESQUELETO DE LA APLICACION

Creamos los paquetes mencionados en el enunciado:

![image](https://user-images.githubusercontent.com/63562181/219902759-2fcc2531-90d1-478b-9ffc-d8e2f4a74665.png)

Creamos la interfaz llamada Shape.java en el directorio src/main/java/edu/eci/cvds/patterns/shape:

![image](https://user-images.githubusercontent.com/63562181/219903013-a61d70db-0c91-4143-8eb5-b344c9bb4212.png)

Creamos una  enumeración llamada RegularShapeType.java en el directorio src/main/java/edu/eci/cvds/patterns/shapes

![image](https://user-images.githubusercontent.com/63562181/219902854-932fcf14-db13-48c0-967f-abda3d0dda71.png)

En el directorio src/main/java/edu/eci/cvds/patterns/shapes/concrete cramos las clase Triangle, Quadrilateral, Pentagon,
Hexagon, que implementen la interfaz creada y retornan el número correspondiente de vértices que tiene la figura. 

Por ejemplo la clase Triangle:

![image](https://user-images.githubusercontent.com/63562181/219902983-9e028332-0dfb-48a1-9b20-892d38f3b738.png)

Creamos las otras clases:

![image](https://user-images.githubusercontent.com/63562181/219902992-05e92e3f-3dda-4dc8-a71e-cd29cc7e08c0.png)

Creamos el archivo ShapeMain.java en el directorio src/main/java/edu/eci/cvds/patterns/shapes y agregamos el codigo dado en el enunciado:

![image](https://user-images.githubusercontent.com/63562181/219903040-af2bd5b0-2d50-4320-8a1e-8a31e4d1ca7e.png)

Creamos la clase ShapeFactory.java en el directorio src/main/java/edu/eci/cvds/patterns/shapes implementando el patrón fábrica, haciendo uso de la
instrucción switch-case de Java y usando las enumeraciones.

![image](https://user-images.githubusercontent.com/63562181/219903227-23847f44-efe8-4e22-bf76-807e9f51dcef.png)


### Pruebas ShapeMain 

1. Sin parámetros: `mvn exec:java -Dexec.mainClass="edu.eci.cvds.patterns.shapes.ShapeMain"`

![image](https://user-images.githubusercontent.com/63562181/219903280-5bc8857c-40b3-460b-89da-053a21669fa1.png)

FUnciona correctamenta dado que en la clase ShapeMain se verifica que la variable `args` no sea nula.

2. Parámetro: qwerty `mvn exec:java -Dexec.mainClass="edu.eci.cvds.patterns.shapes.ShapeMain" -Dexec.args="qwerty"`

![image](https://user-images.githubusercontent.com/63562181/219903329-64ffd867-cc70-4d37-8ef3-0d5bf59fb185.png)

Funciona correctamente dado que en la clase ShapeMain se captura la execión lanzada y muestra el mensaje:

Parámetro: pentagon `mvn exec:java -Dexec.mainClass="edu.eci.cvds.patterns.shapes.ShapeMain" -Dexec.args="pentagon"`

![image](https://user-images.githubusercontent.com/63562181/219903395-1bef2abd-fd61-43f6-bcc4-0dd8b8f2f1de.png)

Comportamiento similar a la pruea anterior, pentagon no esta definida en RegularShapeType.java

Parámetro Hexagon `mvn exec:java -Dexec.mainClass="edu.eci.cvds.patterns.shapes.ShapeMain" -Dexec.args="Hexagon"`

![image](https://user-images.githubusercontent.com/63562181/219903450-b2a16a7b-9e20-408f-89c3-0d03647b2c05.png)

Comortamiento correcto, muestra el mensaje esperado.

