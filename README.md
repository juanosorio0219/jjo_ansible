# Despliegue de Contenedor Docker de Mario Bros en Azure con Ansible
Este repositorio contiene los archivos necesarios para desplegar un contenedor Docker con el juego de Mario Bros en una máquina virtual de Azure utilizando Ansible.

## Estructura del Proyecto
El proyecto está organizado en las siguientes carpetas:

- inventory: Contiene archivos de inventario de Ansible para definir los hosts en los que se realizarán las operaciones.

- playbooks: Contiene los playbooks de Ansible que describen las tareas necesarias para el despliegue del contenedor Docker en la máquina virtual de Azure.

- roles: Contiene los roles de Ansible, que son colecciones de tareas y archivos que pueden ser reutilizados en diferentes playbooks.

## Requisitos previos
Antes de comenzar con el despliegue, asegúrate de tener lo siguiente instalado y configurado:

- Clonar el proyecto:
   ```plaintext
  git clone https://github.com/juanosorio0219/jjo_ansible.git
  ```

- Ansible en tu máquina local. Puedes encontrar las instrucciones de instalación en la documentación oficial de Ansible.
  
- Una cuenta de Azure con permisos para crear recursos, como máquinas virtuales y grupos de recursos.

- Una máquina virtual deplegada en Azure, para ello puedes usar el siguiente proyecto: https://github.com/juanosorio0219/vm-modular-azure-terraform

## Pasos a seguir

- Abrir la terminal del proyecto y ejecutar el siguiente comando para instalar todo lo necesario en la máquina virtual usando uno de los playbooks (install_docker.yml)
  ```plaintext
  ansible-playbook -i inventory/hosts.ini playbooks/install_docker.yml
  ```

  <img width="1180" alt="Screenshot 2024-04-09 at 10 56 58 PM" src="https://github.com/juanosorio0219/jjo_ansible/assets/80568091/dd906217-4315-4716-afdb-ac0f904e3daa">

  
- Una vez tenemos lo necesario instalado, se ejecuta el siguiente comando para correr el contenedor de Docker en la máquina virtual usando el otro playbook (run_container.yml)
  ```plaintext
  ansible-playbook -i inventory/hosts.ini playbooks/run_container.yml
  ```
  <img width="1178" alt="Screenshot 2024-04-09 at 11 02 39 PM" src="https://github.com/juanosorio0219/jjo_ansible/assets/80568091/f35217cf-70e6-4bb8-89d7-f1d70f287b13">

- Verificar que el contenedor se encuentre en la máquina virtual, para ello es necesario conectarse via ssh usando la dirección ip, el usuario y la contraseña
  
  <img width="1045" alt="Screenshot 2024-04-09 at 11 05 51 PM" src="https://github.com/juanosorio0219/jjo_ansible/assets/80568091/61f3874d-3447-406b-ab99-c01e928153c5">
  
- Es necesario crear una regla de salida para el puerto del contenedor que se definió, esto se hace desde el portal de Azure
  
  <img width="580" alt="Screenshot 2024-04-09 at 11 09 19 PM" src="https://github.com/juanosorio0219/jjo_ansible/assets/80568091/6d771686-31c8-4538-8ba0-976d076214bd">

- Acceder usando la ip pública de la máquina virtual y el puerto definido

  <img width="1118" alt="Screenshot 2024-04-09 at 11 12 17 PM" src="https://github.com/juanosorio0219/jjo_ansible/assets/80568091/1df772f5-138f-4493-97d3-14fb162c2b29">

  


  
