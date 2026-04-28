# CURSO DE GIT 
## CLASE - 01 (GIT)
### ¿Qué es Git?
Es un Sistema de Control de Versiones, que nos permite llevar un control de los cambios realizados en nuestros proyectos, facilitando la colaboración entre varios desarrolladores.
Permitiendo a los desarrolladores trabajar de manera conjunta en un proyecto, sin preocuparse por los conflictos de código o la pérdida de información. Git registra cada cambio realizado en el proyecto, lo que permite revertir a versiones anteriores si es necesario y facilita la colaboración entre equipos de desarrollo.
<center>
<img src="images/logo-git.png" width="200">
</center>   

### ¿Cómo nació Git?
Git nació en abril de 2005, creado por Linus Torvalds (creador de Linux), tras la necesidad de un sistema de control de versiones rápido y distribuido para el kernel de Linux.
Surgió tras la polémica cancelación de la licencia gratuita de BitKeeper, el sistema que usaban anteriormente, lo que obligó a Torvalds a diseñar uno nuevo en poco más de una semana.
<center>
<img src="images/descarga.jpg" width="300">
</center>  

### Cómo instalar Git?
#### En Windows:
1. Descarga el instalador desde la página oficial: https://git-scm.com/downloads
2. Ejecuta el instalador y sigue las instrucciones. Puedes dejar las opciones por defecto, pero asegúrate de seleccionar "Git from the command line and also from 3rd-party software" para usar Git desde la terminal.
3. Una vez instalado, abre la terminal (Git Bash) y verifica la instalación con el comando:
   ```
   git --version
   ```      
#### En macOS:
1. Abre la terminal y ejecuta el siguiente comando para instalar Git usando Homebrew:
   ```
   brew install git
   ```      
2. Verifica la instalación con el comando:
   ```
    git --version
    ```
#### En Linux:
1. Abre la terminal y ejecuta el siguiente comando para instalar Git:   
    - En Debian/Ubuntu:
      ```
      sudo apt-get update
      sudo apt-get install git
      ```
    - En Fedora:
      ```
      sudo dnf install git
      ```
    - En Arch Linux:
      ```
      sudo pacman -S git
      ```
2. Verifica la instalación con el comando:
    ```
    git --version
    ```
### Configuración inicial de Git
Después de instalar Git, es importante configurar tu nombre de usuario y correo electrónico, ya que esta información se asociará con tus commits. Para configurar Git, abre la terminal y ejecuta los siguientes comandos:
```
git config --global user.name "Tu Nombre"
git config --global user.email "tu.email@ejemplo.com"
```
        
### Archivos en todo repositorio deberia tener
- README.md: Un archivo que proporciona información sobre el proyecto, cómo usarlo, cómo contribuir, etc.
- .gitignore: Un archivo que especifica qué archivos o directorios deben ser ignorados  por Git, como archivos temporales, dependencias, etc.
- LICENSE: Un archivo que especifica la licencia bajo la cual se distribuye el proyecto, indicando los términos de uso y distribución.

## CLASE - 02 
### STATES Y COMMITS
#### Los estados de Git
En Git, los archivos pueden estar en diferentes estados que reflejan su situación en el proceso de desarrollo. Estos estados son fundamentales para entender cómo Git maneja los cambios y cómo se preparan los archivos para ser incluidos en los commits.
#### Directorio de trabajo (Working Directory)
Es el lugar donde se encuentran los archivos del proyecto en tu sistema de archivos. Aquí es donde realizas cambios en los archivos, como editarlos, agregar nuevos archivos o eliminar archivos existentes. El directorio de trabajo refleja el estado actual de tu proyecto.
* **Untracked:** El archivo no está siendo rastreado por Git. No forma parte del historial de versiones y no se incluirá en los commits a menos que se agregue explícitamente.
* **Unmodified:** El archivo está siendo rastreado por Git y no ha sufrido cambios desde el último commit. No se necesita hacer nada con este archivo, ya que no hay cambios que registrar.
* **Modified:** El archivo ha sido modificado desde el último commit, pero aún no se ha agregado al área de preparación (staging area). Para incluir estos cambios en el próximo commit, es necesario agregar el archivo al área de preparación.
Si necesitas que un archivo vuelva a su estado original, puedes usar el comando `git restore -- <archivo>`, lo que descartará los cambios realizados en ese archivo y lo devolverá a la última versión confirmada en el repositorio local.
##### ¿Qué pasa si quiero que el archivo que creé no quiero que lo vea Git?
En ese caso, puedes agregar el nombre del archivo o el patrón de archivos al archivo `.gitignore`. Esto le indicará a Git que ignore esos archivos y no los rastree ni los incluya en los commits.

