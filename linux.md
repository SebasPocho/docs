# COMANDOS VARIOS
```
ps -fp $(pgrep -d, -u userid)
pkill 
stty erase ?
who -rb
df -k
```
```
find . -size +10000k -print0 | xargs -0 ls -l
find . -size +10000k -type f -ls -exec rm -rf {} \;
find . -type f -mtime +10 -exec rm -rf {} \;
find . -type f -mtime +1 -exec rm -rf {} \;
find . -type f sapocb13-cxf* -mtime +3 -exec rm -rf {} \;
find . -type f -exec grep -i -n "importer" /dev/null {} \; 
find . -type f -exec grep -i -n "The Framework has started." /dev/null {} \; 
find . -type f -mtime +30 -name "SFTP*" -exec rm -rf {} \;
find . -type f -size 2659992 -exec rm -rf {} \;
find . -type f -mtime +90 -exec mv '{}'  \;
find . -type f -exec grep -i “db2smpd” {} \; -print 2>/dev/null
find . -type f *.log
find / -type f *.log
find . -type f -mtime +30 -exec rm -rf {} \;
```
```
du -sh * | sort -n 
```
```
shutdown -g0 -y -i0 (init 0 - boot command line)
shutdown -g0 -y -i6 (restart)
shutdown -g0 -y -i5 (shutdown with no advice)
```
```
mount /dev/cdrom /media/cdrom
mount -r -t iso9660 -o loop -v <ISO_fname> <mount_point>
```
```
ls *.tar | xargs -i tar xf {}
```


# QUOTA
```
quota -v
quota <userid>
```

# TCP CHECK
```
timeout 1 bash -c 'cat < /dev/null > /dev/tcp/<servidor>/<puerto>'
echo $?

Respuesta: 0	--> OK
Respuesta: 124	--> Error

netstat -nap | awk '/tcp/ {print $6}'| sort | uniq -c
```

# TCPDUMP
```
tcpdump -i eth1 -s 0 -w /pfmtest.pcap host x.x.x.x (ip address of external server)

-s 0 -w C:\Users\l0314749\Desktop\test.pcap


**TCP DUMP HTTP PROTOCOL: **

tcpdump -i eth1 -s 0 -w /waslogs/pfmtesthttp.pcap tcp port http

tcpdump -i eth0 -s 0 -w /home/l0640174/Push_APNS.pcap tcp dst host 10.0.3.18

-i -> network interface, if they only use eth0 to communicate between MPP and application server.  Otherwise, remove the option.
-w -> write the raw packets to file
-s -> snaplen to 0 to set default 65535 bytes
host -> ip address of the application server if they only use one.  Otherwise, remove the option.
```

# SCP
```
scp [options] [[user@]host1:]filename1 ...  [[user@]host2:]filename2
scp file1.txt dvader@deathstar.com:somedir
```

# FILE SYSTEM CHECK
```
check for / partition: /dev/sda1

1. Reboot the server: shutdown -r now
2. Bring it on to single user mode while booting. At boot prompt "boot:", type in: a1 single
(or type "a6 single" if in your case the partition /dev/sda6 is used to boot).
3. Once it is on, unmount the file system by executing the below command: umount /dev/sda1
4. Run file system check on the system by executing the below command: fsck -yvf /dev/sda1
5. Once the above step is done reboot the system: reboot
To run fsck on the other partitions of the disk, do:
umount /dev/sda6 (/root2)
umount /dev/sda5 (/var)
fsck -yvf /dev/sda6
fsck -yvf /dev/sda5
```

# SSH KEYS
```
ssh-keygen -t rsa (crear key)
ssh-copy-id -i .ssh/id_rsa.pub user@host (para enviar la key, crea solo el authorized_keys)
```

# VIRTUAL MACHINES
```
* virt-manager (consola de administracion grafica)
* virsh (abre consola de maquinas virtuales. help da los comandos para correr)
* virsh list (--all|domain)
* virsh console domain
```

