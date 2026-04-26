# Ansible - Paso a Paso

## Requisitos

- Python3 >= 3.8.0
- Multipass (https://multipass.run/install)
- pipx (https://pipx.pypa.io/stable/)

##

Lo primero sera clonar este proyecto

```bash
git clone https://github.com/tiagomedi/ansible_playbooks.git
```

## Instrucciones uso

### Instalación

```bash
pip3 install ansible
```

### Instalar pre-requisitos

```bash
make requirements
```

### Crear ambiente de prueba

```bash
make start
```

### Destruir ambiente de prueba

```bash
make stop
```

##

## Comandos Paso a Paso

```bash
ansible-galaxy collection install -r requirements.yaml # Instalar colecciones

ansible-playbook -i inventory.ini vms.yaml --tags "start" # Iniciar el servidor

ansible-playbook -i inventory.ini vms.yaml --tags "stop" # Detener el servidor

multipass list # Listar VMs

multipass info demo # Info del servidor

multipass shell demo # Acceder al servidor

multipass delete demo # Eliminar el servidor
```

Al Iniciar el servidor crea en la raiz del proyecto un archivo llamado `inventory.ini` que contiene la ip de la VM. A su vez, crea un directorio llamado `.ssh` que contiene las claves privadas y publicas de ssh para acceder al servidor.

Al eliminar el servidor con `make stop` o `multipass delete demo` se eliminara la VM pero no el directorio `.ssh` ni el archivo `inventory.ini`.

### `inventory.ini`
Es un archivo de texto plano que contiene la ip de la VM y las credenciales de acceso. En otras palabras, es una lista del inventario que estamos manejando. 

Tambien existe el inventario dinamico que es un archivo que se encarga de obtener la ip de la VM automaticamente, en caso de tener varias VMs se crea dinamicamente.

Finalmente, existen dos formas de manejar el inventario, una de ellas es `inventory.ini`, pero la otra es `inventory.yaml` siendo esta ultima la mas moderna y la mas recomendada para entornos mas complejos.