#### Área de preparación (Staging Area)
Es un espacio intermedio donde puedes preparar los cambios que deseas incluir en el próximo commit. Cuando agregas un archivo al área de preparación, estás indicando que quieres que esos cambios se registren en el historial de versiones. Puedes agregar archivos al área de preparación utilizando el comando `git add <archivo>`. Y con el comando `git reset <archivo>` puedes eliminar un archivo del área de preparación, lo que significa que esos cambios no se incluirán en el próximo commit.
Al aplicar el comando `git add .`, todos los archivos modificados en el directorio de trabajo se agregarán al área de preparación, lo que significa que estarán listos para ser incluidos en el próximo commit.
#### Repositorio local (Local Repository)
Es donde Git almacena el historial de versiones de tu proyecto. Cuando realizas un commit, los cambios que has preparado en el área de preparación se registran en el repositorio local. El repositorio local es una copia completa del historial de versiones, lo que permite trabajar de manera independiente sin necesidad de una conexión a internet.
Los comandos básicos para manejar estos estados son:
- `git commit -m "Mensaje del commit"`: Crea un nuevo commit con los cambios que has preparado en el área de preparación.
- `git status`: Muestra el estado actual de los archivos en el directorio de trabajo, el área de preparación y el repositorio local, indicando qué archivos están modificados, cuáles están preparados para el commit y cuáles no están siendo rastreados por Git.
- `git log`: Muestra el historial de commits en el repositorio local, permitiéndote ver los cambios realizados a lo largo del tiempo y quién los realizó.
- `git reset --hard HEAD`: Restaura el estado del repositorio local al último commit, descartando cualquier cambio no confirmado en el directorio de trabajo y el área de preparación. Ten cuidado al usar este comando, ya que perderás cualquier cambio no confirmado.
- `git reset --soft HEAD~1`: Deshace el último commit, pero mantiene los cambios en el área de preparación. Esto te permite modificar el mensaje del commit o agregar más cambios antes de volver a confirmar.

### Buenas prácticas para el uso de Git
1. **Usa verbos imperativos en los mensajes de commit:** Los mensajes de commit deben ser claros y concisos, describiendo la acción realizada. Por ejemplo, "Agrega función de autenticación" en lugar de "Función de autenticación agregada".
* <mark>Add</mark>: Indica que se ha agregado una nueva función o característica al proyecto.
* <mark>Fix</mark>: Indica que se ha corregido un error o bug en el código.
* <mark>Update</mark>: Indica que se ha actualizado o mejorado una función existente.
* <mark>Remove</mark>: Indica que se ha eliminado una función o código innecesario del proyecto.

2. **No uses punto final en los mensajes de commit:** Los mensajes de commit no deben terminar con un punto, ya que esto puede dificultar la lectura y el seguimiento del historial de versiones. 

3. **Usar como maximo 50 caracteres para el mensaje de commit:** Los mensajes de commit deben ser breves y al punto, idealmente no más de 50 caracteres. Esto facilita la lectura y comprensión del historial de versiones, especialmente cuando se visualiza en herramientas como `git log` o plataformas de alojamiento de código como GitHub.

