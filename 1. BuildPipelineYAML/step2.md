En esta sesión, se modificará el pipeline como YAML, para la compilación y generación de artefactos de forma satisfactoria

Ubicados en la pestaña de review, en el cual se puede observar la definición del pipeline de integración continua, se realizará las siguientes modificaciones: 

1.Cambiar el agente por **windows-2019**

![agente](./assets/agente.png)

2.Establecer el valor de trigger en none 

![trigger-none](./assets/trigger-none.png)

3.Remover tarea de VSTest (Esto ya que el proyecto que se está usando para las pruebas es uno que ofrece Microsoft para realizar experimentos, sin embargo, actualmente están fallando unas pruebas unitarias)

![delete-test](./assets/delete-test.png)

4.Adicionar la versión **4.4.1** a la tarea de **NuGetToolInstaller**, el cual se realizaría de la siguiente manera: 

![nuget-version](./assets/nuget-version.png)

5.Adicionar la tarea **PublishSymbols**, para este paso, nos apoyaremos del asistente que ofrece la plataforma para configurar nuevas tareas.


5.1 Cursor en la última parte del archivo, para que a la hora de configurar la nueva tarea quede ubicada en ese lugar

![cursor](./assets/cursor.png)

5.2 Abrir asistente 

![abrir-asistente](./assets/abrir-asistente.png)

5.3 Buscar la tarea **Index sources and publish symbols**

![publish-symbol-task](./assets/publish-symbol-task.png)

5.4 Adicionar tarea 

![adicionar-tarea-publish](./assets/adicionar-tarea-publish.png)

6.Adicionar la tarea **PublishBuildArtifacts**, para este paso, nos apoyaremos del asistente que ofrece la plataforma para configurar nuevas tareas.

6.1 Cursor en la última parte del archivo, para que a la hora de configurar la nueva tarea quede ubicada en ese lugar (Como se muestra en el punto 5.1)

6.2 Abrir asistente de configuración de tarea (Como se muestra en el punto 5.2)

6.3 Buscar la tarea **Publish build artifacts**

![publish-build-task](./assets/publish-build-task.png)

6.4 Adicionar tarea 

![adicionar-tarea-build](./assets/adicionar-tarea-build.png)

**Nota:** Cuando se trata de pipelines como código, es importante mantener la identación del archivo, ya que YAML es bastante estricto en cuanto al orden de cada uno de los parámetros de configuración, por lo que se podrían estar generando errores, por ejemplo 

![errores](./assets/errores.png)


7.Finalmente, la definición debería quedar como en el archivo a continuación

[Pipeline YAML .NET](./assets/azure-pipelines.yml)