# YUM
```
system-config-packages (interfaz grafica del YUM)
rpm -ivh <paquete>

** Crear archivo de repositorio
	a) /etc/yum.repo.d/nombre.repo
		Sintaxis:
				[repo-name]
				name=descripcion
				baseurl=http://tuserver.com/
				enabled=1
				gpgcheck=1
* yum list all
* yum search <paquete>
* yum install <paquete>
* yum localinstall <paqueteRPM>
* yum groupinstall <grupodepaquetes>
* yum remove <paquete>
* yum update <paquete>
* yum update kernel --> para updetear el kernel.
```

# LOGS
```
* /var/log/dmesg
* /var/log/messages
* /var/log/maillog
* /var/log/secure
* /var/log/audit/audit.log

** Agregar logueo:
			vi /etc/syslog.conf
			mail.*@example.com
			
* /etc/sysconfig/syslog
```						

# CRON
```
* crontab -l (lista el crontab)
* crontab -e (para editar)
		Sintaxis:

.---------------- minuto (0 - 59) 
|  .------------- hora (0 - 23)
|  |  .---------- día del mes (1 - 31)
|  |  |  .------- mes (1 - 12) O jan,feb,mar,apr ... (los meses en inglés)
|  |  |  |  .---- día de la semana (0 - 7) (Domingo=0 o 7) O sun,mon,tue,wed,thu,fri,sat (los días en inglés) 
|  |  |  |  |
*  *  *  *  *  comando para ser ejecutado

* /etc/cron.allow
* /etc/cron.deny
```

# PRINTERS
```
* system-config-printer (interfaz grafica para configurar impresoras)
* http://localhost:631  (web interface)
* service cups restart --> restartea el servicio de printers
```

# TIME
```
* system-config-date
* /etc/ntp.conf
```

# FIREWALL - SELinux
```
* system-config-sercuritylevel o system-config-SElinux (interfaz grafica)
* /etc/sysconfig/selinux
```

# SYSTEM INITIALIZATION
```
* uname -r --> kernel
* yum list installed kernel o rpm -qa kernel --> kernels disponibles
* /etc/inittab
* init <nuevo runlevel> --> cambiar el runlevel
```

# SERVICES
```
*system-config-services (interfaz grafica)
* chkconfig --list <service name>
* chconfig <service name> on|off|reset
```

# KERNEL
```
* /etc/sysctl.conf --> IP forwarding.
* lsmod --> lista modulos cargados
* modinfo --> informacion
* modprobe <modulo> --> cargar modulo
* rmmod <modulo> --> borrar modulo
```

# NETWORK
```
* system-config-network (interfaz grafica)
* system-config-network-tui (interfaz por linea de comando)
* /etc/sysconfig/network-scripts/ifcfg-name
	Sintaxis:
			DEVICE=eth0
			ONBOOT=yes
			BOOTPROTO=static o dhcp
			HWADDR=x:x:x:x:x --> Para dhcp
			IPADDR=x.x.x.x
			NETMASK=x.x.x.x
			GATEWAY=x.x.x.x
			
* route -n --> ver las rutas
* /etc/sysconfig/network
* /etc/resolv.conf
	Sintaxis:
			search example.com
			namesever <ip>
			nameserver <ip>
```

# ACL (Access control List)
```
* vi /etc/fstab --> Agregar despues de default ",acl"
* mount -o remount <filesystem>
* getfacl <archivo> --> para ver si tiene ACL configurado
* setfacl -m u:<usuario>:rwx <archivo> ---> Para setear un ACL a un file
* setfacl -m d:g:<usuario>:rwx <directorio> --> para setear ACL a un directorio
* setfacl -x u:<usuario> <archivo> --> Eliminar ACL de un archivo
* setfacl -m u:<usuario>:--- --> quita acceso por sobre grupos etc.
```