4. **Usar un prefixo para el mensaje de commit:** Es recomendable usar un prefijo en el mensaje de commit para indicar el tipo de cambio realizado. Esto ayuda a categorizar los commits y facilita la comprensión del historial de versiones. Algunos prefijos comunes incluyen:
* <mark>feat</mark>: Indica que se ha agregado una nueva función o característica al proyecto.
* <mark>fix</mark>: Indica que se ha corregido un error o bug en el código.
* <mark>docs</mark>: Indica que se han realizado cambios en la documentación del proyecto.
* <mark>style</mark>: Indica que se han realizado cambios en el formato o estilo del código, sin afectar la funcionalidad.
* <mark>refactor</mark>: Indica que se ha refactorizado el código, mejorando su estructura sin cambiar su comportamiento.
* <mark>test</mark>: Indica que se han agregado o modificado pruebas para el proyecto.
* <mark>chore</mark>: Indica que se han realizado tareas de mantenimiento o cambios menores que no afectan la funcionalidad del proyecto.
* <mark>perf</mark>: Indica que se han realizado cambios para mejorar el rendimiento del proyecto.
* <mark>ci</mark>: Indica que se han realizado cambios relacionados con la integración continua o el proceso de construcción del proyecto.
* <mark>build</mark>: Indica que se han realizado cambios relacionados con el proceso de construcción o compilación del proyecto.
5. **Añade todo el contexto necesario en el mensaje de commit:** Además de ser breve, el mensaje de commit debe proporcionar suficiente contexto para que otros desarrolladores (o tú mismo en el futuro) puedan entender claramente qué cambios se realizaron y por qué. Esto puede incluir detalles sobre la razón detrás del cambio, cómo se implementó o cualquier información relevante que ayude a comprender el propósito del commit.

> Razón por la cual no asistí a la clase 21/03/2026.
>  ![](images/Foto_de_WhatsApp.png )
> - Estaba en el parcial de la materia de Taller de Sistemas Operativos, que se llevó a cabo el mismo día.
> Hora de inicio de Parcial 18:45 pero nos dió tiempo a resolver hasta las 20:30 y de ahí a casa me demoro aproximadamente una hora y media. por lo cual no pude asistir lamentablemente.

## CLASE - 03 
### GIT HUB Y SSH
#### ¿Qué es GitHub?
GitHub es una plataforma de alojamiento de código fuente y control de versiones basada en Git. Permite a los desarrolladores colaborar en proyectos de software, compartir código, gestionar versiones y realizar un seguimiento de los cambios realizados en el código fuente. GitHub ofrece una interfaz web intuitiva para gestionar repositorios, realizar pull requests, revisar código y colaborar con otros desarrolladores en proyectos de software.
#### Git vs GitHub
| Git | GitHub |
| --- | --- | 
| Es un sistema de control de versiones. | Es una plataforma de alojamiento de código basada en Git. |
| Permite gestionar el historial de versiones de un proyecto. | Permite colaborar en proyectos de software y compartir código. |
| Es una herramienta de línea de comandos. | Ofrece una interfaz web para gestionar repositorios y colaborar con otros desarrolladores. |

#### SSH vs HTTPS
| SSH | HTTPS |
| --- | --- |
| Es un protocolo de comunicación seguro que utiliza claves SSH para autenticar a los usuarios. | Es un protocolo de comunicación seguro que utiliza certificados SSL para cifrar la conexión. |
| Requiere configuración de claves SSH en el sistema. | No requiere configuración adicional, solo autenticación con usuario y contraseña. |
| Permite una autenticación más segura y sin necesidad de ingresar credenciales cada vez. | Requiere ingresar credenciales cada vez que se realiza una operación que requiere autenticación. |

Por lo que se recomienda usar SSH para una experiencia más fluida y segura al interactuar con repositorios en GitHub, especialmente si realizas operaciones frecuentes que requieren autenticación.
#### Configurar GitHub con SSH
1. **Generar una clave SSH:** Abre la terminal y ejecuta el siguiente comando para generar una nueva clave SSH:
   ```
   ssh-keygen -t ed25519 -C " "tu correo electrónico"
   ```
    Sigue las instrucciones para guardar la clave en el directorio predeterminado y establece una contraseña si lo deseas.
2. **Agregar la clave SSH a tu cuenta de GitHub:** Copia el contenido de tu clave pública SSH (generalmente ubicada en `~/.ssh/id_ed25519.pub`) y agrégala a tu cuenta de GitHub en la sección "SSH and GPG keys" de tu configuración de perfil.
3. **Configurar Git para usar SSH:** Asegúrate de que Git esté configurado para usar SSH en lugar de HTTPS. Puedes hacerlo ejecutando el siguiente comando:
   ```
   git config --global url."https://github.com/".insteadOf "https://github.com/"
   ```
    Esto redirigirá automáticamente las solicitudes de GitHub a usar SSH en lugar de HTTPS. 
