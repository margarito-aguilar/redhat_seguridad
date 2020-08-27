# redhat_seguridad

Rally_Redhat Estación 3 
Seguridad

La Organización requiere que se evaluen los estándares de Seguridad PCI-DSS v3.2.1 y Operating System Protection Profile v4.2 (OSPP) en ambientes con RHEL8.

Afortunadamente para ello se pueden aprovechar los perfiles de seguridad generados por OpenSCAP (familia de herramientas SCAP para realizar comprobaciones de cumplimiento de vulnerabilidades y configuraciones). Para más información www.open-scap.org.

Para cumplir el requerimiento se requiere configurar en Ansible Tower lo siguiente para el nodo3:

    Solamente se requiere un "check" de las plantillas de trabajo, no la aplicación de los estándares.
    Para el estándar Operating System Protection Profile (OSPP) se requiere modificar la longitud mínima de password a 12 (var_password_pam_minlen).

Tips

Existen varias formas de resolver esta tercer vuelta, aqui te dejamos algunos tips:

Usa los roles de ansible que están listos para dichos estándares.

    https://github.com/RedHatOfficial/ansible-role-rhel8-pci-dss
    https://github.com/RedHatOfficial/ansible-role-rhel8-ospp

Para usar dichos roles desde un job de Tower:

    Crea tu repo en github
    En tu repo, crea el directorio roles y dentro del mismo el archivo requirements.yml con el contenido

- src:  https://github.com/RedHatOfficial/ansible-role-a-usar

    Desde la ruta origen de tu repo, crea el archivo site.yml con el contenido

- name: Nombre
  hosts: all
  become: yes
  
  roles:
    - ansible-role-a-llamar

Referencia https://www.ansible.com/blog/using-ansible-and-ansible-tower-with-shared-roles

    Explora el rol ansible-role-rhel8-ospp donde encontrarás la variable a modificar.

Arrancamos!!