# NIS
```
* authconfig --enable nis --<dominio> --<server> update --> Para habilitar nis en el cliente
* system-config-authentication --> Interfaz grafica para setear nis o ldap
* authconfig --> Interfaz grafica para setear nis o ldap
* Services:	
			* ypbind
			* yppasswdd
			* ypserv
(Para checkear que nis quedo levantado tienen que estar estos servicios)

* ypwhich			--> nis server que estas usando
* ypdomainname		--> display o sets el nis domain al que te vas a joinear
* ypcat <nisdomain> --> printea el contenido del mapa del server
* rpcinfo -p <hostname> --> Verifica si el server nis esta disponible.
```

# RAID
```
* fdisk /dev/xxx ---> Crear 1 particion extendida y 3 "FD" (opcion t para cambiar el system id de la particion).
* partprobe
* mdadm -C /dev/md0 -l 5 -n 3 /dev/xxx{5,6,7} 
* mke2fs -j -b 4096 -E stride=16 /dev/md0
* vi /etc/fstab ---> Agregar /dev/md0   <mountpoint>  ext3 defaults 1 2
* vi /etc/mdadm.conf --> agregar MAILADDR<tab>usuario@dominio.TLD    (manda mail al administrador del RAID

* mdadm /dev/md0 -r /dev/xxx --> Recoveri to new disk
* mdadm /dev/md0 -a /dev/xxx --> Agrega la particion que estas reemplazando
```

# LVM
```
* fdisk /dev/xxx --> PRIMARIA "8e" (opcion t para cambiar el system id de la particion).
* pvcreate /dev/xxx ---> le da volumen fisico crea
* vgcreate <nombre> /dev/xxx /dev/xxx /dev/xxx ... --> creas volume group
* lvcreate -L 300M -n <nombre> <nombre volume group> --> crea volumenes logicos
* mke2fs -j /dev/<nombre volume group>/<nombre(lvcreate)> --> dar formato
* mount /dev/<nombre volume group>/<nombre(lvcreate)> </mnt/nombre(lvcreate)> --> montas el volumen (punto de montaje mismo nombre que logical volume)
* system-config-lvm (interfaz grafica para ver los volumenes logicos)

* Resize:
			1) lvextend -L +XXM /dev/<nombre volume group>/<nombre(lvcreate) 
			2) resize2fs -p /dev/<nombre volume group>/<nombre(lvcreate)
			
Para agrandar logical volumes.

			1) e2fsck -f /dev/<nombre volume group>/<nombre(lvcreate) 
			2) resize2fs /dev/<nombre volume group>/<nombre(lvcreate) XXXM
			3) lvreduce -L XXXM /dev/<nombre volume group>/<nombre(lvcreate)
			4) reboot
			
Para achicar Logical volumes.
```

# AUTOMOUNT
```
* showmount -e instructor.example.com --> para ver si esta levantado NFS en el server.

* vi /etc/auto.master
					<mount point>	/etc/auto.caca
					
* vi /etc/auto.caca
					* -rw,soft instructor.example.com:/tmp/&
					
* service autofs stop
* service autofs start
```

# FILE SYSTEM:
```
* fdisk /dev/xxx
* mkfs.ext3 -L <label> /dev/xxxX
* crear mount point
* vi /etc/fstab
				LABEL=<label>	 </mountpoint> 	ext3 defaults 0 0
* partprobe				
* mount -a
```

# SWAP
```
* fdisk /dev/xxx (extendida)
* t - 82
* partprobe
* mkswap /var/local/swapfile
* vi /etc/fstab 
				/var/local/swapfile 	swap swap defaults 0 0
* swapon -a
```

# MEMORY
```
 cat /proc/meminfo
 egrep --color 'Mem|Cache|Swap' /proc/meminfo
```

# Vi: Search and Replace
```
 First occurrence on current line:      :s/OLD/NEW
 Globally (all) on current line:        :s/OLD/NEW/g 
 Between two lines #,#:                 :#,#s/OLD/NEW/g
 Every occurrence in file:              :%s/OLD/NEW/g 
```