4. **Probar la conexión SSH:** Para verificar que la configuración SSH esté funcionando correctamente, ejecuta el siguiente comando:
   ```  
    ssh -T git@github.com
    ```
    Si la conexión es exitosa, deberías ver un mensaje de bienvenida de GitHub indicando que has autenticado correctamente con tu clave SSH. Ahora puedes usar Git para interactuar con tus repositorios en GitHub sin necesidad de ingresar tus credenciales cada vez.
### Crear un repositorio en GitHub
1. Inicia sesión en tu cuenta de GitHub y haz clic en el botón "New repository" para crear un nuevo repositorio.
2. Completa los detalles del repositorio, como el nombre, la descripción y la visibilidad (público o privado). Puedes elegir si deseas inicializar el repositorio con un archivo README, un archivo .gitignore o una licencia.
3. Haz clic en el botón "Create repository" para crear el repositorio.
### Conectar un repositorio local de Git con uno existente en GitHub
   ```
   git remote add origin <URL del repositorio en GitHub>
   git branch -M main
   git push -u origin main 
   ```
Nota: Asegúrate de reemplazar `<URL del repositorio en GitHub>` con la URL real de tu repositorio en GitHub. Este comando establece una conexión entre tu repositorio local y el repositorio remoto en GitHub, permitiéndote enviar tus cambios al repositorio remoto utilizando `git push`. Para esto también es necesario haber inicializado un repositorio local de Git con `git init` y haber realizado al menos un commit antes de ejecutar estos comandos.
### Clonar un repositorio de Git
Para clonar un repositorio de Git desde GitHub, puedes usar el siguiente comando en tu terminal:  

   ```
   git clone <URL del repositorio en GitHub>
   ```
Si por accidente clonaste el repositorio usando HTTPS y deseas cambiarlo a SSH, puedes usar el siguiente comando para actualizar la URL del repositorio remoto:

   ```
   git remote set-url origin <URL del repositorio en SSH>
   ``` 
Este comando también es útil si deseas cambiar la URL del repositorio remoto por cualquier motivo, como cambiar de un repositorio privado a uno público o viceversa. Asegúrate de reemplazar `<URL del repositorio en SSH>` con la URL real del repositorio en formato SSH.

Para verificar que la URL del repositorio remoto se ha actualizado correctamente, puedes usar el siguiente comando:

   ```
   git remote -v
   ```
### Cambios 
* Subir mis cambios a GitHub: Para subir tus cambios locales a GitHub, puedes usar el siguiente comando:

   ```
   git push origin <nombre de la rama>
   ```
* Bajar cambios de GitHub a tu repositorio local: Para bajar los cambios realizados en el repositorio remoto de GitHub a tu repositorio local, puedes usar el siguiente comando:

   ```
   git pull origin <nombre de la rama>
   ```

## CLASE - 04 
### Remote, SSH multiple y checkout

#### GIT REMOTE
Permite gestionar conexiones con repositorios remotos, comunica a GIT local donde enviar o de donde traer la información.

#### SSH MULTIPLE
Permite configurar múltiples claves SSH para diferentes cuentas o servicios, lo que es útil si trabajas con varios repositorios en GitHub o en otros servicios de alojamiento de código. 
#### Configurar multiples claves SSH para diferentes cuentas o servicios
Para configurar SSH multiple, puedes seguir estos pasos:
1. Genera una nueva clave SSH para cada cuenta o servicio que deseas usar. Puedes hacerlo ejecutando el siguiente comando en tu terminal:
   ```
   ssh-keygen -t ed25519 -C "tu correo electrónico" -f ~/.ssh/id_miname
   ```
    Asegúrate de guardar cada clave con un nombre diferente para evitar sobrescribir las claves existentes. 
