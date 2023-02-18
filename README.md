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

Creamos lainterfaz llamada Shape.java en el directorio src/main/java/edu/eci/cvds/patterns/shape:

![image](https://user-images.githubusercontent.com/63562181/219902808-79eaa4e3-2836-4461-aff3-8b6acf2c42f0.png)





