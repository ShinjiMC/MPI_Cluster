Fedora:
sudo dnf install openmpi openmpi-devel
sudo dnf install openssh-server
export PATH=$PATH:/usr/lib64/openmpi/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib64/openmpi/lib
Hacer
ip a

sudo nano /etc/hosts

Master <master ip address>
Slave <slave ip address>

ssh-keygen

servicio SSH esté en ejecución:
sudo systemctl status sshd

sudo systemctl enable sshd
sudo systemctl start sshd

sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
En ambos pc

ssh-copy-id master_username@ip_slave

Escribe un programa MPI (en este caso, hello world) y guárdalo con el mismo nombre y en el mismo directorio en ambas computadoras. (Guardaremos en Documents).

Abre la terminal.

Cambia al directorio donde guardaste el archivo de tu programa MPI (Documents en nuestro caso):

bash
Copiar código
cd ~/Documents
Compila el archivo del programa MPI:

bash
Copiar código
mpicc helloworld.c -o mpi_hello_world

mpiexec --oversubscribe -n 20 -host 192.168.3.45,192.168.3.108 ./mpi_hello_world
