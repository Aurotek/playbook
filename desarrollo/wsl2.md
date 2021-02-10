# Trabajando en Linux en Windows

En esta página hay algunas recomendaciones para trabajar de la mejor manera con WSL2, Linux y Docker desde Windows.

## Instalacion/Activacion de WSL2

Lo primero es instalar/activar WSL2, para eso utilizar [este elnace](https://docs.docker.com/docker-for-windows/wsl/) a la documentación de Docker.

## Descargando un OS de linux

Una vez que WSL2 ya se encuentra activado, es muy sencillo instalar un sistema operativo de Linux. Solo es necesario entrar a la Windows Store y buscar por ejemplo __Ubuntu__

## Usando Windows terminal

Utilizar la Windows términal te permite hacer algunas cosas del desarrollo con linux mas sencillas. Una de ellas es que te permite iniciar consolas directamente en el OS de tu elección. Si presionas __Ctrl__ + __,__ te abrirá las configuraciones. En esta sección puedes modificar el directorio de inicio de la consola como en el siguiente ejemplo.

```json
{
    "guid": "{07b52e3e-de2c-5db4-bd2d-ba144ed6c273}",
    "hidden": false,
    "name": "Ubuntu-20.04",
    "startingDirectory": "//wsl$/Ubuntu-20.04/home/<tu_usuario_de_linux>/<tu_path_deseado>",
    "source": "Windows.Terminal.Wsl"
}
```

Hay otras opciones que pueden configurarse desde aquí. Como estilo de la consola, el usuario que utiliza, etc.

## Credenciales de github/autenticacion

Para poder tener acceso a los repositorios de Auronix es necesario que desde el OS Linux el usuario se pueda autenticar con Github. Debido a conflictos en los permisos de archivos entre Windows y Linux no es posible solo agregar al agente ssh el path con las credenciales en Windows. Es necesario copiarlas y modificar sus permisos en Linux. Esto se puede hacer de manera sencilla con los siguientes comandos.

Copiar la carpeta de .ssh/ de Windows a Linux

`cp -R /mnt/c/Users/<tu_usuario_en_windows>/.ssh/ /home/<tu_usuario_en_linux>/.ssh/`

Y este es para modificar los permisos de los archivos de esta llave

`chmod 400 /home/<tu_usuario_de_linux>/.ssh/id_rsa.pub`

## Conviviendo con Homestead

Lamentablemente hay problemas al tratar de hacer convivir a Docker/WSL2 con Virtual Box, por lo que puede que al activar WSL2 y Docker dejen de poder accedar a sus entornos de Homestead. 

Cuando quieran desactivar WSL2 para poder volver a entrar a Homestead en Powwershell con privilegios de admin ejecuten el siguiente comando _(requiere reiniciar)_:

`bcdedit /set hypervisorlaunchtype off`

Para regresar a WSL2/Docker usen el siguiente comando _(requiere reiniciar)_:

`bcdedit /set hypervisorlaunchtype auto`

Esperamos que pronto todos los proyectos de Homestead estén migrados a Docker para que esto no sea necesario.