# ADMIN CONSOLES
```
 GlassFish:
 https://<hostname>.inetpsa.com:4848
 
 Sun ONE:
 <host>.intepsa.com:18279
 
 WAS:
 https://<host>.inetpsa.com:11001/ibm/console/login.do?action=secure

```

# DB2 connect
``` 
 db2 CONNECT TO <DB> USER <USER> USING <passwd>
```

# ULIMIT
```
ulimit -a
modificar el archivo para que sea permanente --> /etc/security/limits.conf
```

# LIBERAR CHACHE MEMORIA
```
sync;sysctl -w vm.drop_caches=3
```


# JAVA
```
Thread Dump: jstack {pid} > stack-trace.tdump
Heap Dump: jmap -dump:live,format=b,file=<filename>.hprof <pid>

jps -l 
jmap -heap <PID>  ---> (ojo puede afectar la VM)
jmap -histo:live <PID> | head

ssl debug:
-Djavax.net.debug=ssl:handshake
```

## JAR
```
Ver contenido:

jar -tvf

cat contenido y ver file:
unzip -p com.sap.banking.bgba-config_8.3.1.2.jar META-INF/spring/bundle-context-security.xml | grep -A 20 channelStateConfigMap

Generar Jar:
jar cmf META-INF/MANIFEST.MF com.sap.banking.banking-core-common_8.3.1.2.jar com
```

# Delay Red:
```
tc qdisc add dev eth0 root netem delay 3000ms (esto lo pones)
tc -s qdisc (lista)
tc qdisc del dev eth0 root netem (quita)
```

# SSL:
```
openssl s_client -showcerts -connect ppfm.bancogalicia.com.ar:443
```



# Scripting Tips

### CHECKEO PARAMETROS:
```
if [ $# -eq 0 ]
  then
    echo "No arguments supplied"
fi
```

### SHEBANGS:
```
bash: #!/bin/bash
ksh: #!/bin/ksh
csh: #!/bin/csh
```

### DATE
```
date +%d%m%Y  -----> 18112015 (dias,meses,años)
date +%Y%m%d%H%M%S ----> 20151118152212  (años,meses,dias,horas,minutos,segundos)
```

### PARAMETROS DEFAULT:
```
$? --> Return Code
$$ --> PID
$# --> Cantidad de parametros indicados
$@ --> sees arguments as separate words
$* --> sees all arguments as single word
```

### IF SENTENCES:
```
if [ "$ENVIRONMENT" == "d" ]; then  --> Matching caracters
else
fi

if [ -d $SERENA_HOME/repository ]; then --> Directory 
else 
fi 

if [ "$REPO_CHECK" == "0" ] ; then --> Matching Numeric
else 
fi
```

### REDIRECTION:
```
1>filename       # Redirect stdout to file "filename."
1>>filename      # Redirect and append stdout to file "filename."
2>filename       # Redirect stderr to file "filename."
2>>filename      # Redirect and append stderr to file "filename."
&>filename       # Redirect both stdout and stderr to file "filename."
2>&1             # Redirects stderr to stdout.
&>/dev/null      # Redirects every output of a program to /dev/null
```

### Keystore JKS
```

keytool -genkey -alias keystore -keyalg RSA -keystore keystore.jks -keysize 2048
keytool -import -trustcacerts -alias CA -file sica01b64.cer -keystore keystore.jks
keytool -import -trustcacerts -alias SubCA -file isicab64.cer -keystore keystore.jks

keytool -list -v -keystore /opt/keystore/keystore.jks

JAVA_OPTIONS=-Djavax.net.ssl.keyStorePassword=${KEY_PASSWORD} -Djavax.net.ssl.keyStore=/opt/keystore.jks/keystore.jks -Djavax.net.ssl.trustStorePassword=${KEY_PASSWORD} -Djavax.net.ssl.trustStore=/opt/keystore.jks/keystore.jks

-Djavax.net.debug=ssl,handshake

```
