# Práctica para la creación y uso de una red virtual de Azure con una Máquina Virtual

![virtual-network](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/virtual-network.png)
 
## Breve descripción 
Azure Virtual Network es un servicio de tipo [IaaS](https://azure.microsoft.com/es-mx/overview/what-is-iaas/#overview) que se ejecuta en la [nube](https://azure.microsoft.com/es-mx/overview/what-is-the-cloud/) de Azure y ésta permite realizar conexiones (como su nombre lo dice) de forma virtual para diversos recursos a través del [portal de Azure](https://portal.azure.com/#home).Además, permite crear subredes dentro la red principal para mayor organización de las instancias. Para más información, se puede consultar los siguientes enlaces:
- [Azure](https://docs.microsoft.com/es-mx/connectors/azurevm/).
- [Microsoft Docs](https://docs.microsoft.com/es-mx/azure/virtual-network/).

-----------
## Requisitos
 - Tener una cuenta de Azure para realizar la práctica en su [Portal](https://portal.azure.com/#home) (si aún no se cuenta con alguna, se puede hacer el registro en el siguiente [enlace](https://azure.microsoft.com/es-mx/free/)). 
 - Contar con una suscripción activa de Azure para poder realizar la práctica (en el enlace anterior se muestra como se puede hacer).


---
## Instrucciones
Para realizar la práctica, se debe realizar los siguientes pasos:

1. Entrar al Portal de Azure y se busca, ya sea en la caja de búsqueda, o bien a tráves del enlace de [Grupo de Recursos](https://portal.azure.com/#view/HubsExtension/BrowseResourceGroups). 
![buscar-grupo-recursos](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/buscar-grupo-recursos.gif)
    - Seleccionamos el botón de crear y deberá aparecer una ventana con una serie de campos para rellenar:
    
        | Campo | Valor |
        |----| ----|
        | Nombre del grupo de recursos | Nombre del gripo de recursos nuevo. Ejemplo: PracticaAzureVirtualNetwork |
        |Región| Buscamos la opción más cercana y disponible. ***Importante**: Esta región no puede ser diferente a las demás instancias que serán creadas.* |

    ![grupo-recursos-info](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/grupo-recursos-info.png)
    - Una vez terminado el registro, se debe verificar que el grupo de recursos se ha creado correctamente. Esto se hace al presionar los botones de **Revisar y crear** y **Crear**.
    - Si todo ha ido bien, se visualizará la siguiente pantalla:
    ![grupo-recursos-creado](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/grupo-recursos-creado.gif)

#### Primera red virtual

2. Crear una Red Virtual en Azure. Para ello, se busca el servicio a través de la caja de búsqueda, o bien a tráves del enlace de [Redes Virtuales](https://portal.azure.com/#view/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2FvirtualNetworks).
![buscar-red-virtual](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/buscar-red-virtual.gif)
    - ***Datos básicos***:
        
        |Parámetros|Descripción|
        |----------|------------|
        |Grupo de Recursos|Seleccionar el Grupo de Recursos previamente creado|
        |Nombre|Nombre de la red virtual. Ejemplo: ***RedVirtual1***|
        |Region|Region de la red virtual. Debe ser igual al Grupo de Recursos creado|
        
        ![red-virtual1-datos](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/red-virtual1-datos.gif)

    - ***Direcciones IP***. Aquí ya se cuenta con una subred (y se puede dejar su nombre y dirección), pero podemos crear una con la misma dirección borrando la subred que existe por default.
        |Parámetros|Descripción|
        |----------|------------|
        |Agregar una Subred|Agregar una presionando el botón **Agregar subred**|
        - Se aparecerá un apartado del lado derecho de la pantalla con los siguientes parametros que **sólo se editarán**:
            |Parámetros|Descripción|
            |----------|------------|
            |Nombre de Subred|Nombre de la subred. Ejemplo: ***Subred1***|
            |Intervalo de direcciones de la subred| Para este caso, es `10.0.0.0/24` (nota importante: debe de ser los primeros números de dirección similar a la *Red Padre*)|
        - Se da clic en el botón **Agregar**.
        ![red-virtual1-direccion](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/red-virtual1-direccion.gif)
        - Se valida la Red Virtual creada con el botón **Revisar y crear**.
        -Esperamos a que se cree correctamente.
        ![red1-creada](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/red1-creada.gif)

#### Segunda red virtual

3. Crear otra Red Virtual en Azure. Es similar al paso anterior, pero con algunos cambios:
    - ***Datos básicos***:
        |Parámetros|Descripción|
        |----------|------------|
        |Grupo de Recursos|Seleccionar el Grupo de Recursos previamente creado|
        |Nombre|Nombre de la red virtual. Ejemplo: ***RedVirtual2***|
        |Region|Region de la red virtual. Debe ser igual al Grupo de Recursos creado|
    - ***Direcciones IP***. Aquí ya se cuenta con una subred (y se puede dejar su nombre y dirección), pero podemos crear una con la misma dirección borrando la subred que existe por default.
        |Parametros|Descripcion|
        |----------|------------|
        |Agregar una Subred|Agregar una presionando el botón **Agregar subred**|
        - Se aparecerá un apartado del lado derecho de la pantalla con los siguientes parametros que **sólo se editarán**:
            |Parámetros|Descripcion|
            |----------|------------|
            |Nombre de Subred|Nombre de la subred. Ejemplo: ***Subred2***|
            |Intervalo de direcciones de la subred| Para este caso es `10.1.0.0/24` (nota importante: debe de ser los primeros números de dirección similar a la *Red Padre*)|
        - Se da clic en el botón **Agregar**.
        ![red-virtual2-datos-direccion](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/red-virtual2-datos.direccion.gif)
        - Se valida la Red Virtual creada con el botón **Revisar y crear**.
        -Esperamos a que se cree correctamente.
        ![red2-creada](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/re2-creada.gif)

4. Como siguiente instrucción, se buscará el recurso (no su grupo de recursos) de la **Primera Red Virtual** creada (RedVirtual1). Se puede hayar desde el panel de inicio del Portal de Azure.
![buscar-red1](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/buscar-red1.gif)
    - En esta interfaz, en el panel derecho buscamos la opción de **Emparejamiento**.
    - Se agrega un nuevo emparejamiento con la **RedVirtual2** ya que se usará para conectar dos máquinas virtuales con las dos diferentes redes virtuales. Nos importarán únicamente los siguientes elementos de la configuración.
        |Campo|Valor|
        |-----|-----|
        |**Esta red virtual** ➡ Nombre del vínculo de emparejamiento | **RedVirtual1-a-RedVirtual2** (vínculo de *ida* de ésta red a la segunda red virtual)|
        |**Red virtual remota** ➡ Nombre del vínculo de emparejamiento | **RedVirtual2-a-RedVirtual1** (vínculo de *vuelta* de la segunda red a ésta red virtual)|
        |**Red Virtual** (es la red virtual destino)| **RedVirtual2**|
        
        ![emparejamiento-redes](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/emparejamiento-redes.gif)
    - Se da clic en el botón **Agregar** y se espera a que se actualice.
    ![emparejamiento-actualizado](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/emparejamiento-actualizado.gif)    

#### Primera máquina virtual

5. Crearemos una Máquina Virtual de Azure. Podemos crearla usando como referencia el siguiente [repositorio](https://github.com/JohnNadja/Practica-VM-dentro-de-VM). Sin embargo, se hará **sólo la primera parte** de éste y se harán cambios en los siguientes parámetros (lo demás se deja en su estado por defecto):
    - Datos básicos:
        |Parámetros|Descripción|
        |----------|------------|
        |Grupo de Recursos|Seleccionar el Grupo de Recursos previamente creado|
        |Región|Region de la máquina virtual. Debe ser igual al Grupo de Recursos creado|
        |Nombre de la máquina virtual|Nombre de la máquina virtual. Ejemplo: ***MaquinaVirtual1***|
        |Imagen (es el Sistema Operativo)|Seleccionar la imagen que se desea usar. En esta ocasión será: *Ubuntu Server* (Linux)|
        |Tipo de autenticación|Seleccionar el tipo de autenticación que se desea usar. En esta ocasión será: *Contraseña* |
        |Usuario|Nombre de usuario de la máquina virtual|
        |Contraseña|Ingresar la contraseña que se desea usar para la Máquina Virtual|
    - Redes:
        |Parámetros|Descripcion|
        |----------|------------|
        |Red Virtual|Seleccionar la **RedVirtual1**|            
        |Subred|Seleccionar la *Subred1* para esta primera Máquina Virtual|
    ![maquina-virtual1-datos](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/maquina-virtual1-datos.gif)
    - Esperamos a la Revisión y creación de la Máquina Virtual.

#### Segunda máquina virtual

6. Realizaremos los mismos pasos de la Prrimera Máquina Virtual para crear esta segunda. Aunque, tendrá de cambios lo siguiente:
    - Datos básicos:
        |Parámetros|Descripción|
        |----------|------------|
        |Grupo de Recursos|Seleccionar el Grupo de Recursos previamente creado|
        |Región|Region de la máquina virtual. Debe ser igual al Grupo de Recursos creado|
        |Nombre de la máquina virtual|Nombre de la máquina virtual. Ejemplo: ***MaquinaVirtual2***|
        |Imagen (es el Sistema Operativo)|Seleccionar la imagen que se desea usar. En esta ocasión será: *Ubuntu Server* (Linux)|
        |Tipo de autenticación|Seleccionar el tipo de autenticación que se desea usar. En esta ocasión será: *Contraseña* |
        |Usuario|Nombre de usuario de la máquina virtual|
        |Contraseña|Ingresar la contraseña que se desea usar para la Máquina Virtual|
    - Redes:
        |Parámetros|Descripcion|
        |----------|------------|
        |Red Virtual|Seleccionar la **RedVirtual2**|            
        |Subred|Seleccionar la *Subred2* para esta primera Máquina Virtual|
        
        ![maquina-virtual2-datos](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/maquina-virtual2-datos.gif)

7. Una vez creadas las dos Máquinas Virtuales, se procede conectarse a la Máquina Virtual 1 obteniendo la siguiente información:
    - Se conectará por medio de una conexión SSH.
    - Se copia los datos de conexión que se encuentra en el ounto 4 de la interfza de la Máquina Virtual.
    - Se abrirá una terminal y se ingresa la siguiente orden:
        1. **ssh** *usuario*@*ip*
        2. Escribimos **yes** para aceptar la conexión.
        3. Se ingresa la contraseña de la Máquina Virtual 1.
        4. Para verificar que la conexión se realizó correctamente, se revisa el nombre de usuario en la terminal.
    ![maquina-virtual1-conectar](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/maquina-virtual1-conectar.gif)
    - Si se quiere hacer una prueba, se puede hacer con el siguiente comando: `sudo apt-get moo`

8. Para conectarse a la Máquina Virtual 2, se debe ingresar al recurso de **RedVirtual2** y, en *Dispositivos conectados*, se encontrará la Máquina Virtual 2 con una dirección IP.
![ip-vm2](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/ip-vm2.gif)
    - Se copia esa dirección y se ingresa en la terminal con el siguiente comando: `ping *dirección ip*` (sin los asteriscos * ) .
    ![conexion-vm2](https://github.com/JohnNadja/Practica-Virtual-Networks/blob/main/images/conexion-vm2.gif)


### Listo, ya está creado un servicio de 2 Virtual Networks emparejadas y conectadas hacia Máquinas Virtuales en Azure.

----
# **⚠Importante⚠** 
### Recordar eliminar el grupo de recursos que se creó en Azure para evitar costos extras no deseados en caso de no ocupar el servicio.
Se puede hacer desde el panel de Azure en inicio y buscando el tipo de recurso que se llama **Grupo de Recursos**.


## Hasta aquí la finalización de la práctica.