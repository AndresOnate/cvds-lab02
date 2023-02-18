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