2. Agrega cada clave SSH a tu cuenta de GitHub o al servicio correspondiente. Copia el contenido de cada clave pública SSH (generalmente ubicada en `~/.ssh/id_ed25519.pub`) y agrégala a la sección "SSH and GPG keys" de tu configuración de perfil en GitHub o en el servicio que estés utilizando.
3. Configura tu archivo `~/.ssh/config` para especificar qué clave SSH usar para cada host. Puedes agregar entradas como la siguiente para cada cuenta o servicio:
   ```
   # Cuenta personal en GitHub

   Host github.com
     HostName github.com
     User git
     IdentityFile ~/.ssh/id_ed25519_github

   # Cuenta de trabajo en GitLab
   Host gitlab.com
     HostName gitlab.com
     User git
     IdentityFile ~/.ssh/id_ed25519_gitlab
   ```
    Asegúrate de reemplazar `id_ed25519_github` y `id_ed25519_gitlab` con los nombres reales de tus claves SSH. Con esta configuración, cuando te conectes a GitHub o GitLab, se utilizará la clave SSH correspondiente para autenticarte automáticamente sin necesidad de ingresar tus credenciales cada vez. 

* **Host** especifica el nombre del host al que deseas conectarte (por ejemplo, github.com).
* **HostName** especifica la dirección real del host (en este caso, github.com).  
* **User** especifica el nombre de usuario que se utilizará para la autenticación (en este caso, git).
* **IdentityFile** especifica la ruta a la clave SSH que se utilizará para autenticarte con ese host específico.
4. Prueba la conexión SSH para cada host para asegurarte de que la configuración sea correcta. Puedes hacerlo ejecutando el siguiente comando para cada host:
   ```
   ssh -T git@github-mi-cuenta
   ssh -T git@gitlab-mi-cuenta
   ```
    Reemplaza `github-mi-cuenta` y `gitlab-mi-cuenta` con los nombres de los hosts que hayas configurado en tu archivo `~/.ssh/config`. Si la conexión es exitosa, deberías ver un mensaje de bienvenida de GitHub o del servicio correspondiente indicando que has autenticado correctamente con tu clave SSH. Ahora puedes usar Git para interactuar con tus repositorios en cada servicio sin necesidad de ingresar tus credenciales cada vez.
#### Configuraciones locales para cada repositorio
Además de la configuración global de Git, también puedes configurar opciones específicas para cada repositorio local. Esto es útil si deseas tener diferentes configuraciones para diferentes proyectos o si estás trabajando en un proyecto con requisitos específicos. Para configurar opciones locales para un repositorio, puedes usar el comando `git config` con la opción `--local`. Por ejemplo, para configurar un nombre de usuario específico para un repositorio, puedes ejecutar el siguiente comando dentro del directorio del repositorio:
```
git config --local user.name "Nombre del Usuario"
```
* No te olvides hacer git clone con el host correcto, es decir, si configuraste SSH multiple, debes usar el host que corresponda a la cuenta o servicio que deseas usar para clonar el repositorio. Por ejemplo:

``` 
git clone git@github-mi-cuenta:usuario/repositorio.git
```
#### GIT CHECKOUT
El comando `git checkout` se utiliza para cambiar entre ramas o para restaurar archivos en tu repositorio local. Aquí hay algunos usos comunes del comando `git checkout`:
1. Cambiar a una rama existente:
   ```
   git checkout nombre-de-la-rama
   ```
    Esto cambiará tu directorio de trabajo a la rama especificada, permitiéndote trabajar en esa rama y realizar cambios sin afectar otras ramas.

2. Crear y cambiar a una nueva rama:
   ```   
   git checkout -b nombre-de-la-nueva-rama
   ```
    Esto creará una nueva rama con el nombre especificado y cambiará tu directorio de trabajo a esa nueva rama, permitiéndote comenzar a trabajar en ella de inmediato. 

3. Restaurar un archivo a su estado anterior:
   ```
   git checkout -- nombre-del-archivo
   ```
      Esto restaurará el archivo especificado a su estado anterior, descartando cualquier cambio no confirmado que hayas realizado en ese archivo. Ten cuidado al usar este comando, ya que perderás cualquier cambio no confirmado en el archivo.
4. Cambiar a una rama remota:
   ```
   git checkout origin/nombre-de-la-rama-remota
   ```
    Esto cambiará tu directorio de trabajo a la rama remota especificada, permitiéndote trabajar con los cambios realizados en esa rama remota. Ten en cuenta que esta opción no creará una nueva rama local, sino que simplemente te permitirá trabajar con la rama remota directamente. Si deseas crear una nueva rama local basada en la rama remota, puedes usar el siguiente comando:
   ```
   git checkout -b nombre-de-la-nueva-rama origin/nombre-de-la-rama-remota
   ``` 
