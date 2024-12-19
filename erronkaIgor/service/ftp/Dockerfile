#FTP ZERBITZUA MONTATZEKO MAKINA

# Usa una imagen base de Debian o Ubuntu
FROM ubuntu:latest

# Instala vsftpd
RUN apt-get update && apt-get install -y vsftpd

# Copia el archivo de configuración personalizado de vsftpd (si tienes uno)
COPY vsftpd.conf /etc/vsftpd.conf

# Crea una carpeta para los archivos FTP
RUN mkdir -p /home/ftperab1/ftp/files
# pasahitza duen fitxategia kopiatu
COPY pass.txt /home/ftperab1/ftp/files/pass.txt

# Da permisos y crea el usuario de FTP
RUN useradd -m ftperab1 && echo "ftperab1:password" | chpasswd && \
    chown ftperab1:ftperab1 /home/ftperab1/ftp -R

# Expone el puerto 21 para FTP
EXPOSE 21

# Ejecuta el servicio vsftpd en segundo plano
CMD ["/usr/sbin/vsftpd", "/etc/vsftpd.conf"]