5. Cambiar a una rama específica en un repositorio remoto:
   ```
   git checkout -b nombre-de-la-nueva-rama origin/nombre-de-la-rama-remota
   ```
6. Cambiar a una rama específica y actualizarla con los cambios del repositorio remoto:
   ```
   git checkout nombre-de-la-rama
   git pull origin nombre-de-la-rama
   ```
7. Cambiar a una rama específica y eliminar los cambios no confirmados:
   ```   
   git checkout nombre-de-la-rama
   git reset --hard HEAD
   ```
8. Cambiar a una rama específica y eliminar los cambios no confirmados en un archivo específico:
   ```
   git checkout nombre-de-la-rama
   git checkout -- nombre-del-archivo
   ```
9. Cambiar a una rama específica y eliminar los cambios no confirmados en todos los archivos:
   ```
   git checkout nombre-de-la-rama
   git reset --hard HEAD
   ```
10. Cambiar a una rama específica y eliminar los cambios no confirmados en un directorio específico:
    ```

      git checkout nombre-de-la-rama
      git checkout -- nombre-del-directorio/
    ```  
#### Buenas prácticas del checkout
1. **No trabajes mucho tiempo en 'Dectached HEAD':** Evita realizar cambios significativos mientras estás en un estado de 'Detached HEAD', ya que estos cambios pueden perderse fácilmente si no se gestionan adecuadamente. Si necesitas realizar cambios, considera crear una nueva rama para preservar tu trabajo.
2. **Limpia tu directorio de trabajo antes de hacer checkout:** Antes de cambiar a otra rama, asegúrate de que tu directorio de trabajo esté limpio y sin cambios no confirmados. Esto evitará conflictos y problemas al cambiar entre ramas.
3. **Usa checkout para cambiar de rama, no para crear ramas:** El comando `git checkout` se utiliza principalmente para cambiar entre ramas existentes. Para crear una nueva rama, es mejor usar el comando `git branch` o `git checkout -b` para evitar confusiones y mantener un flujo de trabajo claro.
4. **No hagas checkout a ramas remotas directamente:** Evita hacer checkout directamente a ramas remotas, ya que esto puede llevar a un estado de 'Detached HEAD'. En su lugar, crea una nueva rama local basada en la rama remota para trabajar de manera más segura y organizada.
5. **Usa checkout para restaurar archivos con precaución:** El comando `git checkout` puede ser útil para restaurar archivos a su estado anterior, pero ten cuidado al usarlo, ya que puede resultar en la pérdida de cambios no confirmados. Asegúrate de revisar los cambios antes de usar `git checkout` para restaurar archivos y considera hacer un commit o stash de tus cambios antes de restaurar archivos si no quieres perder tu trabajo. 

## CLASE - 05
### RAMAS Y GITFLOW BÁSICO
#### Ramas en Git
Las ramas en Git son una característica fundamental que permite a los desarrolladores trabajar en diferentes líneas de desarrollo de manera simultánea. Cada rama representa una versión independiente del proyecto, lo que permite a los desarrolladores realizar cambios sin afectar la rama principal (generalmente llamada "main" o "master"). Las ramas facilitan la colaboración, el desarrollo de nuevas características, la corrección de errores y la experimentación sin comprometer la estabilidad del proyecto principal.

#### Git Branch
Es el comando utilizado para crear, listar y gestionar ramas en Git. Algunas de las operaciones comunes con `git branch` incluyen:
- `git branch`: Lista todas las ramas en el repositorio local.
- `git branch nombre-de-la-rama`: Crea una nueva rama con el nombre especificado.
- `git branch -d nombre-de-la-rama`: Elimina la rama especificada (asegúrate de que la rama no tenga cambios no fusionados antes de eliminarla).
- `git branch -m nombre-viejo nombre-nuevo`: Renombra una rama existente.

#### Git checkout
Es el comando utilizado para cambiar entre ramas en Git. Algunas de las operaciones comunes con `git checkout` incluyen:
- `git checkout nombre-de-la-rama`: Cambia a la rama especificada.

No debemos tener nada previamente modificado en el directorio de trabajo, ya que esto puede causar conflictos al cambiar de rama. Si tienes cambios no confirmados, es recomendable hacer un commit o stash de esos cambios antes de usar `git checkout` para cambiar a otra rama.
- `git checkout -b nombre-de-la-nueva-rama`: Crea una nueva rama y cambia a ella al mismo tiempo.

#### Git checkout vs Git switch
| Git checkout | Git switch |
| --- | --- |
| Se utiliza para cambiar entre ramas y también para restaurar archivos. | Se utiliza exclusivamente para cambiar entre ramas. |
| Puede ser confuso para los nuevos usuarios debido a su funcionalidad dual. | Proporciona una sintaxis más clara y específica para cambiar de rama. |

#### Gitflow básico
Gitflow es una metodología de desarrollo de software que se basa en el uso de ramas para organizar el flujo de trabajo en un proyecto. Gitflow define un conjunto de ramas específicas y reglas para su uso, lo que ayuda a mantener un proceso de desarrollo estructurado y eficiente. Las ramas principales en Gitflow son:
1. **Main (o Master):** Es la rama principal que representa la versión estable del proyecto. Solo se deben fusionar cambios a esta rama después de que hayan sido probados y estén listos para producción.
2. **Develop:** Es la rama de desarrollo donde se integran todas las nuevas características y correcciones de errores. Esta rama se utiliza para el desarrollo activo y se fusiona regularmente con la rama Main para mantenerla actualizada.
3. **Feature branches:** Son ramas temporales que se crean para desarrollar nuevas características o funcionalidades específicas. Estas ramas se crean a partir de la rama Develop y se fusionan de nuevo a Develop una vez que la característica está completa y probada.
4. **Release branches:** Son ramas temporales que se crean para preparar una nueva versión del proyecto. Estas ramas se crean a partir de Develop y se utilizan para realizar pruebas finales, correcciones de errores y ajustes antes de fusionar a Main para su lanzamiento.
5. **Hotfix branches:** Son ramas temporales que se crean para corregir errores críticos en la rama Main. Estas ramas se crean a partir de Main y se utilizan para realizar correcciones rápidas sin afectar el desarrollo activo en la rama Develop. Una vez que se corrige el error, la rama Hotfix se fusiona tanto a Main como a Develop para mantener ambas ramas actualizadas.
#### Buenas prácticas para el uso de ramas y Gitflow
1. **Usa nombres descriptivos para las ramas:** Al crear ramas, es importante usar nombres descriptivos que reflejen claramente el propósito de la rama. Esto facilita la comprensión del flujo de trabajo y ayuda a otros desarrolladores a identificar rápidamente el propósito de cada rama. Por ejemplo, en lugar de usar nombres genéricos como "feature1" o "bugfix2", es mejor usar nombres como "feature/login-page" o "bugfix/fix-header-alignment" para indicar claramente qué característica o corrección de error se está desarrollando en esa rama.
2. **Mantén las ramas actualizadas:** Es importante mantener las ramas actualizadas con los cambios realizados en la rama Develop o Main para evitar conflictos y asegurarte de que estás trabajando con la versión más reciente del código. Esto se puede hacer regularmente fusionando los cambios de Develop o Main a tu rama de trabajo para mantenerla sincronizada con el resto del proyecto.
3. **Realiza commits frecuentes y significativos:** Al trabajar en una rama, es recomendable realizar commits frecuentes y significativos que describan claramente los cambios realizados. Esto facilita el seguimiento del historial de cambios y ayuda a otros desarrolladores a entender el propósito de cada commit. Evita hacer commits con mensajes genéricos como "cambios" o "arreglos", y en su lugar, proporciona mensajes descriptivos que expliquen qué cambios se realizaron y por qué.
4. **Usa pull requests para revisar y fusionar cambios:** En lugar de fusionar cambios directamente a la rama Develop o Main, es recomendable usar pull requests para revisar y discutir los cambios antes de fusionarlos. Esto permite a otros desarrolladores revisar el código, proporcionar comentarios y asegurarse de que los cambios cumplen con los estándares de calidad antes de ser integrados en la rama principal del proyecto.
5. **Elimina ramas después de fusionar:** Una vez que una rama ha sido fusionada a Develop o Main, es recomendable eliminarla para mantener el repositorio limpio y organizado. Esto ayuda a evitar confusiones y reduce el desorden en el historial de ramas, facilitando la navegación y el mantenimiento del proyecto a largo plazo.
